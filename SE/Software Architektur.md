‘### Woraus besteht die Software Architektur?
- Festlegen von bestimmten Qualitätsmerkmalen, welche wichtig für das System sind
	- Ergibt sich aus den Ergebnissen der Anforderungsanalyse, inbesondere der nicht-funktionale Anfoderungen
- Architekturstile festlegen
	- Zum Beispiel Schichtenmodell, Pipes and Filters, usw
- Treffen bestimmter Entscheidungen, welche für die Architektur wichtig sind
	- Welche Art von Web Frameworks wollen wir unterstützen?
	- Welche schichten können miteinander Interagieren?
	- Welches Datenformat soll für den Austausch verwendet werden?
- Entwurfsprinzipien festlegen
	- NoSQL Datenbanken sind die bevorzugten Speicheroptionen
	- Nutze asynchrones Kommunizieren zwischen Services wenn möglich

## Architektur und Design
### Wofür ist das Architekturteam zuständig
- Sie extrahieren die relevanten Qualitätsmerkmale für das System aus der Anforderungsanalyse
- Sie wählen welche Stile im System realisiert werden sollen
- Sie legen die Komponentenstruktur fest
- Sie geben den Input für das Entwicklungsteam

### Wofür ist das Entwicklungsteam zuständig?
- Sie Designen die Klassenstruktur für alle Komponenten
- Sie Designen das User Interface
- Sie schreiben und Testen den Sourcecode
- Geben Feedback and das Architekturteam

### Charakteristiken der Architektur
- Eine Architektur Charakteristik trifft Folgende kriterien
	- Trifft Entwurfsentscheidungen, welche nichts mit der Domain zu tun haben
		- Spezifiziert operationelle und Design Kriterien, welche sich darauf konzentrieren, wie man eine gegebene Anforderung implementiert
	- Beeinflusst strukturelle Design Aspekte
		- Benötigt die Einführung eines spezifischen Architektur Elements
	- Kritisch oder Wichtig, damit Anwendungen funktionieren wie gewünscht

**Operationell:**
- Verfügbarkeit
	- Bestimmte Zeiten, wann das System online / benutzbar sein muss
- Performance
	- Betrifft peak Analyse, Antowortzeiten, Stresstests
- Skalierbarkeit
	- Fähigkeit mit steigender Anzahl von Zugriffen, Usern, etc. fertig zu werden

**Strukturell:**
- Erweitbarkeit
	- Wie gut kann man neue Funktionen hinzufügen
- Wartbarkeit
	- Wie leicht kann man das System anpassen oder verbessern?
- Nutzbarkeit
	- Wiederverwendbarkeit von gemeinsamen Komponenten unter verschiedenen Produkten
- Lokalisierung
	- Support für verschiedene Sprachen, Währungen, Einheiten, usw.
- Konfiguration
	- Möglichkeit für End Nutzer ihr System via nutzbaren Interface an ihre Bedürfnisse anzupassen 

**Cross-Cutting:**
- Accessibility
	- Weite Nutzbarkeit, auch für Nutzer mit Behinderungen
- Privatsphäre
	- Möglichkeit Daten für unauthorisierte Personen unerreichbar zu machen
- Sicherheit
	- Verschlüsselung der Datenbank, des Netzwerkverkehrs, Authentifizierung, Authorisation,...

### Architekturelle Stile
- Sie helfen dabei die fundamentale Struktur eines Softwaresystems zu spezifizieren
- Sie haben einfluss auf das Erscheinungsbild von konreten Software Architekturen
- Sie definieren die globalen Eigenschaften eines Systems
	- Wie kooperieren verteilte Systeme und wie tauschen die Daten aus?
	- Grenzen von Subsystemen

Beispiel:
- Monolithisch
	- Schichtenmodell
	- Pipes and Filters
	- Model-View-Controller
- Distributed
	- Service basiert
	- Broker
	- Microservices

### Monolithische Architektur Stile
**Geschichtet:**
![[Bildschirm­foto 2023-02-19 um 14.44.28.png]]
- Topologie
	- Anzahl und Namen von Schichten sind nicht fest
	- Manche Architekturen kombinieren Business und Persistance Layer
	- Manche Architekturen nutzen zusätzliche Schichten um wiederverwendbarkeit oder begrenzten Zugriff zu ermöglichen
- Entscheidungen über die Architektur
	- Definition der Aufgabend jeder Schicht
	- Schichtentyp (open oder closed)
		- Top-Down requests müssen durch closed Schichten, können aber open Schichten überspringen
- Trade Offs
	- +
		- Einfach und Kostengünstig
		- Verlässlich
	- -
		- Nicht oder schlecht Skalierbar
		- Performance schlechter, weil Parallelisierung nicht von Grund auf möglich ist
		- Verfügbarkeit schlechter, weil Startup-zeiten normalerweise sehr hoch

**Pipes and Filters:**
![[Bildschirm­foto 2023-02-19 um 14.56.32.png]]
- Topologie
	- Pipes
		- unindirektionale, punkt-zu-punkt Kanäle von einer Datenquelle zu einem Ziel
		- Erlauben alle Datenformate
	- Filters
		- Eigenständig und unabhängig von anderen Daten
		- Zustandslos, das heißt ihre Funtionalität hängt nicht von der Vergangenheit ab und sollte genau eine Aufgabe realisieren
		- Verschiedene Arten von Filtern
			- Producer
				- Quelle von Daten
			- Transfromer
				- Bekommt daten von seinem input Channel
				- Führt eine Aktion aus
				- Leitet das Ergebnis über den Outputchannel weiter
			- Consument
				- Daten werden auf dem Display ausgegeben, oder in eine Datei bzw Datenbank gespeichert
			- Branching ist mithilfe von Testern auch möglich
				- Der input wird überprüft und schickt die Daten basierend auf dem Ergebnis an die entsprechenden Output Channel weiter

**Model-View-Controller:
![[Bildschirm­foto 2023-02-19 um 15.27.36.png]]**
- Topologie
	- System wird in drei Module aufgeteilt
		- Model
			- Businesslogik und Datenspeicher unanhängig von input behavior und output repräsentation
		- View
			- Präsentation der Modeldata für den User
				- Daten werden vom Model gezogen
				- Meistens mehr als nur eine View
		- Controller
			- Übersetzt Userinteraktionen zu Operationen auf dem Model
			- Alle Interaktionen gehen über den Kontroller
	- Controler und View sind direkt mit dem Model verbunden, das Model aber nicht direkt mit dem Controler oder der View
- Change Propagation
	- Ein Change Propagation Mechanismus sorgt für konsistenz zwischen UI und dem Model
	- Idee:
		- Views melden sich selbst im Model an
		- Model alamiert die registrierten Views bei einer Veränderung
- Wann sollte man MVC verwenden?
	- Wenn die Model Daten auf unterschiedlicher Art und Weise dargestellt werden soll
	- Wenn die Anzahl und Art der Views nicht fix ist
	- Wenn Display und Anwendungsverhalten Datenänderungen sofort anzeigen müssen
	- Wenn das wechseln und übertragen der UI nicht den Kern der Anwendung beeinflussen sollte
- Trade Offs
	1. Updates wuchern, aber nicht alle Views brauchen alle Veränderungen
	2. Komplexität steigt durch seperate views und Kontrollerkomponenten ohne viel flexibilität dazu zu gewinnen 
	3. Starke abhängigkeiten zeischen View und Controller

### Distributed Architekturstile
**Service-Based:**
![[Bildschirm­foto 2023-02-19 um 15.50.53.png]]
- Topologie
	- Main
		- Ein monolithisches UI für alle Services
		- Jeder Service $i$ ist aus verschiedenen Komponenten $C^i_j$ zusammengesetzt
		- Services teilen sich eine Datenbank
	- Varianten
		- Nicht monolithische User Interfaces
			- Domain Based UI
			- Service Based UI
		- Service-Local Databases
			- Jeder Service kann seine eigene Datenbank haben
			- Es können sich verschiedene Services beliebig Datenbanken teilen

### Wovon hängt die Entscheidung für einen Architekturstil ab?
- Domain
- Architkurelle Charakteristiken
- Daten Architektur
- Organisations Faktoren
- Entwicklungsprozess

