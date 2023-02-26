### Maintenance
> Wie alle anderen komplexe Technische Artefakte, ist Software sogut wie niemals wirklich "fertig", sie muss regelmäßig gewartet werden.

Software altert nicht, und es gibt keine Abnutzung, allerdings verändert sich die Umgebung in der die Software läuft

#### Trigger von Software Wartungs Aktionen
1. Bug Fixes
	- Meist vorkommende Wartungsaktion
	- Vorsicht: Behebt man einen Bug, werden warscheinlich neue Bugs entstehen, oder die Fehlerbehebung funktioniert vielleicht nicht wie gewollt / erwartet. Also: Regressions Test
	- Bugs sollten innerhalb eines Zeitplans behoben werden. (Beispiel: Wöchentliche Updates) und man sollte einen Changelog zur verfügung stellen
	- Es empfielt sich ein Ticketing System zum priorisieren und verteilen von Aufgaben zu verwenden

2. Verändernde Anforderungen
	- Veränderungen wärend der Entwicklung
		- Einfach weinen, weil viele Projekte dann sterben, in welche vielleicht eine Menge Zeit reingesteckt wurde
	- Andere Gründe
		- Beispielsweise durch Gesetze, Feedback, usw.
		- Oder neue Anforderungen zum Beispiel durch steigende Nutzerzahlen oder wachsende Menge an Daten
	- Neue Anforderung können auch getarnte neue Feature sein
		- Wird die neue Funktionalität denn wirklich benötigt? Lohnt es sich?
		- Muss die vorherge version weiterhin gewartet werden?

3. Neue Features werden angefragt
	- Je besser eine Software funktioniert, desto eher werden neue Features angefordert
		- "Die SOftware hat dieses Problem echt gut geregelt, können wir die Software auch für diese Problem verwenden?"
	- Features werden auch durch Innovationen angetrieben
	- Features könnten auch durch neue Kunden und deren Anforderungen angetrieben werden
	> Neue Features können dazu führen, dass es verschiedene Versionen der Software gibt (Eine mit und eine ohne neues ) welche alle gewartet werden müssen

4. Evolving Hardware
	- Parallelisierung wird durch mehr cores ermöglicht
	- Neue Hardware Architekturen, z.B. x86  $\Rightarrow$  ARM
	- Peripheriy
		- Bildschirme verbessern sich $\rightarrow$ Bessere GUI
		- Speicher Technologie entwickelt sich $\rightarrow$ Einwirkung auf Backup-Anforderungen
		- Authentifikation verändert sich $\rightarrow$ Biometrische Authentifikation möglich

5. Entwickelnde Software Architektur
![[Bildschirm­foto 2023-01-31 um 14.19.10.png]]
- SaaS
	- Nur die Software wird ausgeliefert 
- PaaS
	- Software wird zum Beispiel in einer Cloud betrieben, also die Nutzenden müssen die Software nicht selbst ausführen
- laaS
	- Software wird mit System/Infrastruktur ausgeliefert

6. Evolution Software Stack
	- Bibliotheken sind Softwarepackete, müssen deshalb auch gewartet werden
	- Bibliotheken ohne gute Doku sind meistens Sinnlos
	- Bibliotheken können mobilität und virtualisierung behindern
	- Viele Firmen, welche viele Softwareprodukte anbieten, sind noch lange keine Experten in den Bibliotheken, welche ihnen zugrunde liegen
		- Firmen, welche nichts mit IT-Security am Hut haben, könnten möglicherweise Sicherheitsfunktionen in ihren Bibliotheken anbieten, welche aber schwere Sicherheitslücken haben können, eben da sich die firmen im hinblick auf IT-Security nicht auskennen.
		- Also: Für Speziale Bibliotheken an Spezialisten wenden
	- Eigene Bibliotheken sind aber vertretbar, wenn
		- Sie Zentrale Produktinhalte beinhalten
		- Business-kritische Abhängigkeiten für einzelne Anbiter kreieren
	- Programmiersprachen sind zwar downwards compatible aber möglicherweise unterstützen Compiler manche Versionen nicht auf dauer
	- Datenbanken entwickeln sich
		- Datenbankanwendungen wurden von Externen zu In-Memory Datenbanken
		-  Business Logik wird in Datenbanken verschoben, da man so an effizienz gewinnen kann

### Pipelining Parallelization Pattern
- Anforderungen
	- Domain / Rechnung kann in unterschiedliche Stufen aufgeteilt werden, welche regelmäßig, geordnet und Synchron laufen. 
	- Jede Stufe arbeitet dabei auf einem anderen Teil der Dateien 
	- Der Datenfluss legt eine Reihenfolge für die Stufen fest
- Kräfte
	- Stabile, synchrone Ordnung
	- Spezielle Stages können spezieller Hardware zugewiesen werden
	- Erlaubt das einfache Modifizieren, Hinzufügen oder Umordnen von Stages
	- Kann nicht benutzt werden um input faults zu entschärfen
- Lösung:
	- Zerlegen der Berechung in Stufen, welche auf unterschiedlichen Datensegmenten arbeiten
	- Jede Stufe läuft folgende Loop:
		1. Daten derf vorherigen Stufen erhalten (Weiter wenn alle Daten erhalten wurden)
		2. Daten verarbeiten
		3. Ergebnisse an die nächste Stage schicken (Und wieder zu 1.)

### Software Evolution
- Komplexe und wiederholte Wartungsaktionen bilden Software Evolution
- Kritische Probleme in der Software Evolution
	- "Verschlimmbesserung" - Wir denken wir haben einen Fehler behoben, haben es aber vielleicht verschlimmert oder gar andere Fehler geschaffen
		- Also Regression Testen ist wichtig, mehr Zeit fürs Testen als fürs fixen des Bugs einplanen, vielleicht kann man Beta Versionen an Erfahrene User ausrollen
	- Auseinandertriften von Spezifikation, Dokumentation und Implementation
		- Veränderte Anforderungen und neue Features initiieren einen vollen Entwicklungskreislauf

### Towards Software Variability
Drastische änderungen sorgen dafür, dass man eine neue Variante einer Software erstellt
- Veränderungen im User Daten Format sind immer Problematisch
- Veränderungen im GUI kann den Work Flow beeinträchtigen
- Verlust von Verfügbarkeit mit vorherigen Inkarnationen
- $\Rightarrow$ Alte **und** neue Version müssen Gewartet werden 

### Software Variability Engineering
Mittlerweile ist Variabilität gang und gebe in der Industrie

#### Chalenges in (Software) Veriabiltiy
- Möglicherweise kann es eine riesige anzahl an variablen geben (Millionen...)
- Bestimmte Anforderungen können miteinander Clashen (Beispiel Cabrio mit Kombi) 
- In der Software:
	- Man muss in der Lage sein die Anforderungen, Dokumentationen und die Implementationen Synchron zu halten
	- Bug Fixes müssen an allen betroffene Varianten ausgeteilt werden

#### Definitionen
- Software Product Lines
	- Eine Sammlung von Software Systemen welche gemeinsame Ziele und Produktionsweisen
	- Typische Gemeinsamkeit
		- Code Basis der Kernfunktionalität
		- Architektur
		- Implementierungssprache(n)
	- Brauchen Konzeptuelle Basis um Gemeinsamkeiten und Variabilität festzulegen
		- Konzept: Featur (Merkmal)
- Software Feature
	- Eine UNterschiedende Charakterisitk eines Software Elements (z.B. Performance, Portabilität oder Funktionalität) (IEEE 829)
- Produkt
	- Parameter die eine Implementierung festlegen (Menge von Merkmalsauswahlen und eine Menge von Instanziierungen von Parametern, ausreichend um Ausführbaren Code von einer Software Product Line zu Produzieren)
- Variant
		- Ausführbarer Code welcher ein Produkt von einer Software Product Line implementiert

### Die Natur der SPLE 
(SPLE = Software Product Line Engineering)
- Ziel:
	- Verhindern, dass man jede Variante seperat warten muss
- SPLE Prinzipien
	1. Design des Feature Spaces ist getrennt vom Software Design und im Vorhinein durchgeführt
	2. Gleiche Features sollten nicht mehr als einmal Implementiert werden
	3. Es muss möglich sein den Code, welcher ein Feature implementiert aufzufinden

### Schema von SPLE
![[Bildschirm­foto 2023-01-31 um 20.47.38.png]]
- Family Engineering
	- Hier überlegt man sich welche Merkmale man unterstützen will also welche Produkte am ende die Familie enthalten soll
	- Wiederverwendbare Teile (Artefaktbasis) werden geschaffen
- Application Engineering
	- Instanziierung der Familie in ein Individuelles Produkt, also Selektion eines Produktes wird mit der Artefaktbasis zusammen gebracht in eine Variante

### Feature Diagramme
![[Bildschirm­foto 2023-01-31 um 20.53.45.png]]
- Oben ist die Wurzel
- Sub-Feature nur existent wenn Elternfeature existent sind
- Man kann mehrere sub-Features auswählen
- Semantik als Boolean Integer Formel
$\text{FeatureName } \wedge \text{ }(\text{FeatureName} \leftrightarrow \text{SubName}_1) \text{ } \wedge \text{ } (\text{FeatureName } \leftrightarrow \text{ SubFeature}_2)\text{ }$
$\wedge \text{ } (\text{ SubFeature}_2 \leftrightarrow \text{ AFeature})$ 

![[Bildschirm­foto 2023-01-31 um 21.05.00.png]]
Der Kreis macht SubFeature$_2$  optional

![[Bildschirm­foto 2023-01-31 um 21.05.50.png]]
Der eingezeichnete Winkel(?) steht für eine Oder Beziehung

![[Bildschirm­foto 2023-01-31 um 21.08.09.png]]
Der Schwarze Kreis macht SubFeature$_2$ Verpflichtend

![[Bildschirm­foto 2023-01-31 um 21.09.13.png]]
Der hohle Winkel steht für genau ein Feature (entweder oder)

![[Bildschirm­foto 2023-01-31 um 21.13.29.png]]
Parameter mit Typ
![[Bildschirm­foto 2023-01-31 um 21.15.25.png]]
Kann auch nur spezifiziert werden

![[Bildschirm­foto 2023-01-31 um 21.16.47.png]]
Wenn Merkmale sich wiedersprechen, kann man dies mit einer Exclude Verbindung zeigen
	Beispiel: Feature Cabrio schließt Feature Dachfenster aus