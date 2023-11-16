### Grundlagen
- Anders als bei OpenMP gibt es hier keinen Geteilten speicher, auf den jeder Prozess zugreifen kann, stattdessen hat der Prozess seinen eigenen Speicher
- Sollen Daten unteinander gewechselt werden, muss read und write ausgeführt werden → Message Passing

### Message Passing
Pseudo code:
```c
if(my_id == SENDER)
	send_to(RECEIVER, data)

if(my_id == RECEIVER)
	recv_from(SENDER, data)
```

### Vorteile
- Universell
	- Funktioniert sowohl auf Maschinen mit geteiltem Speicher, als auch mit verteiltem Speicher
- Ausdrucksfähig
	- Intuitieves und komplettes Model um parallelismus auszudrücken
- Einfaches Debugging
	- message-passing ist einfacher zu Debuggen, als shared-memory Programme
	- Debugger für mp zu schreiben könnte schwerer sein
- Leistung und Skalierbarkeit
	- Bessere Kontrolle über Daten Standort
	- Maschinen mit geteiltem Speicher bieten mehr Speicher und Cache
		- Kann super-lineare Speedups ermöglichen

### Nachteile
- Inkrementelle parallelisierung funktioniert nicht
	- Um ein sequentielles Programm mit MPI zu Parallelisieren ist oftmals ein komplettes redesign nötig
- Message-passing Primitive (idk) sind reltiv low-level
	- Die Aufmerksamkeit der Entwickler wird vom eigentlichen Anwendungs Problem auf eine effiziente paralle Implementierung gelenkt
- Kommunikations und Synchronisations Overhead
	- Kommunikations- und Synchronisationskosten können in großen Skalen zu einem Bottleneck werden (besonders bei Gruppenkommunikation)
- MPI Standard ist ziemlich Komplex
	- Die Basics sind simple, aber MPI zu nutzen benötigt wesentliches Wissen

### Was ist MPI?
- MPI = **M**essage **P**assing **I**nterface
- MPI spezifiziert eine Bibliothek, keine Sprache
	- Spezifiziert Namen, Aufrufsequenzen, Ergebnisse von Funktionen / Subroutinen benötigt um via message-passing zu Kommunizieren
	- Language Bindings für C/C++ und Fortran
	- MPI Programme sind mit der MPI Bibliothen verbunden und mit normalen Compilern kompiliert
- MPI ist eine Spezifikation und keine besondere Implementierung
	- Quasi ein Standard für message-passing
	- Definiert vom MPI Forum (Offene Gruppe mit Repräsentanten von Akademien und Industrie)
- MPI Programme sollten mit allen MPI Implementationen funktionieren, ohne veränderungen
- Es gibt sowohl Firmeneigene als auch Open Source Implementierungen von MPI

### Minimales message passing interface
```c
send(addres, length, destination, tag)
//bzw.
receive(address, length, source, tag, actlen)
```
- Address und Length geben den Message Buffer an:
![[Pasted image 20230204130621.png]]
- Adress = 2 (Rot); length = 7 (Orange)
- Tag wird zum abgleichen benutzt
- actlen: Der benötigte teil einer Message kann kleiner als der Buffer sein (= actualLength)

### Message buffer
- Oftmals sind die Messages nicht Zusammenhängend, liegen also nicht nebeneinander im Speicher
	- Beispiel: Reihe einer Matrix, welche aber Spaltenweise abgespeichert wird
	- Allgemein: Verstreute Sammlung von Strukturen verschiedener Größen
	- Programmierer wollen das zusammensammeln von Messages verhindern, da es aufwendig und fehleranfällig ist
- Datentypen können verschiedene Größen in heterogenen Systemen haben
	- Die länge in Bytes ist keine angemessene Spezifizierung für den Semantischen Kontent der Nachricht

### MPI Lösung:
```c
(address, count, datatype)
```
Beispiel:
```c
(a, 300, MPI_REAL) //Beschreibt array(vector) a mit 300 realen nummern
```
- (Datentypen können auch nicht Zusammenhängend sein)

#### Familien von Nachrichten unterscheiden
- Messages via Tag vergleichen
	- Wildcardtags matchen alle Tags
	- Das ganze Programm muss Tags auf eine vorher Definierten und Zusammenhängenden weise Verwenden
	- Problem: Bibliotheken sollten nicht versehntlich Nachrichten vom Main-Programm empfangen
- MPI Solution
	- Nachrichten Kontext
		- Wird vom System im Zusammenhang von User- und Bibliotheksanforderungen definiert
	- Der Kontext kann nicht mit einer Wildcard gematcht werden 

#### Prozesse benennen
- Prozesse gehören zu Gruppen
- Innerhalb dieser Gruppen haben sie einen Rank
	- Ranks von 0 bis n-1 (n = Anzahl aller Prozesse in der Gruppe)
- Es gibt eine Initiale Gruppe, zu welcher alle Prozesse gehören
	- Ranks von 0 bis n - 1 (n = Anzahl aller vorhandenen Prozesse)

#### Kommunikator
- Kombiniert die Hinweise des Kontext und der Gruppen ein einem Einzelnen Objekt, welches communicator genannt wird
- Wird der Wert der meisten kommunikations Operationen
- Destination und source von `send` bzw, `receive` zeigen auf den rank eines Prozesses innerhalb einer vom Kommunikator identifizierten Gruppe
- Zwei Vordefinierte Kommunikatoren:
```c
MPI_COMM_WORLD //Enthällt alle Prozesse
MPI_COMM_SELF //Enthält nur die lokalen Prozesse
```

#### Blocking send
```c
MPI_SEND(address, count, datatype, destination tag, comm)
```
- Sendet `count`-viele Vorkommen von Elementen des Typs `datatype` startend an `address`
- `destination`, spezifiziert als rank in einer Gruppe, assoziiert mit communicator `comm`
- `tag` ist eine Integer welche zum Message Matching verwendet wird
- `comm` identifieziert eine Gruppe von Prozessen und einen communication Kontext

#### Blocking receive
```c
MPI_Recv(address, maxcount, datatype, source, tag, comm, status)
```
- Erlaubt das Empfangen von `maxcount` Vorkommen von Elementen des Typs `datatype` im Buffer startend an `address`
- `source` ist der Rank in `comm` or wildcard `MPI_ANY_SOURCE`
- `tag` ist eine Integer welche für das Message Matching genutzt wird, oder wildcard `MPI_ANY_TAG`
- `comm` identifiziert eine Gruppe von Prozessen und ein communication Kontext
- `status` beinhaltet Informationen über die tatsächliche Nachrichtengröße, -quelle und -tag

#### Kollektive Kommunikation und Berechnung
- Wiederkehrende parallele Gruppen-Kommunikationsmuster (1 → n, n → 1, n → n)
	- Kommunikation (z.B. Broadcast)
	- Berechung (z.B. Summen Reduktion)
- Manuelle implementation via Punkt zu Punkt Nachrichten sind umständlich und meistens Ineffizient
- MPI bietet viele vordefinierte Kollektive Operationen an
	- Dabei werden optimierte Algorithmen genutzt
	- Könnte Vorteile von Hardware Spezifischen Features nutzen (z.B. Netzwerk)

#### Sechs-Funktionen-Version von MPI
| Function      | Berschreibung                            |
|---------------|------------------------------------------|
| MPI_Init      | Initialisiert MPI                        |
| MPI_Comm_Size | Gibt die Anzahl aller Prozesse zurück    |
| MPI_Comm_rank | Gibt Rank des aktuellen Prozesses zurück |
| MPI_Send      | Sendet eine Nachricht                    |
| MPI_Recv      | Empfängt eine Nachricht                  |
| MPI_Finalize  | Terminiert MPI                           |

#### Generic MPI function Format
```c
error = MPI_Function(parameter, ...)
```
- Error Code ist ein Integer return Wert
- Erfolgreicher return Code ist MPI_SUCCESS
- Fehlercode-Rückgaben sind abhängig von der Implementierung

#### Initialisierung und Finalisierung
```c
int MPI_Init(int *argc, char ***argv)
```
- Muss als erste MPI funktion aufgerufen werden
	- Einzie Ausnahme: `MPI_Initialize

```c
int MPI_Finalize()
```
- Muss als letzte MPI Funktion ausgeführt werden
	- Einzige ausnahme: `MPI_Finalized`

#### Rank in einem Kommunikator
```c
int MPI_Comm_rank(MPI_Comm comm, int *rank)
```
- Bestimmt den Rank des aufrufenden Prozesses innerhalb des Kommunikators `comm` und speichert diesen an `*rank`
- Mithilfe der Ranks kann man jeden einzelnen Prozess innerhalb des Kommunikators identifizieren

Beispiel:
```c
int myrank;
...
MPI_Init(&argc, &argv);
...
MPI_Comm_rank(MPI_COMM_WORLD, &myrank);
```

#### Größe eines Kommunikators
```c 
int MPI_Comm_size(MPI_Comm comm, int *size)
```
- Bestimmt die größe der Gruppe assoziiert mit dem Kommunikator `comm`

Beispiel:
```c
int size;
...
MPI_Init(&argc, &argv);
...
MPI_Comm_size(MPI_COMM_WORLD, &size);
```

#### Broadcast
```c
int MPI_Bcast(void *buf, int count, MPI_Datatype datatype, int root, MPI_Comm comm)
```
- Broadcastet eine Nachricht eines Prozesses mit dem Rank `root` zu allen anderen Prozessen der Gruppe
	- `buf` = Start-Adresse des Buffers
	- `count` = Anzahl aller Einträge in Buffer
	- `datatype` = Datentyp des Buffers
	- `root` = Rank des Broadcastenden Prozesses
	- `comm` = communicator

#### Reduce
```c
int MPI_Reduce(void *sendbuf, void *recvbuf, int count, MPI_Datatype datatype, MPI_Op op, int root, MPI_Comm comm)
```
- Kombiniert die Elemente des Inputbuffers jedes Prozesses mithilfe von `op` und returnt den wert dann in den Outputbuffer des Prozesses mit dem Rank `root`
	- `sendbuf` = Adresse des send buffers
	- `recvbuf` = addresse des receive buffers
	- `count` = Anzahl aller Elemente in Buffer
	- `datatype` = Datentyp der Elemente des send buffers
	- `op` = reduce operation
	- `root` = Rank des root Prozesses
	- `comm` = communicator

#### Main und Worker
- Self-scheduling Algorithmus
	- Main-Prozess koordiniert die Berechung von Tasks indem er Input-Daten an die Worker weitergibt und die Ergebnise einsammelt
- Geeignet wenn
	- Worker untereinander Kommunizieren müsse
	- Arbeit, die jeder Worker-Thread erledigen muss nicht einschätzbar ist
- Beispiel: Matrix_Vector multiplikation

#### Return Status
- In C ist status eine Struktur mit drei Feldern:
	- MPI_SOURCE = Rank des Quellprozesses
	- MPI_TAG = Tag der message
	- MPI_ERROR = Error Code
- Die drei Felder beinhalten Informationen über die Nachricht, welche tatsächlich empfangen wurde
- Die Anzahl der Einträge welche empfangen wurden, kann mit folgender Funktion bestimmt werden:
```c
int MPI_Get_count(MPI_Status *status, MPI_Datatype datatype, int *count)
```

#### Mögliches blocking-Verhalten von MPI_Send()
- Send() kann gestartet werden, egal ob es ein Matchendes reveice gibt
- Zwei mögliche wege zum Abschließen von Send()
	- Buffered
		- Könnte Abschließen, bevor ein passendes receive gepostet wird
	- Synchronous
		- Schließt nur ab, wenn ein passendes receive gepostet wird, und die receive-operation gestartet wird
	Welche genutzt werden sollte hängt von der größe der Nachricht ab

#### Deadlock
- Was passiert, wenn zwei sends nicht terminieren, bis die empfänger ihr receive gepostet haben?
	- Zwei Prozesse sind deadlocked, wenn jeder Prozess auf ein Event wartet, das nur der jeweils andere Prozess initiieren kann.
	- Wenn mehr als zwei Prozesse in ein deadlock verwickelt sind, dann warten sie in einer runden Kette

#### Send und Receive kombiniert
```c
MPI_Sendrecv
```
- Diese Funktion erlaubt einem Prozess sowohl zu senden als auch zu empfangen.

```c
int MPI_Sendrecv(void *sendbuf, int sendcount, MPI_Datatype sendtype, int dest, int sendtag, void *recvbuf, int recvcount, MPI_Datatype recvtype, int source, int rectag, MPI_Comm comm, MPI_Status *status)
```
- Führt blocking send und receive operationen aus
- Sowohl send als auch receive nutzen den gleichen Kommunikator, aber möglicherweise unterschiedliche Tags
- Semantik als hätte der aufrufende Prozess zwei Threads gleichzeitig, einen um zu senden und einen um zu empfangen, gefolgt von einem join beider Threads

#### Allreduce
```c
int MPI_Allreduce(void *sendbuf, void *recvbuf, int count, MPI_Datatype datatype, MPI_Op op, MPI_Comm comm)
```
- Kombiniert die Werte aller Prozesse der Gruppe von comm und verteilt das Ergebnis an jeden Prozess zurück
	- `sendbuf` = startadresse des send buffer
	- `recvbuf` = startadress des receive buffer
	- `count` = Anzahl der Elemente im send buffer
	- `datatype` = Datentyp der Elemente des senbuffers
	- `op` = reduce operation
	- `comm` = communicator

#### Kommunikatoren
```c
MPI_Init;  // MPI initiieren
MPI_Group world_group, worker_group;  //Gruppen werden erstellt
//[...]  
MPI_Comm_size(world, &numprocs);  //Wir holen uns die anzahl aller Prozesse
MPI_Comm_rank(world, &myid);  //Wir holen uns den Rank des aktuellen Prozesses innerhalb der Gruppe mit allen Prozessen
server = numprocs-1;  //Wir bestimmen den Server Prozess (Der letzte Prozess in der Gruppe aller Prozesse)
MPI_Comm_group(world, &world_group);  //Wir initialisieren die world_group
ranks[0] = server;  //Wir erstellen eine Gruppe nur mit dem Server Prozess bzw. mit den Prozessen, die wir entfernen wollen
MPI_Group_excl(world_group, 1, ranks, &worker_group); //Wir erstellen eine Gruppe mit allen Prozessen ohne 
MPI_Comm_create(world, worker_group, &workers);  
MPI_Group_free(&worker_group);  
//[...]  
MPI_Comm_free(&workers)
```

#### Kollektiv Operations
- Alle operationen die kollektiv von mehreren MPI Prozessen ausgeführt werden
	- Z.B.: Broadcast
- Typisch für die meisten Kollektivoperatoren: Der Root Prozess spielt eine große Rolle

##### Wie sieht die Verteilung von Daten aus?
- Variante a
	- Der Root Prozess verteilt seine Daten einzeln an jeden Prozess
	- Nicht so schlau tho
- Variante b
	- Der Root Prozess verteilt seine Daten auf andere Prozesse und diese Prozesse verteilen diese Daten auch weiter 
	- Schon schlauer, gibt sogar eine Funktion in MPI die das übernimmt:
		- MPI_Bcast (siehe Broadcast)

#### Kollektive Kommunikationsregeln
- Viele kollektive Operationen wie Broadcast oder gather haben einen einzigen Quellprozess bzw. Ziel Prozess
	- Manche Argumente sind nur in der Root wichtig und werden von allen anderen Prozessen ignoriert
- Typ Matching ist strenger als im Punkt zu Punkt Fall
	- Die Menge der Daten, welche gesendet werden muss genau der Menge entsprechen, die der Receiver Spezifiziert
- Blocking
	- Kollektive Operationen können dann returnen, wenn ihre Mitarbeit in der Kollektiven Kommunikation nicht mehr benötigt wird
	- Ein Kollektiver Aufruf könnte einen Synchronisierenden Effekt haben
- Alle Prozesse des kommunikators müssen die Kollektive Routine aufrufen
- Die Operationen gibt es auch als Non-Blocking
	- Spezifiziert, wenn MPI_IN_PLACE statt send oder receive buffer verwendet wird

#### Barrier Sync
```c 
int MPI_Barrier(MPI_Comm *comm)
```
- Blockt den Aufrufenden Prozess bis alle Gruppenmitglieder die Funktion aufgerufen haben
- Der Aufruf returnt bei jedem Prozess nur dann, wenn alle Gruppenmitglieder ddue Funktion aufgerufen haben.
- Anwendung
	- Korrektheit (I/O, ready send)
	- Performance (Nummer der Nachrichten im transit limitieren)

#### Gather
```c
int MPI_Gather(void *sendbuf, int sendcount, MPI_Datatype sendtype, void *recvbuf, int recvcounts, MPI_Datatype recvtype, int root, MPI_Comm comm)
```
- Jeder Prozess sendet den Inhalt seines Send buffers an den Root Prozess
- Der Root Prozess erhält die Nachrichten und speichert sie in der Rank-Reihenfolge

#### Gatherv
```c
int MPI_Gather(void *sendbuf, int sendcount, MPI_Datatype sendtype, void *recvbuf, int recvcounts, int *displs, MPI_Datatype recvtype, int root, MPI_Comm comm)
```
- Erweitert die funktionalität von gather indem es folgendes ermöglicht:
	- Eine variierende Anzahl an Daten von jedem Prozess
	- Mehr flexibilität indem man via displacements bestimmen kann, wo die Daten im root gespeichert werden
- Die Daten vom Prozess j werden im `recvbuf` des Rootprozesses beginnend an `displs[]` Elements 

#### Scatter und Scatterv
```c
int MPI_Scatter(void *sendbuf, int sendcount, MPI_Datatype sendtype, void *recvbuf, int recvcount, MPI_Datatype recvtype, int root, MPI_Comm comm)

int MPI_Scatterv(void *sendbuf, int *sendcounts, int *displs, MPI_Datatype sendtype, void *recvbuf, int recvcount, MPI_Datatype recvtype, int root, MPI_Comm comm
```

#### All-to-all austausch
- MPI_Allgather / MPI_Allgetherv
	- Ähnlich wie Gather, nur das alle Prozesse das Ergebnis bekommen und nicht nur die Root
- MPI_Alltoall / MPI_Alltoallv
	- Eine Erweiterung von allgather, für den Fall, in welchem jeder Prozess eigene Daten an jeden Receiver sender
	- Alltoallv erlaubt displacements die man für die Sender spezifizieren kann
- MPI_Alltoallw
	- Allgemeiste form vom Complete Exchange
	- Erlaubt seperate Spezifizierung von count, displacements und datentypen, wobei displacements in byte spezifiziert werden
- MPI_Allreduce
	- Wie das normale reduce, nur, dass das Ergebnis in dem receive buffer jedes Gruppenmitglieds gespeichert wird
- MPI_Reduce_scatter_block und MPI_Reduce_scatter
	- Das ergebnis der reduce operation wird an jedes Gruppenmitglied gestreut
	- Beispiel: Prozess n soll das Ergebniss von Reduce des der spalte n haben

#### Scan
```c
int MPI_Scan(void *sendbuf, void *recvbuf, int count, MPI_Datatype datatype, MPI_Op op, MPI_Comm comm) //Ergebnis von 0 op (e.g +) 1 op (e.g +) ... op (e.g +) n

int MPI_Exscan(void *sendbuf, void *recvbuf, int count, MPI_Datatype datatype, MPI_Op op, MPI_Comm comm) //Ergebnis von 0 op (e.g +) 1 op (e.g +) ... op (e.g +) n - 1
```
- Inklusiv
	- Jeder Prozess hat das Ergebnis von Reduce des Vorherigen Prozesses + den Wert den er selbst gespeichert hat
	- Parallelisieren wird schwer - Man kann jedoch mit geschicktem Tauschen der Reihenfolge der Prozesse eine Teilweise Parallelisierung erreichen
- Exklusiv
	- Jeder Prozess hat das Ergebnis von Reduce bis zum vorherigen Prozess

### Hybrides Programmieren
- Die meisten Cluster sind mit shared-memory nodes zusammengesetzt
- Einen MPI Prozess pro Kern zu nutzen leidet unter Skalierbarkeits- und Effizientslimits
	- Es wird mehr speicher benötigt um seperate private adressräume zu unterhalten
	- Es ist aufwendig daten zwischen den Adessräumen zu kopieren
	- Zu viele externe MPI Links pro Node
- Lösung:
	- MPI und OpenMP kombinieren um die Anzahl von MPI Prozessen zu reduzieren
		- Oftmals ein Prozess pro Socket anstatt einer pro Core

#### MPI und Threads
- In einer Thread Kompatiblen implementierung kann ein MPI Prozess multi-threaded werden
	- Jeder Thread kann MPI Aufrufe starten
- Aber, threads sind nicht seperat ansprechbar
	- Ein Rank in einem Send oder Receive Aufruf identifiziert einen Prozess und keinen Thread
	- Eine Nachricht welche an einen Prozess gesendet wird kann von jedem Thread dieses Prozesses erhalten werden

##### Initialisierung
```c
int MPI_Init_thread(int *argc, char ***argv, int required, int *provided)
```
- Initialisiert MPI genauso wie MPI_Init und initialisiert gleichzeitig eine Thread-Umgebung
	- required = gewünschtes level von thread support
	- providet = level von thread support, welche von der Implementierung gewährleistet wird
- 

##### Thread Support Level
- MPI_THREAD_SINGLE
	- Quasi keine Threads, aka nur ein Thread (Also quasi nur der Prozess)
- MPI_THREAD_FUNNELED
	- Prozesse können multi-threaded sein, aber die Anwendung muss versichern, dass nur der Main Thread MPI Aufrufe startet
- MPI_THREAD_SERIALIZED
	- Prozesse können multi-threaded sein und mehrere Threads können MPI calls starten, aber nur einer Gleichzeitig (Alle MPI Aufrufe sind Serialisiert)
- MPI_THREAD_MULTIPLE
	- Mehrere Threads können ohne beschränkung MPI Aufrufe starten

- Wenn ein Aufruf möglich ist, returnt der Aufruf provided = required
- Failed der Aufruf, returnt er das kleinste supportete Level, sodass provided > required
- Wenn die User Anforderungen nicht erfüllt werden können, dann returnt der Call das höchste unterstützte Level
- Tipp: Check ob `required <= provided`

##### Thread-compliant MPI implementation
- Wird dazu in der Lage sein provided = MPI_THREAD_MULTIPLE zu returnen
- Alle MPI Aufrufe sind thread-safe. Beispielsweise könnten zwei Threads parallel MPI Aufrufe starten und das Ergebnis wäre, als wenn die Aufrufe in einer bestimmten Reihenfolge stattgefunden hätten
- MPI Aufrufe blocken den Aufrufenden Thread, was einem anderen Thread erlaubt auszuführen, nur wenn es möglich ist

##### Konflikte Communication Calls
- Der User muss rece conditions selbst verhindern
- Wenn man für unterschiedliche Threads unterschiedliche Kommunikator verwendet,  hat man die Situation, das für ein send nur ein receive da ist und somit ist der Konflikt gelöst
- Matching von Kollektiven Aufrufen innerhalb von communicators passiert in der Reihenfolge in der die Calls aufgerufen wurden auf dem Prozess
- Macht man eine inter-thread Sync kann man die Reihenfolge in der man MPI Calls von nebenläufigen Threads Aufruft steuern