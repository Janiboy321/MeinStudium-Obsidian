#vorlesung1
### Was sind Anforderungen?
> Defintion: Anforderungen sind beschreibungen der Leistungen und operationellen Bedingungen, welche das System zu leisten hat

- Anforderungen werden in Pflichtenheften als User Stories, strukturierte natürliche Sprache, Use Cases, Zustandsdiagramme, usw. niedergeschireben und werden in der Produkt Backlog gespeichert
- Anforderungen sind noch keine Lösungen

### Arten von Anforderungstypen
##### User Anforderungen
	- Meistens in natürlicher Sprache gegeben
		- Welche Leistungen werden vom System erwartet?
		- Welche operationellen Bedingungen gibt es?
	- Meistens high-level und abstrakte Beschreibungen
>Beispiel: Das Buchungssystem muss die Buchungen beibehalten, sowie das deutsche Gesetz es verlangt 

##### System Anforderungen
- Präzise und Detaillierte spezifizierungen von Funktionen, Leistungen
- Operationelle Bedingungen welchen das System unterliegt
>Beispiel: Buchungsdetaills müssen 10 Jahre lang vom System gespeichert werden

- Systemanforderungen sind
	- verfeinerungen von Useranforderungen
	- bestimmen das Systeminterface (funktionale, keine Technischen interfaces)
	- als ein Teil der Systemanforderungsdokumente und des Vertrags aufgezeichnet
	- in zusammenarbeit von Entwicklern und Kunden bestimmt

##### Funktionale Anforderungen
- Funktionalität die klar identifizierbar im Code implementiert ist
- Funktionale Anforderungen spezifizieren
	- Services welche vom System geleistet werden
		- z.B. Authentifizierung, Bestätigungsmail, usw.
	- Reaktionen des Systems auf bestimmte Inputs bzw. Events
		- z.B. Fehlermeldungen, wenn Rückgabedatum vor Abholdatum ist
	- Verhalten des Systems in bestimmten Situationen
		- z.B. Netzwerkabbruch wärend eines Buchungsprozesses

##### Nicht-funktionale Anforderungen
- Bedingungen für die Services bzw. Funktionen welche das System leistet, z.B.:
	- Zeitliche Bedingungen
	- Bdeingungen für den Entwicklungsprozess
	- Standards
- Um diese Anforderungen du erfüllen reicht es meistens nicht einfach "einen Stück Code" hinzuzufügen oder sie können nicht vom System allein garantiert werden
>z.B. "User Daten dürfen nur von authorisierten Personen eingesehen werden"

**Nicht-funktionale Anforderungstypen**
- Produktanforderungen
	- Portabilität
	- Zuverlässlichkeit
	- Effizienz
	- Nutzerfreundlichkeit
- organisatorische Anforderungen
	- Auslieferung
	- Implementierung
	- Standardisierung
- Externe Anforderungen
	- Ethische Anforderungen
	- Legislative (Sicherheit, Privatsphäre)

**Funktionale vs. nicht-Funktionale Anforderungen**
- Nicht-funktionale Anforderungen
	- können bei der identifiezierung von funktionalen Anforderungen dienen
	- sind meistens auftragskritischer als funktionale Anforderungen
		- Ein Buchungssystem welches keine Bestätigungsmails verschickt kann verwendet werden, ein System mit Sicherheitslücken ist nutzlos

**Sicherstellung der Überprüfbarkeit von nicht-funktionalen Anforderungen**
> Wie Überprüft man ob nicht-funktionale Anforderungen erfüllt sind?

*Beispiel: "Das User-Interface sollte einfach zu benutzen sein"*
- Wie misst man "einfach"?
- Einfach für wen?
	- Experten
	- Durchschnittliche User
	- Personen, welche beispielsweise unter einer Sehschwäche leiden?
- Lösung: Formulierung konkretisieren
	- "Mitarbeiter sollten nach einem Schulungstag dazu in der Lage sein, bei Buchungen zu assistieren und den Auto-Pool zu Managen"
	- "Ein durchschnittlicher End user sollte dazu in der Lage sein, eine Buchung in weniger als x Minuten abzuschließen"
	- "Das User Interface sollte Skalierbare Schriftarten und Beschreibende Texte beinhalten"

##### Domain Anforderungen
- Werden eher von Anwendungsdomänen als von den Bedürfnissen der User abgeleitet
	- Sie werden in einer Domain-Spezifischen Sprache ausgedrückt und sind für Software Engineers schwer zu verstehen
	- Meistens Implizit angenommen, weil offensichtlich für Domain Experten
	- Funktional oder nicht-Funktional
> Beispiel: Car-Sharing Firmen müssen überprüfen ob bei neuen Kunden eine Fahrerlaubnis vorliegt

##### Anforderungs Engineerings Prozess
- Anforderungs Engineering ist der Prozess, in welchem die Anforderungen
	- erschlossen werden
	- analysiert werden
	- dokumentiert werden 
	- validiert werden
- Außerdem wird hier das Systemanforderungsdokument erstellt und gewartet

**Enginnering Prozess-Flow**
![[Bildschirm­foto 2023-02-16 um 15.10.54.png]]
1. Feasibility Study (Durchführbarkeitsstudie)
	- Ziel: Gerechtfertigte Empfehlung ob das Anforderungs Engineering und der System Entwicklungs Prozess gestartet werden soll, basierend auf:
		- Vorläufigen business Anforderungen
		- Skizze des Systems
		- Beschreibung, wie das System den business Prozess unterstützen soll
	- Feasibility Report:
		- Trägt das System zur Zielführung der Organisation bei?
		- Kann das System mithilfe aktueller Technologie und mit den gegebenen Kost- und Zeitplänen entwickelt werden?
		- Kann das System in andere Systeme, welche die Organisation benutzt, integriert werden

1. **Anforderungen bestimmen und analysieren**
- Viewpoint orientierte Ansätze
	- Generische Typen von viewpoints
		- Interactor Viewpoint
			- Personen bzw. Maschinen die direkt mit der System interagieren
		- Indirekte Viewpoints
			- Stakeholder, welche die Systemanforderungen beeinflussen, aber nicht direkt mit dem System interagieren (z.B. CFO (finances))
		- Domain Viewpoints
			- Domain Charakteristiken und Bedingungen welche die Systemanforderungen beeinflussen (z.B. Gesetzliche Regelungen für Buchungsdetails und Aufbewahrungsdauer)
	- Entwickelt spezifischere viewpoint wärend Anforderungsbestimmung
	- Nutzt die wichtigsten Viewpoints um Anforderungen zu bestimmen
- **Interview Orientierter Ansatz**
	- Feste Inteviews
		- Vordefenierte Fragen
	- Offene Interviews
		- Keine Vordefinierte Agenda
	- Probleme:
		- Interview sollten nur ergänzend genutzt werden
			- Möglicherweise kooperiert der Interviewte nicht richtig (Möglicherweise angst, seinen Job zu verlieren)
			- Interviewter nutzt Domainwissen, bzw geht davon aus, dass der Interviewer sich in der Domain auskennt, obwohl er es garnicht tut
- Andere Ansätze
	- Use Cases
	- Scanarien 

2. **Requirements Classification and Organization**
- Gegeben: Unstrukturierte Sammlung von Anforderungen
- Ziel: Anforderungen gruppiert und organisiert in kohärente Cluster
- Mögliches Model für das Kategorisieren: FURPS+
	- **F**unctional
	- **U**sability
	- **R**eliability
	- **P**erfomance
	- **S**upportability
	+
	- Implementierung
	- Interface
	- Operationen
	- Packaging 
	- Gesetzlich

3. **Requirements Prioritization and Negotiation*
- Priorisierung und Verhandlung
	- Anforderungen sind Priorisiert
	- Konflikte werden gefunden und in Verhandlungen gelöst

4. **Requirements Documentation**
- Anforderungen sind Dokumentiert und werden als Input für die nächste Iteration genutzt
- Die produzierten Dokumente können formell oder unformell sein

**Software Requirements Specifications Document**
- Zielgruppe
	- Diverse Mengen von Usern
		- System Kunden
		- Manager
		- System Engineers, Systemtests- und Wartungs Engineers
- Level of Details abhängig von
	- Typ des Systems
	- Genutzte Entwicklungsprozesse
	- Wo das System entwickelt wird (Extern oder Intern)
- Struktur:
	1. Einführung
		1. Grund des Dokuments
		2. Scope des Produkts
			- Kann auch enthalten was nicht im Scope liegt
		3. Definitionen, Acronyme, Abkürzungen
			- Glossar um mehrdeutige Begriffe zu erklären
		4. Referenzen
		5. Überblick
	2. Allgemeine Beschreibung
		1. Produkt Perspektieve
		2. Produkt Funktionen
		3. User Charakteristiken
		4. Beschränkungen/Bedingungen
		5. Annahmen und Abhängigkeiten
	3. Spezielle Anforderungen
	4. Anhänge, Index, etc.

##### Anforderungsprüfung
- Validität
	- Erfassen die Anforderungen die benötigten Features?
	- Werden zusätliche oder andere Funktionen benötigt?
- Konsistenz
	- Überprüfen, dass die Anforderungen nicht im Konflikt zueinander stehen
- Vollständigkeit
	- Definieren die Anforderungen alle Funktionen und Beschränkungen, wie vom System User definiert?
- Realismus
	- Können die Anforderungen vernünftig implementiert werden?
- Verfizierbarkeit
	- Ist es möglich einen Test zu entwickeln, ob eine Anforderug erfüllt ist?
- Rückverfolgbarkeit
	- Ist jede Anforderung bis zu ihrer Quelle rückverfolgbar?
	- (Von wo stammt die Anforderung?)