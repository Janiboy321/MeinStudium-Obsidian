## Software Qualität

### Wie sichert man die Qualität von Software?
Es muss ein definierter Qualitätssicherungsplan in den Software-Entwicklungsprozess integriert werden:
- Die Qualität der Software muss konstant geprüft werden
- Man muss dazu fähig sein, gut getestete Design-Prinzipien anzuwenden
- Tools und Designprinzipien verwenden, welche dabei helfen Qualität zu erreichen
- Nutze Design-Patterns, um davon zu lernen und Lösungen die sich bewährt haben wieder zu verwenden
- Man sollte die Korrektheit und Performance des Designs systematisch verfizieren
- Man muss die erfüllung der Anforderung regelmäßig überprüfen

### Interne und Externe Qualitätsfaktoren
*Was ist gute Software?*
- Interne Qualitätsfaktoren - Nur von Entwicklern wahrnehmbar
	- White Box sicht eines Systems
- Externe Qualitätsfaktoren - Vom Kunden / User wahrgenommen
	- Black Box sicht eines Systems
	- Hängt von internen Qualitätsfaktoren ab

**Interne Faktoren:**
- Modularität
- Verständlichkeit (Nicht übertrieben Komplex)
- Kohäsion (Klare Verantwortlichkeiten)
- Präzision (Wenig Codedopplungen, klarer Code)
- Korrektheit

**Externe Faktoren:**
- Gültigkeit
	- Ist das System dazu in der Lage wie in den Anforderungen definiert zu arbeiten
		- Eine präzise Anforderungs Definition wird benötigt
		- Gültigkeit hängt vom korrekten Design ab
		- Gültigkeit hängt oft von der richtigkeit der tieferen Schichten ab: compiler, OS, VM, Hardware, etc.
- Robustheit
	- Ist das System dazu in der Lage in unnormalen Situationen gescheid zu reagieren? 
- Erweiterbarkeit
	- Wie einfach kann man die Software auf veränderte Anforderungen anpassen?
		- Kann die Architektur einfach angepasst werden?
		- Loose coupling macht veränderungen einfacher (Schichten Architekturstil ist nicht gut anpassbar)
- Wiederverwendbarkeit
	- Wie gut kann man die Softwareelemente in der konstuktion von anderen Anwendungen wiederverwenden?
- Kompabilität
	- Wie gut kann man Softwareelemente mit anderen Anwendungen vereinen?
		- Kompatibilität für Standards, Protokolle,...
		- Ruckwärtskompatibilität (für sich Selbst)
- Portabilität
	- Wie gut kann man die Software auf andere Hardware und Softwareumgebungen übertragen?
- Effizienz
	- Ist das System dazu in der Lage, Hardware Ressourcen wirtschaftlich zu verwenden?
- Nutzerfreundlichkeit
	- Wie gut können Menschen mit verschiedenen Hintergründen und Qualifikationen lernen, die Software zu benutzen und sie für die Lösung von Problemen anzuwenden?
- Funktionalität (Trifft Erwartungen der User)
	- Wie groß ist der Funktionsumfang der Software?
		- Vermeide unnötig viele Features, achte auf Konsistenz und bringe neue Features in zusammenhang mit bereit bestehenden

### Was sind die Attribute von "gut"?
- Wartbarkeit
	- Software ist so konstruiert, dass sie sich auf ändernde Anforderungen von Usern anpassen kann
- Effizienz
	- Die Software verschwendet keine System Ressourcen
- Nutbarkeit
	- Reaktionsvermögen muss für die Vorgesehenen Nutzer nützlich sein
- Verlässlichkeit
	- Verursacht keinen physischen oder Ökonomischen schaden bei einem Systemfehler

## Quantitive Qualitätsmessung

### Wie misst man Softwarequalität?
> Es gibt keinen generell akzeptierten Weg, Softwarequalität zu messen 
- Es gibt viele Qualitäten in Software, welche oft im Gegensatz zueinander stehen
- Was können wir machen?
	- Es gibt Heuristiken welche Qualität vom Code aufzeigen
	- Dieser werden Software Metrics (Code Metrics) genannt 
		- Vorteile von Software Metrics
			- Sie können mechanisch berechnet werden
			- Sie können schlechte Designs erkennen
		- Nachteile von Software Metrics
			- Keine Notation zu semantiken vom code
			- Sie können keine Coding Fehler aufdecken

### Beispiele für Software Metriken
- Fan in/fan out
	- Fan-in von Methode m = anz von Methodenaufrufen von M
	- Fan-out von Methode m = anz von Methodenaufrufen durch m
- Länge des Codes
	- Länge des Codes (indikator für Komplexität)
- Cyclomatic Complexity
	- Unabhängige Pfade durch den Code (im Controll-Fluss Graphen)
- Tiefe von konditionellen Verschachtellungen
	- Tiefe Verschachtelung ist schwer zu verstehen
- Gewichtung von Methoden pro Klasse
	- Die Gewichtung von Methoden ist abhängig von Größe und Komplexität, Summiert pro Klasse
- Tiefe von Vererbungsbäumen
	- Je tiefer die Vererbungsbäume, desto beschränkter sind Klassen im Design

## Kontroll Fluss Graphen
Sie zeigen alle möglichen Ausführungssequenzen eines Programmes

**Basic Block (node):**
Ein Basic Block ist die Maximale Sequenz ohne Branchen, also von Zeilen, welche entweder immer zusammen oder garnicht ausgeführt werden. Die letzte Zeile kann ein branching sein, weil sie ja trozdem immer zusammen mit dem rest ausgeführt wird.

**Edge:** 
Jede Edge zeigt einen möglichen übergang von einem Basic Block zu einem anderen

**Lable:**
Jede Edge hat ein Label, welches die Bedingung für den Branch beinhaltet.
![[Bildschirm­foto 2023-02-20 um 14.09.55.png]]
Sonstiges:
- Es gibt immer expliziete Initial und Exit nodes
- Manche CFG-Basierte Analysen benötigen ein Diagramm mit einem einzigen Exit Node

### Zyklomatische Komplexität C![[Bildschirm­foto 2023-02-20 um 14.29.26.png]]
- Anzahl von unabhängigen Pfaden
- Benötigt CFG mit einem einzigen exit node
- $C:= AnzEdges - AnzNodes + 2*AnzVerbundeneKomponententen$
- Heuristik: $C > 10 \rightarrow$ Design und Code nochmal überarbeiten 

### Klassen und Interface Coupling
- Coupling zeigt das Ausmaß der Anhängigkeiten zwischen Klassen und Packages
- Definition von Coupling:
	- Eine Klasse oder ein Interface A ist mit einer anderen Klasse oder Interface B coupled, wenn A direkt oder indirekt von B anhängt
- Eine Klasse welche von 2 anderen Klassen abhängt hat ein lockereres Coupling als eine Klasse die von 8 anderen Klassen abhängt
**Coupling in Java:**
Typische Couplings in Java:
- Attribute die vom Typ einer anderen Klasse sind
- (sub-)expressions eines Typs einer anderen Klasse
- Aufrufe von Methoden anderer Klassen
- Subtypen
- Referenzen
- Annotiationen wie @Override
- Die Klasse System (System.out.println)
WICHTIG: In Java ist jede Klasse mit der Klasse java.lang.Object coupled

**Design Prinzip: Vermeide starke oder schwaches Coupling**
- Klassen mit starkem Coupling
	- Veränderungen in einer Klasse müssen in allen gekopptelten Klassen angepasst werden
	- Klassen mit Starkem Coupling sind isoliert schwer zu verstehen
	- Klassen mit Starkem Coupling sind schwer wiederzuverwenden, weil man die anderen Klassen dann auch braucht
	- Klassen mit Starkem Coupling sind sehr unmodular

- Klassen mit schwachem Coupling
	- Lose Kopplung im Übermaß führt dazu, dass aktive Objekte die gesamte Arbeit erledigen

**Verbreitung von Klassen:**
- Unterschied Klasse vs. Rolle
	- Eine Klasse hat eigene Attribute und Operationen
	- Eine Rolle ist ein Objekt einer existierenden Klasse

Wann reicht eine Rolle und wann sollte man eine eigene Klasse erstellen?
- Hat das Objekt ein komplett anderes Verhalten als eine existierende Klasse
	- Beispiel: Reicht für einen Polizisten ein Personen-Objekt oder braucht man eine Polizisten Klasse?

### Code Measure: Cohesion
> Misst das Ausmaß der Beziehung zwischen Elementen einer Klasse
- Alle Operationen und Daten in einer Klasse sollten "natürlicher Weise" zu dem Konzept der Modellierten Klasse gehören

**Typen von Kohäsion:**
Es gibt folgende Gründe, warum Code Elemente gruppiert sein können (Sortiert von unwünschenswert bis wünschenswert):
- Zufällig - Es gibt keine bedeutungsvolle Beziehung zwischen Elementen
- Temporär - Alle Klassenelemente werden "zusammen" Ausgeführt
- Sequentiell - Das Ergebnis einer Methode ist der Input für eine andere
- Kommunikativ - Alle Funktionen/Methoden einer Klasse greifen auf den gleichen Input/Output zu
- Funktional - Alle Klassenelemente dienen einer einzigen, wohldefinierten Aufgabe

**Cohesion Messen mit dem "Lack of Cohesion of Methods (LCOM)":**
1. Zuerst zeichnen wir einen Graphen, wessen Nodes die Methoden einer Klasse sind
2. Dann Zeichnen wir die Relationen als Edges ein.
3. Der LCOM Wert setzt sich nun aus der Anzahl der miteinander unverbundenen Elemente des Graphen zusammen.
4. Je höher der LCOM Wert ist, desto niedriger ist die Cohesion
_Beispiel 1:_![[IMG_6870A9F1322D-1.jpeg]]
_Beispiel 2:_![[IMG_F94107A9A6A8-1.jpeg]]

**Design Prinzip: Vermeide niedrige Cohesion:**
- Klassen mit niedriger Kohäsion sind nicht wünschenswert:
	- Schwer zu verstehen
	- Schwer wiederverwendbar
	- Schwer zu unterhalten
	- Repräsentieren Typischerweise zu feine Abstraktion
	- Übernehmen Aufgaben, welche eigentlich nur deligiert werden sollten

## Verantwortungsbewusstes Design
> Ein Systematischer Ansatz um das Design von Softwareobjekten und Komponenten in hinsicht auf Verantwortungen, Rollen und Kolaborationen 

### Verantwortungen
> Klassen eine gewisse Verantwortung zuzuteilen ist eine zentrale Aktivität bei Code Design Patterns und Idiomen. Design Prinzipien helfen dabie

- Beim Verantwortungsbewussten Designen haben Softwareobjekte eine gewisse verantwortung
- Verantwortungen werden Klassen während der Objekt-Design Phase zugeteilt

**Arten von Verantwortungen:**
Verantwortungen sind in hinsicht auf ihre Rolle im Softwaredesign abhängig von den Verpflichtungen oder dem Verhalten der Objekte

- Es gibt zwei fundamentale Typen von Verantwortungen:
	- Doing - Aktionen auführen:
		- Aktionen ausführen (Berechnungen machen, Objekte erstellen,...)
		- Aktionen von anderen Objekten initiieren
		- Aktionen von anderen Objekten kontrollieren und koordinieren
		- Beispiel: Ein Objekt einer Rechnung ist für die Berechnung ihrer eigene Summe zuständig
	- Knowing - Kennen und bereitstellen von Informationen an andere Objekte:
		- Kennen von privaten, eingekapselten Informationen
		- Angehörige Objekte kennen 
		- Beispiel: Ein Auto hat die Verantwortung, die zurückgelegte Distanz zu kennen

**Beziehung von Verantwortungen und Methoden:**
Bei der Implementierung von Verantwortungen, müssen Methoden alleine agieren oder mit anderen Methoden (auch von anderen Objekten) zusammen

> Eine Verantwortung ist nicht das gleiche wie eine Methode

Beispiel:
- Zugang zu einer Datenbank zu gewähren kann duzende Klassen benötigen
- Eine Rechnung zu Drucken, kann eine einzige oder ein paar Methoden benötigen

**Verantwortung auf mehrere Objekte verteilen:**
Wie ermittelt man die Zuteilung von Verantwortungen auf mehrere Objekte?
- Es gibt unzählige Entscheidungen beim verteilen von Verantwortungen
	- "gute" vs. "schlechte" Designs
	- "schöne" vs. "hässliche" Designs
	- "effiziente" vs. "ineffiziente" Designs
> Schlechte Entscheidungen führen zu fragilen Systemen, welche schlechter zu warten, verstehen, erweitern oder wiederverzuwenden sind  

## Design Prinzipien

**Single Responisibilty Prinzip:**
Da Verantwortungen die primären Gründe für Veränderungen sind, ist das Ideal eine Verantwortung pro Klasse

Beispiel Rectangle:
![[IMG_9E79931BC555-1.jpeg]]
_Folgt die Klasse Rectangle dem Single Responsibility Prinzip?_
Nein , die Klasse hat mehrere Verantwortungen:
- Berechung der größe des Vierecks: Mathematisches Model
- Rendern des Viereckes auf dem Bildschirm: GUI-Funktion 

_Ist das in diesem Fall problematisch?_
- Die Wiederverwendung von Rectangle wir durch die Abhängigkeit von dem GUI Package erschwert, da diese auch verwendet werden müssen
- Jede Änderung in der Graphical App, die eine Veränderung von Rectangle verursacht, erfordert ein erneutes Testen und Einführen im Kontext der Geometry App

_Wie kann man das Produkt Refactorn, um das SRP zu erfüllen?_![[IMG_46A0BC60F60B-1.jpeg]]
Lösung: Man trennt die Funktionalitäten für das Zeichnen und der Geometrischen berechnung

**Kollaboration mehrerer Klassen:**
Selbst wenn das SRP realisiert ist, ist nicht immer klar, wo man Verantwortungen einteilt
Also Designt man eine policy, welche eine kollaboration mehrerer Klassen erfordert:![[IMG_1954BADD5948-1.jpeg]]
- Vehicle
	- Statische Informationen über Fahrzeuge: Nummernschilder, Fahrzeugklasse, letzter Service,...
- Customer
	- Statische Informationen über Kunden: KundenID, Name, Adresse,...
- BookingProcessor
	- Statische Informationen über eine angeforderte Buchung: Welches Fahrzeug, Buchungsdauer, Wer hat die Buchung getätigt,...

### Delegation vs. Erbung
![[IMG_49B22FF1D721-1.jpeg]]
- Der Code für die Authentifizierung sollte nicht in Customer kopiert werden
- Es gibt zwei Optionen:
	- Code von Authetification erben
		- Unnatürliche veerbungsrelation, verstößt gegegen SRP
		- Unterklassen von Customer sind dazu gezwungen den Code ebenfalls zu Erben
		- Nicht benötigte Funktionalitäten von Authentification werden ebenfalls geerbt
		- Große Vererbungsbäume sind schwer zu unterhalten/warten
	- Code von Authetification deligieren
		- Man erhält ein Objekt von Authentification, mit geeigneter Funktionalität
		- Man benutzt das Objekt um die Authetification zu delegieren
		- Man nutzt nur Funktionalitäten, welche auch wirklich benötigt werden
		- Vererbungshirarchie wird nicht verändert

Wann sollte man Delegation und wann Vererbung wählen?
- Vererbung
	- Vererbung muss bereits existierende Funktionalitäten organisch erweitern
- Delegation
	- Ansonsten wird delegation preferiert
		- Ist weniger aufdringlich im Gesammtdesign, mehr Fokussiert
		- Delegation kann während der Laufzeit verändert und abgebrochen werden

## Encapsulation

### Programmieren auf Interfaces
- Interface Konzept
	- Ein Interface deklariert die signatur der Methoden und öffentliche Konstanten von der implementierenden Klasse
		- Das Interface bietet unabhängigkeit von Funktionalitäten der Implementation
- Also: Man sollte immer für Interfaces Programmieren
	- Felder, Typen und Methodenparameter mit Interface-Typ deklarieren
	- Keine Details der Implementierung in public Methoden Preisgeben

**Vorteile von der Nutzung von Interfaces:**
- Hilft dabei, ungerechtfertigte Annahmen über die Implementierung zu vermeiden
- Interfaces sind stabiler als ihre Implementierungen
- Um Implementierungen zu verändern, reicht es den Konstruktor Auszutauschen
	- Man kann implementations unabhängigen Code in Abstrakte klassen ausfaktorisieren
	- Man kann Coupling reduzieren

### Zugriff auf Felder
Design Prinzip: Instanzfelder von Klassen sollten niemals Public sein
- Bricht Prinzip des versteckens von Informationen
	- Keine Unterscheidungen zwischen Implementationsspezifischen und öffentlichen Daten
	- Implementationsspezifische Details werden den Klienten exposed
- Fragiler Code, wenn Feld Implementierungen sich ändern
- Bei Feldern welche als Argumente oder Aliasse weitergegeben werden ist es schwer den Überblick über Abhängigkeiten beizubehalten
- 
### Beispiel für Einkapselung:![[IMG_09A8BD5E4AC2-1.jpeg]]
Problem: In dieser Implementierung werden die Namend er Felder verändert, was in anderen Klassen des gleichen Packages dafür sorgt, dass die Implementierung nicht mehr Funktioniert
**Lösung:**
![[IMG_3C1A5C87BD63-1.jpeg]]
Anstatt die Namen zu verändern, implementieren wir eine Methode, welche uns den Vektor unabhängig vom Namen zurück gibt

### Accessor Methoden:
Es gibt gute Gründe, die für die Nutzung von Accessormethoden sprechen:
- Verantwortung für Askepte des User Interfaces
- Klassen, welche accessors benutzen implementieren eine policy
- Klasse ist ein statische Container ohne Verhalten

## Design Wisse Anwenden: Das Gott-Klassen Problem
- Gott Klassen
	- Sie beinhalten den größten Teil der Systemlogik
		- Schlechte Verteilung der Verantwortungen
		- Kein Objekt-Orientiertes Design

**Wie erkennt und vermeidet man Gottklassen?**
- Klassen mit unklarer Verantwortung
	- Klasse welche SRP nicht erfüllen
	- Erforderte Aktion: Klasse aufteilen und Verantwortungen neu verteilen
- Klassen mit niedriger Kohäsion, Klassen die nicht Kommunizieren
	- Klassen mit Methoden, welche auf einer kleinen Teilmenge ihrer Felder operieren
	- Erforderte Aktion: Klasse aufteilen und Verantwortungen neu verteilen
- Nutzen Klassen mit public Feld Accessor
	- Kan daruf hinweisen, dass Verantwortungen in den Falschen Klassen lokalisiert sind
	- Erforderte Aktion: Interface neu Designen und Verantwortungen neu verteilen

Um Gottklassen zu vermeiden ist es ratsam zu versuchen die Reale Welt nachzuprogrammierern, dabei sind die anderen Prinzipien aber wichtiger:
In der Realen Welt berechnet ein Auto nicht sein eigenes nächstes Service Intervall
In einem Car Sharing System ist es aber denkbar diese Verantwortung auf die dazu passende Klasse zu verteilen

## Zusammenfassung
- Vermeide hohes Coupling von Klassen
- Vermeide niedriges Coupling von Klassen
- Neue Klassen sollten immer mit dem Hintergrund eines neuen Verhaltens implementiert werden - berücksichtige Rollen
- Vermeide eine niedrige Kohäsion pro Klasse
- Nutze vererbung Vorsichtig - berücksichtige Delegation
- Vermeide zu viele Klassen
- Programmiere für Interfaces
- Mach Instanzfelder niemal public, biete accessors an, wenn benötigt
- Verstecke interne Felder und biete nur accessors, welche wirklich benötigt werden für die Funktionalität
- Verteile Funktionen gleichmäßig und vermeide Gottklassen

