#vorlesung2

## Use Code Analyse

#### Anforderungen vs. Use Cases
- Anforderungen
	- fokusieren sich auf die gewünschten Funktionen und operationellen Beschränkungen
	- sind oft deklarativ 
	- Perspektive der Auftraggebenden
- Use Cases
	- identiefizieren vorraussichtliche interaktions Sequenzen
	- sind statisch einsetzfähig
	- Perspektive der Anwendenden

#### Use Cases: Aufwand der Client Seite
> Es ist unmöglich gute bzw. komplette Use Cases, ohne Mitarbeit der Nutzer

#### Use Cases
- Use Cases sind stories, welche benutzt werden, um Anforderungen zu bestimmen und aufzunehmen
- Use Cases ergänzen die Anforderungsanalyse

#### Defintionen von Bestandteilen von Use Cases
- Actor 
	- Jemand oder Etwas mit einem Verhalten
		- Eine Person, ein Computer System, etc.
- Primary actor
	- Der Actor der ein Service des Systems anfordert (initiiert den Use Case)
- Scenario (Use Case instance)
	- Eine bestimmte Reihenfolge an Aktionen und Interaktionen zwischen Actors und dem System
- Use Case
	- Eine Sammlung von verwandten Erfolgs und Fehlszenarien, welche das Verhalten eines Actors und die interaktion mit dem System mit einem Ziel beschreiben

#### Verschiedene Arten von Use Cases
- White box vs. black box
	- White box
		- Use Cases geben eine detaillierte einsicht in die Interaktion von Interna dabei ein Ziel zu erreichen
	- Black box
		- Use Cases "ignorieren" das System und Beschreiben die Interaktion durch externe Actors
- Corporate vs. System
	- Corporate 
		- Use Cases beschreiben einen business Prozess (Oft ohne das System zu erwähnen)
	- System
		- Use Cases werden in beachtung des Systems geschrieben und ausgeführt

#### Use Cases Format
- Brief
	- Kurze, ein Paragraph Zusammenfassung, normalerweise das Main Success Scenario
- Casual
	- Informales Paragraphen Format
	- Verschiedene Paragraphen, welche verschiedene Szenarien abdecken
- Fully Dressed
	- Alle Schritte und Variationen werden detailliert beschrieben
	- Es gibt unterstützende Sektionen wie Vorbedingungen und Erfolgsgarantien

#### Fully Dressed Use Case

##### Template 
| Use Case Section                       | Grund / Guideline                                                                            |
| -------------------------------------- | -------------------------------------------------------------------------------------------- |
| Use Case Name                          | beginnt mit einem Verb                                                                       |
| Scope("Umfang")                        | Coporate, System (besser: Name), Subsystem                                                   |
| Level                                  | User goal, Summary goal, subfunction                                                         |
| Primary Actor                          | Initiiert den Use Case                                                                       |
| Stakeholder und Interessanten          | Wem ist dieser use Case wichtig? Was wollen sie?                                             |
| Vorbedingungen                         | Was muss am anfang gegeben sein und lohnt sich den Lesenden zu erzählen                      |
| Minimale Garantie                      | Mindeste Garantie die das System gibt                                                        |
| Erfolgs Garantie                       | Was muss nach einer Erfolgreichen ausführung gegeben sein und sollte man dem Leser erzählen? |
| Main Erfolgs Szenario                  | Repräsentatives Szenario einer Erfolgreichen Use Case Ausführung                             |
| Extensions                             | Alternative Szenarios für Erfolge oder Fehler                                                |
| Spezielle Anforderungen                | Varwandte nicht-funktionale Anforderungen                                                    |
| Technologie und Daten Veriations Liste | Wechselnde I/O Methoden und Datenformate                                                     |
| Menge von Aufkommen                    | Beeinflusst Untersuchungen, Tests und Zeitplanung der Implementierung                        |
| Miscellaneous                          | z.B. offene Probleme                                                                         |

#### Guidelines für Entwicklung eines Use Cases
Allgemein: Arbeite inkrementell
1. Ermittle alle relevanten Use Cases akkurat und auf einem hohen Level
2. Präzision schrittweise erhöhen und detaills ausarbeiten

**Empfohlener Workflow**
1. Schreibe alle Actor und ihre Ziele auf
	1. Überprüfe die Liste auf Genauigkeit und Vollständigkeit
2. Schreibe Stakeholder, Trigger und main success Szenario für jeden Use Case, Validiere ob das System das wichtigste für den Stakeholder hergibt
3. Identifizierene und Liste alle Fehler Bedingungen auf
4. Beschreibe verhalten in Fehlsituationen

**Weitere Empfehlungen**
- Use Cases sollten beim frühen Anforderungs Engineering ignoriert werden
- Man sollte Use Cases kurz und bündig schreiben
- Schreiben von Black Box Use Cases:Beschreibe was das System machen muss und nicht wie
- Nehme die Perspektive eines Actors ein
- Fokusiere dich auf die User und Actor des Systems
	- Frage nach ihren Zielen und typischen Situationen
	- Fokussiere dich darauf, zu verstehen,was der Actor als wertvolles Ergebnis wahrnimmt

**Checklist für gute Use Cases**
- Ist der Use Case wohldefiniert?
	- Wird von einem Stakeholder, an einem Ort zu einem Zeitpunkt ausgeführt
	- Modelliert ein business Event
	- Fügt dem System einen messbaren Wert für das Business zu 
	- Hinterlässt die Daten beständig
- Ist es mehr als ein Schritt?

### UML Use Case Diagram
- Notationen auf UML Use Case Diagrammen sind minimalistisch
- UML Use Case Diagramme sind eine organisierte Methode um die Komunikation und das Verstehen von Use Cases zu verbessern und um Textduplikationen zu vermeiden 
- Use Case Diagramme bieten eine Black Box view auf das Software System
- Use Case Diagramme sind gerade am Anfang der Use Case Analyse nützlich

#### Use Case Diagramm: Notationen
- **Include**: Funtionen auf die ein Include zeigt, werden immer ausgeführt, wenn der Ausgangspunkt ausgeführt wird
![[Bildschirm­foto 2023-02-18 um 15.03.45.png]]
- **Extend**: Mithilfe der Extend Beziehung kann man zeigen, unter welcher Bedingung ein bereits existenter Use Case, oder ein zusätzlicher Use Case, das verhalten eines Use Cases erweitert
![[Bildschirm­foto 2023-02-18 um 15.08.43.png]]