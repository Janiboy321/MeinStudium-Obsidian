### Wie sichert man Softwarequalität zu?
Zentrales Stück ist ein "Software-Qualitätssicherungsplan"
	- Auch wichtig:
		- Design Prinzipien
		- Design Techniken
		- Design Patterns
		- **Verification**
		- Validation


### Validierung vs. Verifikation
##### Validierung:
> Bauen wir überhaupt das richtige System?
- Wir bauen ein Softwaresystem, welches den wünschen und anforderungen des Kunden gerecht wird.
- Sind die implementierten features wie gewollt und vollständig implementiert?
- Passt das fertige system in den Arbeitsablauf der Organisation, welche die Software benutzen soll?
→ Validierung kann niemal ohne die Einbeziehung der KundInnen / bzw. NutzerInnen geschehen
##### Verifikation:
> Bauen wir das System in einer korrekten Art und weise?
- Funktionieren die implementierten funktionen so, wie sie spezifiziert sind?
- Verhält sich das System vernünftig, auch wenn es fehlerhafte Eingaben gibt, oder irgendetwas schief geht?
→ Verifikation geschieht auf Seiten der Entwickelnden

### Verifikationstechniken
#### Static
- Programm muss nicht unbedingt ausgeführt werden
	- Heißt: Das Programm kann händisch oder mit bestimmten Werkzeugen verifiziert werden

**Code Reviews**
- Kann man zu jedem Zeitpunkt des Entwicklungsprozesses anwenden

**Static Checking**
- Automatische Analyse
	- z.B. erweiterte Typchecks, bug-finder, Stylechecker, etc.

**Formale Verifikation**
- Mithilfe von fundierten mathematischem Methoden die funktionalität der Software, formal nachweisen.

#### Dynamisch
- Beruhen auf der Ausführung eines Programmes

**Testen**
- Zusichern, dass ein Programm für ausgewählte eingaben funktioniert.

**Laufzeitbeobachtung**
- Programm wird mit Zusicherungen instrumentiert, werden diese während der Laufzeit verletzt bekommen Nutzende Feedback, dass irgendwas schiefgelaufen ist.

### Code Review
- Strukturierter Inspektionsprozess für ein Stück Software
- Wird in einem Team vorgenommen
- Ziel: Möglichst viele potentielle Defekte aufspüren
- Nimmt an, dass der Entwurf schon detailliert diskutiert und gerechtfertigt wurde und die anforderungen zu diesem Zeitpunkt schon validiert wurden

#### Funtionsweise
##### Vorraussetzungen 
- Man hat tatsächlich vollständigen, aktuellen Code vorliegen, der nicht mehr in der Entwurfsphase ist.
- Man hat Spezifikationonen vorliegen, ohne welche man nicht sagen könnte, was an dem Code fehlerhaft sein könnte

##### Review
 Team Mitglieder nehmen bestimmte Rollen ein
	- Minimales Setup einer Rollenverteilung:
		- AutorIn, Owner, Verantwortliche(r)
		- InspektorIn, LeserIn
		- ProtokolantIn
		- Vorsitzende(r), ModeratorIn

##### Strukturierter Prozess:
1. Planung (Vorsitzende(r)/ModeratorIn)
		- Team auswählen, also Leute die an der Review teilnehmen
		- Raum buchen
		- Material vollständig da und verfügbar
		- usw
2. Überblick geben (AuthorIn)
		- Was soll das zu begutachtende Code-Stück machen?
		- Was ist der Sinn und Zweck?
		- In welchem Rahmen wird der Code verwendet?
3. Individuelle vorbereitung
		- Jede(r) nimmt sich das Stück Code vor, welches begutachtet werden soll und geht es alleine schonmal durch
		- Versuchen im vorfeld möglichst viele Probleme und Fehler zu finden
4. Inspektionstreffen
		- Systematisch, Zeile für Zeile das Stück software durchgehen
		- Defekte sammeln
		- Mögliche Verbesserungen auflisten
		- Wichtig: Treffen darf nicht zu lang gehen, da Aufmerksamkeitsspanne sinkt (1 bis 2 Stunden)
5. Rework (AuthorIn)
		- Software wird mithilfe des Feedbacks verbessert 
6. Follow-Up (Vorsitzende(r) / Moderator)
		- Ist die Software optimiert?
		- Sind die Verbesserrungen adequat?
		- Ist ein weiteres Inspektionsmeeting benötigt?

→ Vorbereitungen und Meeting wird durch Checklisten getrieben, welche in Generischer Form bereits vorhanden sind und mit eigenen Punkten ergänzt werden kann.

###### Vor- und Nachteile von Code Reviews
- **Vorteile**
	- Code Review sind wissenschaftlich geprüft, heißt sie funktionieren und sparen Kosten
	- Wissen über Implementierung wird innerhalb des Teams verteilt
	- Man kann fehler finden bevor sie im Test auftauchen oder gar der Code schon beim Kunden ist
	- Kann Code Qualität und die Dokumentation verbessern
	- Code Reviews können auch ohne fertigen, ausführbaren Code durchgeführt werden
- **Nachteile**
	- Code reviews fordern reife Persönlichkeiten
		- Kontext: Bei Code review wird kritisiert.
		- Beispiel in Vorlesung: Trump wäre kein gutes Mitglied einer Code Rewiew :)
	- Code reviews unter Zeitdruck fühlen sich oft an wie Zeitverschwendung, gerade wenn eine Deadline existiert.
	- Code reviews funktionieren nur, wenn sie richtig durchgeführt werden


### Software testing
> Programm testing can be used to show the presence of bugs, but never to show their absence! ~ E. W. Dijkstra

**Warum ist das so?
- Nicht triviale programme haben unzählbar viele verschiedene wege der Ausführung
	- Es ist unmöglich alle zu testen → Erschöpfendes Testen nicht möglich
Aber: Testen ist heutzutage einer der wichtigsten, wenn nicht sogar die wichtigste Art um die Quälität der Software zu sichern.

##### Was ist ein Programmtest?
- Ein Programmtest besteht aus folgenden Elementen:
	- System, bzw. Implemetation under test (SUT, IUT)
	- Test inputs
	- Testumgebung, in welcher SUT bzw IUT in gestet wird, bzw in einen Zustand gebracht wird, in dem man das System / die Implementation ausführen kann.
	- Testurteil (pass / fail) gegeben von einem Orakel (Das kann ein Mensch sien, oder ein Testendes Programm (z.B. JUnit Tests))
- Test Level
	- Testing team (not Covered)
		- System Test
			- Performance Test
			- Release Test
			- Integration Test
	- Software developer
		- Component Test
			- Unit Test
			- Interface Test
- Test Plan
	- Detaillierte beschreibung eines Testprozesses
	- Dokument, welches von Menschen gelesen werden soll
		- *Work Plan*: Phasen, Zeitplan
		- *Testing Prozeduren* (Werkzeuge?, Maßgaben? Welcher code wird getestet?)
		- Erläuterung des Test Entwurfes
- Test Design
	1. Identifizieren und Analysieren der verantwortlichkeiten der IUT
		- Vor- und Nachbedingungen für einzelne Anwendungsfälle kennen → Ergeben später Eingaben und das Orakel
		- Minimal und Erfolgsgarantien für die ausgearbeiteten Anwendungsfälle → Ergeben Testfälle welche durhcgetestet werden müssen
		- Analysieren der Verteilung der Verantwortlichkeiten im Entwurf analysieren
	2. Testfälle hinzufügen, basierend auf
		- Use-Case, Design und Code Analyse
		- Verdacht, minimale Erfolgsgarantien
		- Generelle Heuristiken (z.B. Domänen bzw. Aussagen Vorgaben)
	3. Für jeden Testfall festlegen, wie Testurteil zustande kommt
		- Erwartete Ergebnisse, programmierte oder Menschliche Testorakel
- Wichtig: Klares Fehlermodel vor Augen halten, da erschöpfendes Testen schier unmöglich

##### Automatisiertes testen
>Testen ist das Teuereste am Softwareentwicklungsprozess

##### Welche Aspekte sind beim Testen automatisierbar?
1. Test druchlaufen lassen (Beispielsweise über Nacht, nach einer änderung, etc.)(state-of-art, supported by build tools)
2. Test input generieren
	- Code-driven
	- Model-driven
	- Data-driven
3. Testurteile generieren
	 - Testurorakel (ein kleines Programm) selbstgeschrieben auf basis der Testrüstung
	 - Automatisch erstelltes Orakel auf basis der formalen Spezifikationen

##### Ablauf eines Tests
1.  Set up test environment
	- Server starten, Netzwerkverbindung einrichten, Services registrieren usw.
2. Starte IUT
3. IUT in benötigten / gewünschten Zustand bringen
	-  Benötigte Daten laden, benötigte Objekte erstellen, usw.
4. Test input einstellen
5. Output evaluieren und Urteil aufnehmen
6. Environment aufräumen
	- Daten löschen, Services stoppen, Daten reseten 

##### Ziel des Testes
>Hinreichend viel Vertrauen in die minimale Funktion der Software schaffen

- Umfassender Test
	1. Initiale Tests ausführen und solange Programm korrigieren bis jeder testfall korrekt durchläuft und das korrekte ergebnis liefert
	2. IUT mit Überdeckungswerkzeug instrumentalisieren
		- Fügt in den Programmcode bestimmte Zähler ein, anhand welcher man sagen kann, ob ein gewisses Ziel erreicht ist.
		- Sagt anhand eines Überdeckungskriteriums, wieviel Prozent überdeckung erzielt wurde.
	3. Initiale Tests nochmal ausühren und gemeldete Überdeckung prüfen
	4. Wenn nötig neue Testfälle hizufügen um Überdeckung zu steigern
	5. Testen beenden sobald Übderdeckungsziel erreicht wurde und alle Tests korrekt durchgeführt werden

##### Test Input
- Testpoints
	- Wert für ein Testfall
	- Wert für eine Status Variable
	- Wird von anhand einer Domäne gewählt
	- Die Domäne ist eine Sammlung an Werten von welchen input bzw statevariables ausgehen können
- Bestimmung von Testpoints
	- Es gibt bestimmte heuristiken
		- Equivalente Klassen (nur ein Punkt für erwartete equivalente Ergebnise)
		- Boundary values (min/max von Domäne, pivot von Vergleichen)
		- Spezielle Werte (z.B. Zeichen mit speziellen Semantiken)

##### Testfall und Testsuit
- Ein Testfall besteht aus
	- Status der IUT vor dem Test
	- Testpoints und Konditionen
	- Erwartete ergebnisse
- Eine Testsuit besteht auf mehreren Testfällen
- Testlauf
	- Ausführung einer Testsuit / eines Testfalls und deren Ergebnisse
	- Entsprechen die Ergebnisse den erwarteten Test bekommt der Testlauf das Urteil passed wenn nicht dann das Urteil failed

##### Test Driver und Test harness
- Test driver
	- Klasse oder Programm welches Testfalle an einer IUT ausführt
 - Test harness 
	- System von Test drivern und andere tools um die testausführung zu supporten

##### Fault und Failure
- Fault
	- Fehlender oder inkorrekter Code
- Failure
	- Unfähigkeit eines Systems oder einer Komponente, dafür eine benötigte funktion mit spezifizierten Limits auszuführen

##### JUnit
Siehe www.junit.org 
bzw. https://moodleload.hrz.tu-darmstadt.de/FB20_SE/SE/Lecture09/chapters/SE_09_Verification_Part_1_Chapter_4_Test_Automation.mp4 
bzw. https://moodleload.hrz.tu-darmstadt.de/FB20_SE/SE/Lecture09/SE_Lecture_09_Verification_Part_1_JUnit_Demo.mp4


### Test Coverage
>Wann können wir aufhören zu Testen?

##### Strukturelle Kriterien
Beziehen sich auf den Kontrollflussgraphen eines Programmes:
- **Statement Coverage**: für jedes Statement **s** ist ein Test in der Testsuit unter welchem **s** ausgeführt 
- **Basic Block Coverage**: alles Basic Blocks wurden mindestens einmal ausgeführt, änhlich wie SC, jedoch ist BBC **Basic Block Coverage auf einer Maschine oder als Bytecode definitert 
- **Branch Coverage**: Jede Kante der KFG wurde in einer Testsuit innerhalb mindestens einem testrun durchgeführt
- **Path Coverage**: Alle Pfade des KFG wurden mindestens einmal Ausgeführt

##### Logische Kriterien
Beziehen sich auf Logik (u dont say)
`//condition / bedingung -> i == a, 1 != 2, isBla == true,...`
`//decision / entscheidung = (i == a && 1 != 2 && isBla == true)`
- **Condition Coverage**: Jede logische Bedingung muss in einer Testsuit in mindestens einem Testrun mit true und in mindestens einem weiteren Testrun mit false bewertet werden
- **Decision Coverage**: Jede decision muss in einer Testsuit in mindestens einem Testrun mit true und in mindestens einem weiter Testrun mit false bewertet werden
- **Modified Condition Decision Coverage**: Kombiniert Condition, Decision und independence test: *Jede variation der Bedingungen, welche das Ergebnis der entscheidung, in welcher sie vorkommen, beeinflusst, muss getestet werden.
- **Multiple-Condition Coverage**: Alle true und false Kombinationen von Bedingungen innerhalb einer Entscheidung, müssen getestet werden. Beispiel: `boolean a, boolean b, resEntscheidung = a && !b`, benötigte test inputs: (true, true), (true, false), (false, false) und (false, true).

### Automatische Test Case Generierung
- White Box
	- Code basiert
	- **Synthetischer versuch**: Man scannt nach Bedingungen und Entscheidungen und generiert systematisch Testfälle, welche die entsprechenden Überdeckungskriterien garantieren
		- Aufwendig, aber machbar
		- Eventuell werden Tests für unerreichbaren Code generiert -> Over-approximation. 
	- **Symbolische Ausführung**
		- Man rollt den KFG aus, mit symbolischen Anfangswerten um eine ganze reihe von strukturellen Überdeckungskriterien zu realisieren.
			- Eventuell wird Code nicht erreicht -> under-approximation
- Black Box
	- Daten bzw. Model Basiert
	- Modell der vorliegenden Software erstellen (Abstraktion, z.B. Zustandsautomat)
**Probleme: Wie geht die Automation mit Bibliotheksaufrufen um? Wie mit unrelevanten Testfällen und wie mit deep loops / recursions

##### Test Coverage Recording
1. Instrumentalisiere IUT
2. Lasse den Test laufen und Sammle informationen wärend dem Test
3. Analysiere und zeige erreichte Testüberdeckungsstatistiken
> Hilft nicht beim schreiben von Testfällen, aber dabei zu erkennen, wann man aufhören kann

##### Test Orakel Synthese
- Menschliches Orakel: Zeitaufwendig, fehleranfällig und teuer (Lohn)
- Urteil via Code (z.B. assert it JUnit): Benötigt Expertiese und ist schwer zu pflegen (Wird der Code geändert muss eventuell auch der Code verändert werden)
Also: Schreibe Formal auf, wie soll das Programm funktionieren soll und synthetisiere daraus Test-Code (Challenge: Effizienten code aus Formalen Text zu entwickeln)

##### Automatisch Statische Verifikations 
- **Statisches Checken
	- Basieren auf KFD (Oder ähnlichen Diagrammen) des IUT + constraint solving, also finden einer Lösung, welche bestimmte bedingungen erfüllt
	- Geprüft werden statisch gegebene Eigenschaften wie runtime exceptions oder Informationsfluss
	- Typischerweise vollständig automatisiert
	- Over-approximierend, also Tests für Fälle, welche eigentlich garnicht eintreten können
	- Basierend auf Algorithmen, welche normalerweise gut skalieren 
- **Bug finder
	- Basiert auf pattern matching und heuristiken
	- Schnell, skaliert gut und handlet JAVA
	- Über und Unter - approximiert (falschpositiv und unvollständig)

##### Formale Verifikation
- Formale ansätze
	- Basieren auf präzisen und Mathematsich fundamenten (Logik und Mengentheorie)
	- Normalerweise vertrauenswürdige ergebnisse
	- Nicht immer vollständig, möglicherweise kompilieren sie nicht, usw.
- Formale Verification
	- Beweist, dass ein Programm den formalen Anforderungen entspricht
	- Model cheking:
		- Bandera, Java PathFinder, SPint, SDV/SLAM, etc.
	- Deductive verification:
		- KeY, KIV, VCC, VeriFast, jStar, etc.

##### Deduktive Verifikation
- Design by Contract
- Beispiel:
	```
	/@ public normal_behavior
	@requires a != null;
	@ensures \result != -1 ==> a[\result] == entry`;
	@/`
	public int findFirstEntry(int[] a, int entry){...}
	```
 - Pre- und Postconditions, Nebeneffekte für jede Methode
- Klassen und schleifen Invarianten
Verifikartionstool beweist das jede Methode
- Ihr contract erfüllt, in allen möglichen runs
- die loop und Objekt invarianten beibehält

##### Dynamische Verifitkation
- Runtime Monitoring
```
/@ public normal_behavior
	@requires a != null;
	@ensures \result != -1 ==> a[\result] == entry`;
	@*/
	public int findFirstEntry(int[] a, int entry){
		for(int i = 0; i < a.length; i++){
			if(a[i] == entry){
				return i;
			}
		}
		return -1;
	}
```
- Inline preconditions, postconditions, invarianten werden als assert anweisungen hinzugefügt --> an Java Expressions gebunden
```
/@ public normal_behavior
	@requires a != null;
	@ensures \result != -1 ==> a[\result] == entry`;
	@*/
	public int findFirstEntry(int[] a, int entry){
		assert i != null;
		for(int i = 0; i < a.length; i++){
			if(a[i] == entry){
				assert i != -1 ? a[i] == entry : true;
				return i;
			}
		}
		assert i != -1 ? a[i] == entry : true;
		return -1;
	}
```


### Merken
- Testen ist bei weitem der wichtigste und weitverbreiteste verifikations Ansatz
- Automatische Testfall ausführung ist standard (und essentiell)
- Code review sind nicht genug gewertschätzt
- Automatische Verifikations werkzeuge beinhalten bugfinder und static checkers
	- Problem: Hohe rate von Falschpositiv
- Automatische Testgenertoren erfordern expertiese und sind unrobust, aber.
	- potenziell kostensparend
	- Überdeckungs garantien möglich
	- viele verschiedene Industrielle tool existieren
- Formale Verifikation wird hauptsächlich für Sicherheits-Kritische Systeme oder spezifische anwendungs szenarien vorgenommen