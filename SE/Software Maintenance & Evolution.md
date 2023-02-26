> Wie jedes andere komplexe technische Artefakt, ist Software sogut wie nie fertig und muss konstant gewartet werden

### Trigger von Sofware-Wartungs Aktionen
1. Bug fixes
	- Häufigster Grund für Softwarewartung
	- Gutes Testen nötig um Rücktritt zu vermeiden
	- Es ist Ratsam mehrere Bugs mit einem mal zu Fixen
		- Häufige Updates nerven nutzer
		- Eine neue Softwareversion auszuliefern kann sehr teuer sein
		- Stelle Changelogs bereit
	- Nutze ein Ticketingsystem um fixes zu priorisieren und zuzuweisen
		- Somit kann man nachverfolgen, wer an welchen Bugs schuld ist
2. Veränderte Anforderungen
	- Während der Entwicklung meistens der Todeskuss
	- In vielen Fällen unvermeidbar
		- Veränderte Gesetze
		- Veränderter Gesamtprozess, NUtzungsmodalitäten
	- Performanceanforderungen
		- Wachsende Nutzeranzahl und Menge an Daten
	- Neue Anforderungen sind oftmals getarnte neue Features - Differenziere!
		- Braucht man neue Funktionalitäten wirklich, lohnen sie sich?
		- Muss die vorherige Version noch gewartet werden?
3. Neues feature request
	- Je Erfolgreicher eine Software ist, desto wahrscheinlicher sind feature requests
	- Features werden durch innovation getrieben
	- Features könnten auch durch neue Kunden getrieben werden
	- Kann zu verschiedenen Versionen der Software führen, welche trozdem beide gewartet werden müssen
4. Sich entwickelnde Hardware
	- Mehr Kerne ermöglichen parallelisierung
	- Neue Hardwarearchitekturen x86 $\Rightarrow$ ARM
	- Peripherie (Displays, Speicher, Authentifikationsgeräte)
5. Sich entwickelnde Software Architecture
	- Software auf einer Plattform anbieten (SaaS)
	- Plattform auf einer Maschine anbieten (PaaS)
	- Maschine anbieten (laaS)
	- Cloud Services, laaS, PaaS, SaaS
		- Vorteile
			- Kostengünstig, mobil, Skalierbar
		- Nachteile
			- Mangelnde Privatsphäre
			- Granularität der Interfaces
			- Höhere Latenz
			- Abhängigkeit
			- Benötigt Virtualisierung
	- Virtualisierung
		- Vorteile
			- Plattform unabhängig
			- Ermöglicher von Cloud-Services
		- Nachteile
			- Performance overhead
			- Nicht alles ist virtualisierbar
			- Man hat initiale Kosten
1. Sich entwickelnde Software Stacks
	- Software Libraries?
		- Bibliotheken, welche nicht von der API der Programmiersprache angeboten werden
	- Eigene Bibliotheken schreiben oder auf externe Anbieter verlassen?
		- Biliotheken müsse auch gewartet werden
		- Ohne gute Dokumentation sind Bibliotheken sinnlos
		- Eigene bibliotheken könnten die mobilität und virtualisierung behindern
		- Mängel in der eigenen Bibliothek kann ernsthafte Probleme verursachen
			- Beispielsweise könnten Security-Fehler die Angriffsfläche vergrößern
		- Entwicklung einer eigenen Bibliothek ist gerechtfertigt, wenn
			- sie Zentrale Teile des Produktes beinhalten
			- sie business-kritische Abhängigkeiten von einem Anbieter schaffen
	- Programmiersprachen
		- Sind meistens Rückwärtskompatibel
		- alte Versionen werden aber nicht für immer unterstützt
	- Datenbanktechnologien
		- Extern $\Rightarrow$ In-Memory
		- Businesslogik in Datenbanken verschieben um an Performance dazuzugewinnen

#### Parallelisierung als Wartungsaufgabe
- Multiprozessor/-core Systeme sind heutzutage weit verbreitet
- Es ist ein signifikanter Speed-up möglich, aber die bereits existierende Altsoftware sind meisten sequentiell
- Deshalb ist parllelisierung ein wichtiges Teil der Wartungsaufgaben geworden und kann als komplexes refactoring betrachtet werden

### Pipeline Parallelization Pattern
Die Problem Domain kann in unterschiedliche Tasks eingeteilt werden, welche regulär, in einer Reihenfolge oder Synchron durchgeführt werden können
**Forces:**
- Stabil und synchrone Reihenfolge (Berechnungen sind nicht Rückgangig machbar)
- Spezifische Aufgaben kann man auf spezielle Software verteilen
- Erlaubt das einfache modifizieren, hinzufügen und umordnen von Aufgaben
- Kann nicht dazu benutzt werden um fehlerhafte Inputs zu entschärfen
**Lösung:**
- Teile die Berechnung in Teile auf welche auf verschiedenen Datenelementen arbeiten
	- Jede Loop durchgeht 3 Phasen:
		1. Empfangen von Daten der vorherigen Stage
		2. Daten verarbeiten
		3. Ergebnisse an die nächste Stage weiterleiten und dann mit

### Software Evolution
> Komplexe, wiederholte Wartungsaktionen bilden die Software Evolution

**Definition:** Die Serie von Veränderungen, neuen Versionen, anpassungen welche während der Softwarewartung vom Start und initialen Bereitstellung bishin zum finalen Ruhestand

### Kritische Probleme in der Software Entwicklug
- "Verschlimmbesserung" - Existierende Funktionalitäten zerstören
	- Verhinderbar durch gründliches Regression Testing
	- Man könnte auch Beta Versionen für erfahrene User veröffentlichen
- Verbindung zwischen Spezifikation, Dokumentation und Implementierung vernichten
	- "Undokumentierter Code von Jemandem der vor 10 Jahren die Firma verlassen hat, verändert sich"
	- Veränderte Anforderungen und neue Features müssen einen vollen Entwicklungszyklus initiiren
- 