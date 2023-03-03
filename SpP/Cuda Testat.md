# SpP Testat

#### Was ist eine GPU?
- Graphical Processing Unit
- Anwendung in Grafischen User Interfaces, Videospielen und visualen Foto Anwendungen
- Moderne GPUs sind hoch Parallelisierbar
- Sie sind hoch Multithreaded (Optimiert für das Visuelle Computing)

#### Was ist der Unterschied zwischen CPU und GPU?
- CPU
	- Wenig große Cores die viel können
	- Kleinere Anzahl an Prozessoren (~100)
	- Komplexe Kerne mit Control logic um instruction-level Parallelilismus zu maximieren
	- Relativ große Menge an Mainmemory pro Kern
	- Effiziente Betreibung der Caches
- GPU
	- Ganz viele kleine Cores die wenig können
	- Größere Anzahl an Prozessoren (~1000)
	- Wenig Kontrolllogik
	- Massive Anzahl an Threads
	- Daten parallele berechnung
	- Code mit vielen Berechnungen
	- Power Effizient
	- kleiner Caches

#### Data-parallel problem decomposition
- Es ist wichtig zu verstehen, dass CUDA auf gittern und Blöcken arbeitet
- Ein Grid ist ein Gitter aus Blöcken
- Ein Block ist ein Kernel
- In jedem Block habe ich bestimmte Berechnungnen drinnen
- Ich kannjeden block unabhängig von anderen Berechnen
- In einem Block kann ich jedes element von diesem Block unabhägig von jedem anderen Berechnen

Ein Grid besteht aus mehreren Blöcken, ein Block besteht aus mehreren Elementen, welche auf Threads aufgeteilt werden

#### CUDA Device Memories
1. Wir haben ein Grid mit Blöcken
2. Jedes Grid hat einen Globalen Speicher und einen Konstanten Speicher
3. Auf dem Globalen Speicher können Threads und der Host lesen und schreiben während auf dem konstanten Speicher die threads nur lesen können und der Host lesen und schreiben kann
4. In diesen Blöcken haben wir Threads, jeder Thread hat seine eigenen Register und ein lokalen Memory
5. Jeder Block hat einen eigenen Shared Memory, sodass die Threads untereinander Daten austauschn können

#### Scalable Programming Model
- Da die Blöcke unabhängig voneinander ausführbar sind, kann man sie abhängig von der Hardware unterschiedlich aufteilen. So kann man bei einer GPU mit 2 Streaming Multiprozessoren jeder SM jeweils 4 Blöcke geben oder einer GPU mit 4 Streaming Multiprocessoren jedem SM 2 Blöcke zuordnen

#### Scheduling
- Jeder Block muss unabhängig ausführbar sein
- Grids können abhängig voneinander oder unabhängig voneinander ausgeführt werden

#### Parallele Ausführung
- Die Parallelisierung und ausführung der Threads passiert automatisch, das passiert in der GPU
- Threads von Blöcken laufen parallel zueinander und können mit Barriers parallelisiert werden

#### Virtualisierung
### WIEDERHOLEN

#### Zwischenstand
- Was ist ein Kernel?
    - Der Kernel wird von innerhalb eines seriellen Main Programms aufgerufen
    - Einfache Funktion oder volles Programm
    - Wird parallel unter verschiedenen Threads ausgeführt

- Was ist ein Grid?
    - Eine Menge von Blöcken, welche unabhängig voneinander ausgeführt werden können, mas parallel passieren kann

- Was ist ein Thread block?
    - Threads werden in einer Hirarchi von Blöcken organisiert
    - Eine Menge von Threads, welche untereinander kooperieren mithilfe von barrier synchronisierung und zugriff auf Shared Memory des Blockes
    - Die aktuellen GPUs haben ein Maximum von 1024 Threads pro Block

#### CUDA Parallelilismus
- Wir müssen parallelität in CUDA explizit auszeichnen
    - Wir müssen sagen, was parallel zu berehcnen ist, wenn das passt, dann ist das gut, wenn nicht ist das sehr langsam

#### Restrictions
- Blöcke sind independent
- Wenn ich Ergebnisse mehrerer Blöcke verarbeiten möchte, mache ich das üblicherweise indem ich in der nächsten Runde einen neuen Kernel aufrufe, der das übernimmt
- Rekusrion nur nutzbar ab capability 2
    - Durch niedrigem speicher limitiert

#### SIMT
- SM erschafft, managed, plant und führt Threads immer in Gruppen von 32 parallelen Threads aus
    - Das wird Warp genannt
- Was passiert, wenn eine Ausführung läuft?
    - Eine SIMT Instruktion wird gescheduled und damit wird 32 Threads gesagt, was sie zu tun haben
- Welcher Warp ausgesucht wird hängt davon ab, welcher seine Daten hat
- Das Bedeutet wenn so eine SIMT instruktion auf einem warp ausgeführt wird, es einen kleinen Broadcast gibt, der jedem der kleinen Thread sagt, was er zu tun hat
    - Gleiche Instruktion an alle, also alle 32 Threads machen das gleiche
- Es kann inaktive Threads geben, wenn ich einen branch hatte, wie mache ihc dann einen Branch?
    - Erst if dann Else

#### Warp Scheduling
- Normalerweise gibt es mehr warps in einem Multiprocessor, als wirklich gleichzeitig ausgeführt werden können

#### Zero Overhead thread Scheduling
- Scheduling eines warps ist im wesentlichen instantan weil es in der Hardwar epassiert
- Die Daten die ich brauche um einen Thread wieder zum leben zu bringen sind in den Registern

#### SIMT performance
- Ein Warp kann löcher haben
	- Heißt es gibt inaktive Threads, die eigentlich aktiv sein könnten (Sagt aber nichts über die korrektheit des Programmes aus)
	- Lösung: Alle Threads die in einem Warp sind, sollten den gleichen ausführungspfad nehmen

#### SIMD vs. SIMT
- SIMD
	- Eine Instruktion auf mehrere Datalanes
	- Benötigt Software die Data Parallelität durch Vektorinstuctionen ausdrückt
- SIMT
	- Eine Instruktion parallel auf verschiedenen, unabhängigen Threads

#### Compilation Work-Flow
![[Bildschirm­foto 2023-03-03 um 11.37.50.png]]
1. Der C-Code mit CUDA Extension wird vom NVCC Compiler Kompiliert
2. Dabei wird der C-Teil (Host Code) vom CUDA-Teil (Device Code) getrennt und auf der jeweiligen Hardware ausgeführt
- Offline
	- Compiler seperiert host und device Code
	- Kompiliert device Code in Assembly
	- Modifiziert den Host Code indem <<<>>> Syntax duch runtime function calls ersetzte werden
- Just in time
	- PTX code welcher von einer Anwendung zur Laufzeit geladen wird, wird vom Device Driver in  