## Einleitung
> Für was benötigen wir einen Software Enginnering Prozess?

- Größe der Aufgabe
	- Man muss ein potentiell großes Team Organisieren
		- Aufgaben zuteilen
		- Formen der Zusammenarbeit definieren
- Komplexität einer Aufgabe
	- Viele verschiedene Typen von Aktivitäten
		- Abhängigkeiten unter Tasks - Wann macht man was?
- Qualitätskontrolle
	- Man muss dazu in der Lage sein, zu Bestimmen ob etwas funktioniert oder nicht

### Fundamentale Prozessaktivitäten:
- Software spezifizierung
	- Definierung der zu produzierenden Software und die Beschränkungen ihrer Operationen
- Software Developement
	- Design, Implementierung und Verifikation der Software
- Software Validierung
	- Sicherstellen, dass die Software wie in den Anforderungen spezifiziert funktioniert
- Software Evolution
	- Adaption und Modifikation der Software um mit wechselnden Kunden und Marktanforderungen klar zu kommen

### Software Engineering Prozess Modelle
**Beispiele für SOftware Engineering Prozess Modelle:**
- Wasserfallmodell
- Spiral Model
- V-Modell (XT)
- eXtreme Programming

#### Wasserfallmodell
1. Anforderungsanalyse und Definition
	- Anforderungen werden in zusammenarbeit mit den System Usern eingeführt
2. System- und Softwaredesign
	- Definition der allgmeinen Softwarearchitektur
	- Identifizieren von fundamentalen Abstraktionen und ihrer Relationen
3. Implementierung und Unittests
	- Das Softwaredesign wird als eine Menge von Programmunits realisiert
	- Testen verifiziert, dass jede Unit ihre Spezifikationen trifft
4. Integrierung und System Testen
	- Programmunits werden integriert und als das komplette System getestet
5. Operation und Wartung

Fakten:
- Das Ergebniss jeder Phase ist eine Menge von erwiesenen Artefakten
- Die Folgephase beginnt sobald die akutelle Phase vorbei ist (In der Praxis könnte es überlappungen geben)
- Gibt es Fehler, müssen die vorherigen Prozessschritte wiederholt werden
- Reiht sich bei den traditionellen (physischen) Entwicklungsprozessen ein

Kritik:
- Es ist kein iterariver Prozess, heißt frühes Prototyping ist unmöglich
- Veränderung von Anforderungen, Designt, etc. schwer
- Das Testen startet erst in den späteren Phasen
- Unterschiedliche Phasen werden durch unterschiedliche Teams durchgeführt

#### V-Modell
![[Bildschirm­foto 2023-02-26 um 15.33.33.png]]

Unterschied zu Wasserfallmodell:
- Direkt zu Beginn, also nach der Anforderungsanalyse werden Tests entwickelt

Kritik:
- Kein Iterativer Prozess
- Veränderung der Anforderungen teuer

Nur verwenden wenn:
- Produktanforderungen stabil und gut verstanden
- Kurze und kleine Projekte
- Strenge Dokumentation wird benötigt

## Agiles Entwickeln
Ziel: Software schnell, überschattet von rapide ändernder Anforderungen entwickeln

Schlüsselerkenntniss:
- Ändernde Anforderungen während der Entwicklung sind Problematisch
- Trozdem treten häufig Änderungen der Anforderungen auf
$\Rightarrow$ Entwicklungsdurchläufe klein und schnell halten: "agil"

Agile Prozessanforderungen:
- Analysierende, Kunden, Entwickler, Tester, usw. arbeiten zusammen als ein Team (Bedeutet, dass alle Mitglieder immer erreichbar sein müssen)
- Arbeitspraxen, welche eine erforderliche Disziplin und erforderliches Feedback liefern
- Arbeitsdesignprinzipien welche die Software flexible und wartbar halten

Manifest für das agile Entwickeln von Software
1. Individuen und  ihre Interaktionen untereinander stehen über dem Prozess und Werkzeugen
	- Das beste Werkzeug hilft nichts, wenn das Team nicht zusammen arbeitet
	- Wichtig:
		- Team startet klein und wächst/schrumpft je nach anforderung durch das Projekt
		- Regelmäßige refkletion - z.B. regelmäßige Meetings
		- Nachhaltige Arbeit - Burn Outs durch übermäßige Arbeit vermeiden
2. Systemstrukturen und Begründungen für das Design müssen Dokumentiert werden
3. Zusammenarbeit mit Auftraggebenden steht über der Vertragsverhandlung
	- Der Vertrag sollte spezifizieren, wie die Zusammenarbeit zwischen dem Entwicklungsteam und dem Kunden aussehen soll
	- Ein Vertrag welcher ein fixxes Gehalt zu einem fixxen Datum soezifiziert wird warscheinlich scheitern
4. Auf Veränderungen reagieren indem man einen Plan verfolgt
	- Möglichst kleine Iterationen
	- Wichtiger auf Änderungen schnell zu reagieren als einem festen Zeitplan zu folgen
	- Nur grobe Zeitpläne erstellen

Welche Agile Prozesse gibt es:
- Extreme Programming
- SCRUM
- Agile Unified Process
- Crystal Feature Driven Development
- Adaptive Software Development
- ...

## Extreme Programming
**Kunde**:
- Die Person (oder Gruppe) welche Features definiert und priorisiert
- Ein Mitglied eines Teams und erreichbar für das Team

**User Story**:
- Anforderungen werden in Diskussion mit Kunden identifiziert
- Kurzer Text mit einer Einschätzung der relativen Schwierigkeit
- Beschreibung kurz und präzise halten
- Technische Detaills können sich trozdem noch verändern

Gute User Stories:
- Die Story muss verständlich für den Kunden sein
- Jede Story muss dem Kunden einen gewissen Wert bringen
- Stories müssen so Aufgeteilt sein, dass man pro Iteration mehrere implementieren kann
- Stories sollten unabhängig sein
- Jede Story muss Testbar sein

Templates:
- Lang
	- "Als [Rolle] ist mein Ziel [Ziel] sodass [Nutzen]"
- Kurz 
	- Als [Rolle] ist mein Ziel [Ziel]

Gute User Stories (INVEST):
- Independent
	- Eigenständig
	- keine mitinbegriffenden Abängigkeiten zu einer anderen Story
- Nagotiable
	- User Story kann bis zu einem Sprint immer verändert und umgeschrieben werden
- Valuable
	- Muss dem Endnutzer einen gewissen Wert bringen
- Estimable
	- Es muss möglich sein die größe der Story zu Schätzen
- Sized appropriately (Small)
	- Nicht zu groß, sodass es unmöglich ist mit Gewissheit zu planen / priorisieren
 - Testable
	- Nötige Informationen, um das Entwickeln von Tests möglich zu machen, müssen geliefert werden

**Acceptance Test:**
- Details der User Story werden als eine Form von acceptance tests festgehalten
- Acceptance Tests werden vor oder während der Implementation einer User Story geschrieben
- Sobald ein acceptance test bestanden ist, wird er zu Menge der bestandenen acceptance tests hinzugefügt und darf nie wieder failen (Regression verhindern)

**Kurze Entwicklungszyklen:**
- Eine _Iteration_ (oder _Sprint_) ist ein fix definierter Zeitraum in welchem eine Menge von Softwarefeatures implementiert wird
- Nach jeder Iteration muss ein Stück ausführbaren Software existieren, welches getestet werden kann (Dieses Stück muss nicht unbedingt im finalen Produkt eingesetzt werden)
- Iterationen sind Zeitlich