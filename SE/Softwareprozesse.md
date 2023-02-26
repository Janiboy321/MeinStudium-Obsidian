#### Warum benötigen wir einen Softwareprozess?
- Größe der Aufgaben
	- Größeres Team muss organisiert werden
	- Aufgaben verteilen
	- Kollaborationsmöglichkeiten
- Komplexität der Aufgaben
	- Es gibt viele verschiedene arten von Aktivitäten
	- Abhängigkeit zwischen Aufgaben
	- Wann tun wir was?
- Qualitätskonrolle
	- Man muss bestimmen können, ob alles richtig oder falsch läuft

### Software Engineering Procces
Fundamentale 

Extreme Programming
- Sammlung von einfachen, unabhängigien Elementen/Praxen
- Teammitglied: Kunde
	- Person / Gruppe von Person die die Funktionaltitäten der Anwendung spezifiziert
	- Ist vom Team erreichbar
		- Falls nicht wird vom Kunden eine andere Person dafür beauftragt

- Praxis: Userstory
	- Anforderungen werden in Abstimmung mit den Kunden bestimmt
	- Bündiger Text mit einer Einschätzung der relativen Schwierigkeit
	- Nicht zu viele Details, die grobe Idee reicht in der Regel
	- Technische Detailt können sich immernoch verändern

##### Gute User Stories
- Stories müssen für den Kunden verständlich sein
- Jede Story muss etwas Wichtiges für den Kunden beinhalten
- Stories müssen so dimensioniert sein, dass mehrere pro Iteration implementiert werden kann
- Stirie müssen unabhängig sein
- Stories müssen testbar sen
- INVEST
	I: Independent
		Es darf keine Ahängigkeiten zu anderen Userstories geben
	N: Negotiable
		User Stories bis zu einer Iteration können immer getauscht und umgeschrieben werden 
	V: Valuable
		Muss dem End nutzer einen bestimmten nutzen erweisen
	E: Estimable
		Es muss möglic sein die größe einer User Story einzuschätzen
	S: Sizes appropriately or small
		Nicht so groß, dass es unmöglich ist mit sicherheit zu planen bzw priorisieren
	T: Testable
		Es müssen nötige Informationen gegeben sein, um die Test Entwicklung möglich zu machen

##### Element: Acceptance Test
- Ein bestimmter Teil der Userstories wird in Form eines acceptance Tests festgeschrieben
- Sie werden vor bzw parallel zu der Implementation der User Storie geschrieben
- Sobald ein acceptance Test positiv ausfällt, wird er zu der Menge der positiven acceptance Tests hinzugefügt und darf in zukunft nicht mehr failen (Soll rückbildung verhindern)

#### Element: Short Develope Cycles
- Eine Iteration bzw ein Sprint ist eine fixe Zeitspanne in welcher eine Menge von Software features implementiert wird
- Am ende jeder Iteration gibt es ein Stück ausführbare Software, welche getestet werden kann. Die software muss nicht unbedingt im finalen Produkt eingesetzt werden
- Iterationen sind in Zeitboxen eingeteilt. Können bestimmte features nicht rechtzeitig implementiert werden, wir ihre Implementation in eine andere Iteration verlegt

#### Element: The planning game
- Hier werden die Verantwortlichkeiten zwischen bussiness und entwicklung aufgeteilt
- Bussiness People entscheiden wie wichtig ein Feature ist, Entwickler entscheiden wie viel eine Featureimplementation kosten würde
![[Bildschirm­foto 2023-02-07 um 20.19.25.png]]
#### Element: Simplicity
- Das Design muss so simple und ausdruckfähig wie möglich sein
- Fokus auf aktuelle User Storie. Zukünftige sollten ignoriert werden
- Z.B. Füge nur eine Infrastruktur hinzu, wenn die Story das besagt
- Finde die einfachste Lösung für die aktuelle User Storie
- Adde features nur einmal

#### Element: Test-Driven Development
- Die Implementierung starte damit Tests zu schreiben
- Danach wird erst die Funktionalität bze das Feature implementiert
- Jeder Code wird geschrieben, um failende Test zu bestehen

#### Praxis: Continuous Integration
- Entwickler commiten ihren code und integrieren ihre arbeit mehrmals am Tag - es wird eine nicht Blockende Version Controll benutzt
- Nach jedem Commit wird das System kompiliert und alle Tests neu ausgeführt
- Anforderungen
	- Nutzung einer Version Controll (git)
	- Automatisiertes build system
	- Automatisierte Test

#### Element: Refactoring
- Verbessert die Programmstruktur, ohne das existierende verhalten zu verändern
- Jedes mal bevor man ein Feature hinzufügt sollte man sich fragen, ob man das existierende Programm verändern kann, sodass es einfacher ist, dass neue Feature zu implementieren
	- Falls ja, dann:
		- Verändere das Programm
		- Lass alle tests laufen und dann adde das neue feature

#### Praxis: Pair Programming
- Programmierer paaren sich um code zu schreiben
	- Eine/r fokusiert sich auf den besten weg eine Methode bzw ein Feature zu Implementieren
	- Der andere guckt sich an, wie der Code geschrieben wird, aber mit einem strategischen pov
- Gruppierungen ändern sich häufig, um wissen zu verbreiten
- Anforderungen:
	- Programmierer müssen auf einem vergleichbaren Level sein
	- Es muss verhindert werden, "dass einer den Code besitzt"

#### Practice: Collective Ownership
- Das Team besitzt den Code, jedes Paar kan jedes Modul auschecken
- Jeder übernimmt verantwortung für das gesammte System

#### Element: Coding Standarts
- Führe vernünftige Coding standarts ein, welche
	- am wenigsten arbeit aufweisen
	- das "keine duplikate Prinzip" beachten
	- Kommunikation anregen
	- Freiwillig vom ganzen Team angenommen
- 