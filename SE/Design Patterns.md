**Ein Pattern beschreibt:** 
- Ein Problem welches Regelmäßig in unserer Domain vorkommt
- den Kern einer Lösung für das Problem, sodass man diese Lösung mehrmals wiederverwenden kann, aber niemal exakt gleich

**Motivation:**
- Wiederverwendbare Software zu designen kann echt schwer sein
- Neulinge sind überfordert
- Experten schöpfen aus Erfahrung
- Manche Designlösungen kommen immer wieder

### Template Methode:
Ziel: Einen Algorithmus so implementieren, dass man
spezifische und wohldefinierte Teilfunktionen anpassen kann, um Varianten zu realisieren

- Skelett-Algorithmus in einer Methode definieren aber manche Schritte in Subklassen verschieben
- Oftmals ind framworks und APIs vertreten

**Struktur:**
- Es gibt eine Abstrakte Klasse, welche eine Templatemethode implementiert
- Die Templatemthode implementiert den Kernalgorhythmus indem sie andere abstrakte Operationen/Methoden verwendet
- Diese abstrakten Operationen/Methoden können in erbenden Subklassen implementiert werden und eine konkrete Funktionalität zur Verfügung stellen
Erweiternd:
- Man kann eine Default Funktionalität implementieren, indem man anstatt den abstrakten Operationen sogenannte Hooks verwendert
- Der unterschied besteht darin, dass die abstrakten Operationen/Methoden überschrieben werden müssen, wobei das bei Hooks optional ist

**Vorteile des Template Method Pattern:**
- Variante und Invariante Parts werden voneinander getrennt
- Code Dublikationen werden verhindert (Gemeinsames Verhalten wird ausfaktorisiert)
- Kontrolle über Subklass extensions

## Generelle Eigenschaften von Design Patterns
**Vorteile:**
Systematische Softwareentwicklung:
- Expertenwissen wird Dokumentiert
- Generische Lösungen, welche vorher schon gut funktioniert haben, werden wiederverwendet
- Das Abstraktionslevel der Klasse bzw. der Dokumentation wird erhöht

**Essentials:**
- Ein Pattern hat einen Namen
- Das Addressierte Problem ist relevant
- Die Lösung kann einfach an Varianten des Problems angepasst werden

Essentielle Teile eines Patterns:
- Pattern Name
	- Kurze Eselsbrücke um das Designvokabular zu erweitern
- Problembeschreibung
	- Wann wird das Pattern eingesetzt
	- Bedinungen unter welchen das Pattern eine Lösung bietet
- Lösung
	- Elemente die das Design bilden
	- Beziehungen, Verantwortungen und Kollaborationen unter diesen Elementen
- Konsequenzen
	- Kompromisse
		- Sprach- und Implementierungsprobleme
		- Auswirkungen auf flexibilität, erweiterbarkeit und/oder Portabilität

## Verhaltensbezogene Design Pattern: Observer Pattern
Ziele:
- Kommunikation unter Objekten ermöglichen ohne diese Objekte stark aneinander zu koppeln
- Trennung der zugrundeliegenden Daten von GUIs, damit man die Klassen, welche die Daten berechnen, unabhängig von den Klassen, welche die Daten präsentieren, benutzen kann.

**Kommunikation ohne Coupling:**
- Aufgabe
	- Entkoppeln von Datenmodellen ("Subjekt") von Parties ("Observern"), welche sich für veränderungen von internen Status interessieren
- Anforderungen
	- Subjekt soll keine Details über die Observer kennen
	- Identität und Anzahl der Observer ist nicht vordefiniert oder Fix
	- Neue Observerarten können jederzeit zum System hinzugefügt werden
	- Abfragen sind ein ineffizientes Kommunikationsmuster

**Struktur:** ![[Bildschirm­foto 2023-02-23 um 17.24.52.png]]
- getState() und modifyState() von ConcreteSubject sind Platzhalter für implementierende Methoden von Konkreten Subjekten, welche den Status erhalten bzw. modifizieren

**Participants:**
- Subjekte (Abstrakte Klassen)
	- Kennen ihren Observer, aber nur ihr public Interface
	- Liefern Operationen für das Anfügen/Entfernen von Observern
- Observer (Interface)
	- Definiert ein Interface für das Empfangen von Benachrichtigungen über veränderungen in einem Subjekt
- ConcreteSubject
	- Speichert den relevanten Zustand für ConcreteObserver Objekte
	- Sendet eine Benachrichtigung zu seinen Observern bei veränderungen der Status
- ConcreteObserver
	- Beinhaltet eine Referenz auf ein ConcreteSubject Objekt
	- Speichert Zustand, welche konsistent mit dem ConcreteSubject sein muss
	- implementiert das Observerinterface für notification updates

**Benachrichtigung über Veränderungen:**
1. Klient ändert den Zustand von dem ConcreteSubject
2. ConcreteSubject ruft seine eigene Methode notifyObserver() nach jeder Zustandänderung auf
3. notifyObserver() ruft die Methode update() aller oberserver auf

**Vorteile:**
- Abstraktes Coupling zwischen Subject und Observer
- Support für Breitbandkommunikation
	- notifyObservers() spezifiziert seine Empfänger nicht
	- der Absender kennt den Konkreten Typ der Empfänger nicht

**Nachteile:**
- Es besteht die Gefahr von Update Kaskaden für Observer und ihre abhängigen Objekte
- Updates werden an alle Observer geschickt, aber nicht alle Observer interessieren sich für den veränderten Teil
- Es fehlen Detaills über die Veränderung
	- $\Rightarrow$ Observer müssen herausfinden, was genau sich verändert hat
- Ähnlicher Update Interface für alle Observer
	- $\Rightarrow$ Subject kann keine Optionalen Parameter an die Observer schicken 

**Probleme bei der Implementierung:**
- Wer informiert die Observer über die Statusänderung?
	- Alternative 1 - Methoden welche den Status verändern
		- Vorteie
			- Nah an dem eigentlichen Subject State Change
			- Observer werden verlässlich informiert
		- Nachteile
			- Bei vielen Veränderungen auf einmal wird trozdem jedes mal geupdatet, was Beispielsweise zu vielen Screen refreshes führen kann
	- Alternative 2 - Klienten welche die veränderung initiieren
- Wie werden Informationen über Updates übergeben?
	- Pull Mode
		- Subjekt wird nach veränderung durchsucht
		- Normalerweise zu feingranular
	- Push Mode
		- Veränderte Details werden an Update übergeben
		- Sorgt für ein effizientes Updaten der View
- Subjekt mit Subklassenhirarchie
	- In dem Beispiel der Vorlesung wird in einer Subklasse, welche eine andere Klasse erweitert, innerhalb einer Methode erstmal die Methode der vererbenden Klasse aufgerufen, dann etwas verändert und dann Benachrichtigt. Das Problem besteht darin, dass der Aufrug der Methode der Superklasse schon eine Benachrichtigung rausschickt und somit zu früh benachrichtigt wird
	- Lösung: Die Logik für die Veränderung des Modells und das benachrichtigen wird in seperate Methoden aufgeteilt

**Spezifizieren der Objekte welche ein Oberserver Interessieren:**
- Relevante Aspekte spezifizieren:
	- Man kann relevante Aspekte als Attribut spezifizieren, wenn man den Observer registriert
		```java 
	addObserver(Observer, Aspect);
		```
	- Wenn sich jetzt etwas verändert, kann man alle Observer informieren, die sich für den veränderten Aspekt interessieren
	```java 
	triggerUpdateFor(Aspect)
	```
- Verschiedene Observer Interfaces für verschiedene Aspekte
	- Es gibt verschiedene Observer Interfaces in Java
		- ActionListener, MouseListener,...
	- Subjekt liefert einer Methode zum registrieren von supporteten Listener Interfaces
		- addMouseListener(MouseListener),...
	- Observer implementieren dann das listener Interface (Meistens als innere Klasse der View)
	- Subjekt informiert die listener, wenn sich etwas für sie relevantes Verändert (z.B. Mouse Click auf einen Button)

## Erschaffendes Design Patter: Factory Method
**Motivation:**
- Wir nehmen an, wir entwickeln ein Framework für Anwendungen welche dem User multi-format Dokumente anzeigen kann
	- Dafür brauchen wir eine weite Bandbreite an Anwendungssoftware:
		- Text Editor
		- Word Processor
		- Vektor drawing
		- Document Viewer
		- ...
	- Also: Das Framework muss dazu in der Lage sein, die Dokumente zu managen
- Lösung: Wir deklarieren ein Interface für das kreieren von Objekten, lassen aber die Subklassen entscheiden, welche Klasse sie instanziieren wollen

**Struktur:** ![[Bildschirm­foto 2023-02-23 um 19.09.07.png]]
- Product
	- Deklariert ein Interface für Objekte, welche von factoryMethod() erschaffen werden
- ConcreteProduct
	- Implementiert das Produktinterface
- Creator
	- Deklariert factoryMethod() welche ein Objekt des Types Object zurück gibt
	- Creater kann auch eine Default-Implementierung von factoryMethod() definieren, welche ein ein Default ConcreteProduct Objekt zurück gibt
- ConcreteCreator
	- Überschreibt factoryMethod() um eine Instanz eines ConcreteProducts zurückzugeben

**Konsequenzen und Varianten:**
- Konsequenzen
	- Der Klienten Code kennt nur das Produktinterface
		- $\Rightarrow$ Funktioniert mit jeder ConcreteProduct Klasse
	- Liefert einen Hook für Subklassen
		- $\Rightarrow$ Kann eine erweiterte Version eines Objektes via Hook liefern
- Varianten
	- Creator ist Abstrakt
	- Creator ist Konkret und liefert vernünftige default Implementierung

## Erschaffendes Design Pattern: Abstract Factory
> Wie erschafft man eine Familie von verwandten Klassen, welche ein(e Menge von) gemeinsamen/s Interface(s) implementieren

Beispiel: Verschiedene Databases supporten
- Anforderungen
	- Die Anwendung sollte verschiedene Database Formate unterstützen
	- Wir wollen Database Formate unterstützen, welche bis jetzt unbekannt sind

Variirende Databases könnte man zum Beispiel mit einem Gemeinsamen Interface unterstützen:![[Bildschirm­foto 2023-02-23 um 19.23.39.png]]

**Motivation:**
- Wie kann man verhindern, den concreteType bei der erschaffung kennen zu müssen?
	- Folgendes Beispiel wollen wir also verhindern:
	```java 
	PreparedStatement ps = new FBPreparedStatement();
	```
	- Warum?
		- Hard Coding Produkt Typen wie oben, machen es unmöglich ein Unterschiedliches Database-Format beim start auszuwählen
		- Offline veränderungen sind auch schwer, weil man einfach einen konstruktor verfehlen kann und mit einem falschen Objekt endet
	- Lösung: Abstract Factory

**Struktur:**![[Bildschirm­foto 2023-02-23 um 19.32.41.png]]
ACHTUNG: DOZIERENDE ZU FAUL UM CREATE VERBINDUNG VON CONCRETEFACTORY2 ZU PRODUCTA2 UND PRODUCTB2 EINZUZEICHNEN
- AbstractFactory
	- Liefert ein Interface für das Erschaffen von Produkten einer Familie
- ConcreteFactory
	- Implementiert operationen um konkrete Produkte zu erschaffen
- AbstractProduct
	- Deklariert interfaces für konkrete Produkte
- ConcreteProduct 
	- Liefert eine Implementierung für das Produkt, welche von der korrespondierenden concreteFactory erschaffen wurde
- Client
	- Erschafft Produkte durch den Aufruf von ConcreteFactory, indem er das AbstractProduct interface verwendet

**Konsequenzen:**
- Vorteile
	- Abstrahiert weg von konkreten Produkten
		- Klienten können unwissend über konokrete Produkte, welche sie benutzen, sein, sogar zur Erschaffung
	- Verändern von Produkt Familien ist einfach
		- Das Verändern einer einzigen Zeile Code kann das Verhalten der ganzen Klasse verändern
	- Sichert konsistenz zwischen Produkten
		- Familienauswahl begrenzt sich auf eine Zeile, sodass man nicht einfach ausversehen irgendwelche Produkttypen vermischen kann
- Nachteile
	- Unvorhergesehene Arten von Produkten hinzuzufügen ist schwer
		- Beinhaltet das verändern der abstract Factory und aller Subklassen
	- Erschaffen von Objekten folgt einem nicht-standard pattern
		- Klienten müssen eher wissen wie sie factory verwenden als wie sie constructor verwenden

**Zusammenfassung:**
+:
- Anwendungscode kann unwissend über die verschiedenen konrekte Produkte sein
- Eine variierende Zeile code reicht aus um verschiedene Arten von Produkten zu unterstützen
- Man kann verschiedene Produkte beim Start auswählen
- Erzwing das Erschaffen von konsistenten Produktfamilien
	- Beugt beispielsweise vor, dass MySqlBlob mit einer DB2 Datenbank verwendet wird
- 
-: 
- Code muss einer neuen convention für das erschaffen neue Produkte einer Familie (anstatt den standard Konstruktor zu benutzen)