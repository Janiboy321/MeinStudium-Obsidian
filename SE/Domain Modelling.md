### Was bedeutet Domain Modelling?
- Terminologie und fundamentale Aktivitäten festlegen
- Warum: Hilft dabei die relevanten Aufgaben und konzepte der Domain zu identifizieren
- Vorbedingungen: Anforderungsanalyse und Use Case Analyse sind fertig
- Kontext: Teil der objekt-orientierten analyse
- Heuristiken: Wird nur für anstehende Aufgaben durchgeführt
> Domain Model muss mit dem Klienten validiert werden

### Domain Model
_oder auch Analysemodell bzw. Konzeptmodell_
- Ein Objektorientiertes Domain model 
	- teilt die Domain in Konzepte und Objekte, welche die reale Welt repräsentieren, auf
	- Identifiziert die Menge der konzeptionellen Klassen und fundamentalen Aktionen
	- wird iterativ vervollständigt und formt die Basis für das Softwaredesign

### Konzeptionelle Klassen
- Konzeptionelle Klassen repräsentieren Ideen, Dinge oder Objekte in der Domain
- Eine konzeptionelle Klasse hat
	- einen Namen
	- einen Intention ("Bedeutung")
	- eine Extension ("Ausprägung", "Extension")
		- Die extension enthält die Domain Elemente welche die konzeptionelle Klasse repräsentiert

### Visualisierung von Domain Models
- Domain Models werden mithilfe von UML Klassen Diagrammen visualisiert
- Dabei gibt es bestimmte Regeln, um das Domain Modelling hervorzuheben:
	- Es gibt nur Objekte und konzeptuelle Klassen
	- Es gibt nur assoziationen, keine Gruppierungen und keine Zusammensetzungen
	- Klassen können Attribute haben, aber keine Operationen

### UML Klassen Diagramm
**Bestandteile eines Klassendiagramms**
- Klassen 
	- Eine konzptuelle Klasse beschreibt eine Menge von Domain Objekten
		- Ein Objekt ist ein Individuelles Objekt mit einem Status und Beziehungen zu anderen Objekten
- Attribute
	- Eine Klasse kann Attribute haben
	- Logische Datenwerte eines Objektes
	- Man kann Objekte der bestehnden Klasse auf Objekte ihrer Zielklasse abbilden
	Während dem Domain modelling:
		- Identifiziere Attribute der konzeptuellen Klasse welche benötigt werden um Informationsanforderungen zu erfüllen
		- Limitiere Anzahl der Attribute auf Umfang der behandelten Szenarien

**Einfache Version eines Klassen Elements**
![[Bildschirm­foto 2023-02-18 um 18.19.14.png]]
- Class Name: Klassennamen starten immer mit einem großen Buchstaben
- Attribute:
	- Attribute Name: Starten immer mit einem kleinen Buchstaben
	- Attribute Type: Vordefinierte Typen oder andere Domain Model Klassen
- Abgeleitetes Attribut: 
	- Namen beginnen immer mit einem Slash ("/")
	- Werte sind aus existierenden Quellen ableitbar

**Assoziationen**:
![[Bildschirm­foto 2023-02-18 um 18.25.42.png]]
- Name ist optional
- roleA / roleB
	- Default ist der Klassenname, nur klein geschrieben
- multA / multB
	- Default ist 1, kann aber mehr bzw. weniger, in einer bestimmten Range (a..b), oder beliebig ($*$) sein;
- (Es gibt auch eine Richtung, die wird aber bei konzeptionellen Klassen nicht verwendet)

**Vorgehensweise**
1. Identifiziere die kozeptionellen Klassen
	1. Re-Use oder modifiziere ein bereits Existierendes Modell
	2. Nutze eine Kategorienliste
	3. Identifiziere Nomensphrasen
2. Zeichne die ermittelten Konzeopte als Klassen in ein UML Klassen Diagramm
3. Füge die Attribute hinzu
4. Füge beziehungen hinzu

**Kategorienliste**
Potentielle Elemente:
- Physische oder Greifbare Objekte
- Spezifikationen oder Beschreibungen von Objekten
- Orte
- Events
- Transaktionen
- Transaktionselemente
- Organisationen
- Rollen von Menschen
- Container
- ...

**Nomen Identifikation**
- Workflow
	1. Identifiziere Nomen und Nomenphrasen in Textbeschreibungen der Domain
	2. Sie sind mögliche Kandidaten für konzeptionelle Klassen
- Autmatisierbar?
	- Nur Teilweise:
		- Wörter in Texten natürlicher Spracher sind mehrdeutig
			- Ein nomen kann mehrere Bedeutungen haben
			- Verschiedene Nomen können das gleiche Bedeuten

Kriterien, damit ein Nomen zu einer konzeptionellen Klasse wird:
- Muss Informationen beinhalten, welche man nicht aus anderen Quellen schon beziehen kann
- Vermeide Kanidaten die nur Folgendes hizufügen
	- redundante Infomationen
	- abgeleitete Informationen
- Muss spezielle Semantiken in verbindung zur Domain besitzen 

**Beschreibende Klasse**
- Eine description class beinhaltet nur informationen die eine Entität beschreiben
- Eine beschreibende Klasse sollte nur zu der Domain hinzugefügt werden, wenn:
	- Informationen über ein Item oder ein Service benötigt werden, egal ob eine Instanz dieser Elemente oder Services existiert
	- man beim löschen der Eben genannten Elemente System Kritische Daten löscht
	- redundante oder doppelte informationen reduziert werden können

**Model als Klasse oder Attribut?**
_Heuristik_: Denken wir bei einer konzeptionellen Klasse C nicht an eine Nummer, einen Text oder ein Datum der realen Welt, ist C warscheinlich eine konzeptionelle Klasse und kein Attribut

**Nutzung von Assoziationen im Domain Modeling**
_Heuristik_: Benutze Assoziationen im Domain Modelling wenn Wissen über eine Beziehung für eine gewisse Zeit erhalten bleiben muss

**Gute Namen für Assoziationen**: 
- Klassenname-Verb-Klassenname
	- Player-steht-auf-Feld
	- Sale-Paid-by-CashPayment

**Attribut oder Assoziation?**
- Attribute sollten immer für primitive Datentypen verwendet werden
	- Boolean, Integer, Character, String
	- Date, Address, Colo, Phone Number, ...
- Mengen sollten als Klassen modelliert werden, um Einheiten anzuhängen
	- Währungen (EUR, USD, SEK,...)
	- weight (Kilogramm, cm, ...)
- Assoziationen sollten immer verwendet werden, um Relationen zwische konzeptionellen Klassen zu modellieren:![[Bildschirm­foto 2023-02-18 um 19.22.13.png]]

**Verbessern vorhandener Modelle**
- Überlege bei Stringattributen, ob sie nicht vielleicht eine eigene Klasse modellieren sollten
	- Wenn ein String eine bestimmte Struktur hat
		- z.B. maker, type, ...
	- Wenn andere operationen mit dem String assoziiert sind 
		- z.B. SteuerID
	- Wenn der String andere Attribute enthält:
		- z.B. Diesel
	- Wenn der String eine Menge mit einer Einheit darstellt
		- z.B. Euro, Gramm, ...

## Verhaltensmodelle
### UML State Machine Diagramm
> SMD sind Endliche Zustandsautomaten, wessen Transitionen mit in- und output Aktionen und Guards gewappnet sind
![[Bildschirm­foto 2023-02-18 um 19.30.53.png]]

Wenn in State1, wenn input passiert und der guard true ist, dann passiert output und man geht zu State2 über. In State2 wird ununterbrechbare Aktion d ausgeführt.

**Basic States**
![[Bildschirm­foto 2023-02-18 um 19.33.54.png]]
- Sie haben einen Namen und können eine bestimmte kombination von Folgendem sein:
	- Eingangsaktionen (Do at entry)
	- Do-Aktionen (Do while in state)
	- Ausgangsaktionen (Do at exit)
- Aktionen können zum Beispiel Methodenaufrufe sein

Es gibt noch verschiedene Arten von States:
- intial state (Kennzeichnet den Startzustand)
- final state (Kennzeichnet Abschluss)
- terminal state (Schließt ab und eliminiert das Objekt)
![[Bildschirm­foto 2023-02-18 um 19.36.42.png]]
Transitinen zwishen States
- Alle Teile die Optional sind werden mit einem "?" gekennzeichnet 
	- z.B. input? ('['guard']')? '/' output?
- Input Events können sein:
	- Aufrufevent (Methodenaufruf)
	- Zeitevent (Bestimmte Zeit in einem State verbracht)
	- Change Event (Der Wert eines Attributs hat sich verändert)
- Guard ist ein Boolean
- Output (Aktion) ist ein Methodenaufruf oder herstellerspezifischer Ausdruck
![[Bildschirm­foto 2023-02-18 um 19.43.12.png]]

**State Machine Diagrams im Domain Modelling**
>Wärend des Domain Modeling Prozesses verweist das SMD nicht auf Code

- State Machine Diagrams
	- können die Interaktionssequenz der Use Cases erfassen
	- könne mehrere verschiedene Use Cases kombinieren
	- verdeutlichen die Zustände in welchen ein Objekt sein kann
	- helfen Protokolle zu verdeutlichen
	- helfen dabei, das Domain Model zu validieren
	- helfen dabei das Domain Model zu vervollständigen
	- sollten nur benutzt werden um nicht-triviales Verhalten zu modellieren