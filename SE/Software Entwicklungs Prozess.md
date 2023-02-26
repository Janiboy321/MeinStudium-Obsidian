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
- 