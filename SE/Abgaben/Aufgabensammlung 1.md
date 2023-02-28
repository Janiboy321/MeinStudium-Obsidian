### Aufgabe 1
| Stakeholder                    | Art der Interessen | Interesse                                                                                   |
| ------------------------------ | ------------------ | ------------------------------------------------------------------------------------------- |
| Studierende                    | Direkt             | - Zu Kursen und Prüfungen anmelden                                                          |
|                                |                    | - Anmeldungen verwalten                                                                     |
|                                |                    | - Zugriff auf in Kursen veröffentlichten Lernmaterialien                                    |
| Dozent_innen                   | Direkt             | - Lernmaterialien hochladen                                                                 |
|                                |                    | - Prüfunsergebnisse für Studierende eintragen                                               |
|                                |                    | - Allen/Einzelnen Studierenden ihrer Kurse Nachrichten schicken                             |
|                                |                    | - Kompatibilität für Software von Drittanbietern durch flexible Schnittstellen              |
| Mitarbeitende der Prüfunsbüros | Direkt             | - Zugriff auf alle Kurse der Fachbereicher für die sie Zuständig sind                       |
|                                |                    | - Prüfunsergebnisse effizient einsehen                                                      |
|                                |                    | - Leistungsspiegel erstellen                                                                |
|                                |                    | - Kompatibilität für Software von Drittanbietern durch flexible Schnittstellen              |
| Datenschutzbeauftragte         | Indirekt           | - Persönliche Daten der Studierenden dürfen nur von berechtigten Akteuren eingesehen werden |
| Hersteller dritter Software    | Indirekt           | - Funktionalität durch flexible Schnittstellen muss gewährleistet sein
### Aufgabe 2
1. Die Anforderung ist überprüfbar. Man kann sie eindeutig im Code lokalisieren 
	Lösung: Die Anforderung ist gut überprüfbar. Es handelt sich hierbei um eine genau spezifierte Anforderung einer bestimmten Funktion des Systems. In dem Fall eben die möglichkeit der Importfunktionen Überschriften, Text und Bilder aus DOCX-Dokumenten zu übernehmen 
2. Die Anforderung ist nicht überprüfbar, da "wenig" Speicher nicht definiert ist. Wir können sie Überprüfbar machen, wenn wir "wenig" mit zum Beispiel 1GB definieren: "Die Anwendung darf nur 1GB des RAMs benötigen" 

### Aufgabe 3
![[Bildschirm­foto 2023-02-27 um 20.37.05.png]]

### Aufgabe 4
| Use Case                                 | Beschreibung                                                                                           |
| ---------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| Name                                     | Erstelle Frage                                                                                         |
| Kurzbeschreibung des Anwendungsfallziels | Fragesammlung um eine Frage erweitern                                                                  |
| Umfang                                   | The Quiz                                                                                               |
| Zielart                                  | User Goal                                                                                              |
| Interessengruppe und Interessen          | Spieledesignerin: Will eine Frage erstellen                                                            |
| Minimale Garantien                       | Frage wird nur hinzugefügt, wenn der Fragetyp ausgewählt wurde und die Werte der Frage festgelegt sind |
|                                          | Lösung: Die Fragen bleiben unverändert und die Kategorien bleiben erhalten                             |
| Erfolgsgarantien                         | Die Frage wird der Fragesammlung hinzugefügt                                                           |
|                                          | Lösung: Die Frage wird dem Fragenkatalog hinzugefügt, existierende Kategorien bleiben erhalten         |
| Hauptakteur                              | Spieledesignerin                                                                                       |
| Vorbedingung                             | Die Fragesammlung ist geöffnet                                                                         |
| Haupterfolgsszenario                     | 1. Spieledesignerin wählt Fragetyp aus                                                                 |
|                                          | Lösung: System zeigt verfügbare Fragetypen an                                                          |
|                                          | 2. Das System erstellt eine neue Frage und zeigt diese zum bearbeiten an                               |
|                                          | Lösung: Spieldesignerin wählt einen Fragetyp aus                                                       |
|                                          | 3. Spieledesignerin legt die Werte der Frage fest                                                      |
|                                          | Lösung: System zeigt erstellte Frage zum Bearbeiten an                                                 |
|                                          | 4. Jetzt kann die Frage in Einzel- bzw. Mehrbenutzerspielen verwendet werden                           |
|                                          | Lösung: Spieldesigner legt die Wertde der Frage fest und und bestätigt diese                           |
| Erweiterung                              | 1a 3a Spieledesignerin bricht das Erstellen der Frage ab                                               |
|                                          | 1a1 Die Fragesammlung bleibt unverändert und das System zeigt die geöffnete Fragesammlung an           |
|                                          | 3a1 Die Fragesammlung bleibt unverändert und erstelle Kategorien werden erhalten                       |
|                                          | 3b Kategorie fehlt                                                                                     |
|                                          | 3b1 Das System emöglicht diese nach dem Use Case "Ertstelle Kategorie" hinzuzufügen                    |

### Aufgabe 5
![[Bildschirm­foto 2023-02-27 um 21.30.21.png]]

### Aufgabe 6
- Software Inspektion
	- Ziel: Komplexe Sachverhalte bewerten und Semantische Fehler finden
	- Funktionsweise: 
		- Menschliche Prüfung von Dokumenten
		- Sie kann auf alle Arten von Dokumenten angwendert werden und findet eher Fehlerzustände als Wirkungen
		- Worauf in einem Review geachtet werden muss und welche Rollen dafür nötig sind, wird vorher festgelegt
		- Die Inspektion ist eine spezielle Review mit der Aufgabe Fehler zu finden
		- Dabei wird das Dokument meistens anhand einer Checkliste bewertet
	- Einsatz: Im gesammten Entwicklungsprozess auf möglichst alle Dokumente
- Automated Static analysew
	- Ziel: Automatisches aufdecken von fehlern
	- Funktionsweise:
		- Ein Werkzeug (z.B. eine IDE) überprüft formale Dokumente auf die Verletzung definierter Eigenschaften
	- Einsatz: Im Vorfeld zu Reviews, da sie automatisch Ausführbar sind. 
- Formal Verification
	- Ziel: Abwesenheit von Fehlern beweisen
	- Funktionsweise: Mithilfe mathematischer Beweise werden die formal Spezifiziereten eigenschaften des Codes getestet
	- Einsatz: Ergänzend zum Testen von Sicherheitskritischen Anwendungen
- Testing
	- Ziel: Anwesenheit von Fehlern aufzeigen
	- Funktionsweise:
		- Software wird dynamisch ausgeführt und die Eingabe gemäß eines Testskripts vorgenommen
		- Vom Testorakel vorgegebene Sollwerte werden mit den aktuellen Werten verglichen
	- Einsatz: So früh wie möglich und kontinuierlich. Möglichst automatisierte Tests, zum Beispiel täglich, oder nach jeder veränderung am Code
- Runtime assertion checking
	- Ziel: Einhalten von Rahmenbedinungen während der Laufzeit sicherstellen
	- Funktionsweise:
		- Assertions sind spezielle Anwendungen, welche sicherstellen, dass ein Code so funktioniert wie er soll
		- Bei falschauswertung einer Assertion wird beispielsweise eine Exception geworfen
	- Einsatz: Hilfreich während der Entwicklung und unterstützend beim Debugging

### Aufgabe 7
- Fehlertoleranz
	- Layered: Schlecht: Bei ausfall einer Schicht sind mindestens auch die oberen Schichten davon betroffen
	- MVC: Mittel: Fällt eine View aus, sind die anderen Views davon nicht betroffen, fällt hingegen das Model aus, fällt das gesammte System aus
	- Service Based: Gut: Der ausfall eines Diebstes beschränkt zwar die Funktionalität ein wenig, jedoch beeinflusst der ausfall eines Services nicht die funktionalität der anderen Services
- Parallelisierbarkeit
	- Layered: Schlecht: Parallelisierbarkeit wird von der Architektur nicht unterstützt, da die Schichten strickt sequentiell durchlaufen werden
	- MVC: Mittel: Views, Controller und Model können einzelnen Prozessen leicht zugeordnet werden, jedoch wird die Parallelisierung von der architektur nicht von haus aus unterstützt
	- Service Based: Die Architektur ist von haus aus dazu ausgelegt, verschiedene Servises parallel anzubieten, denn die Dienste können als eigene Prozesse Parallel auf dem gleichen oder unterschiedlichen Rechnern laufen

### Aufgabe 9
**a)**
	- java.lang.object
	- java.io.File;
	- java.io.FileInputStream
	- java.io.ObjectInputStream
	- java.math.BigDecimal
	- java.util.Date
	- model.Receipt
	- java.lang.Exception
	- java.io.PrintStream
	- java.lang.Stringbuilder
	- model.ReceiptPosition
	- java.lang.BigDecimal
	- java.lang.Override
	- **java.lang.String**
**b)**
	Dia Klasse hat eine hohe kopplung zu den Klasse Receipt und ReceiptPosition, weshalb die wiederverwendung ohne die Klassen kein Sinn macht. Da die Klassen aber nur Funktione der Java Standart API nutzen, kann man diese leicht mitübertragen
**c)** ![[IMG_A2C4CDAF3895-1.jpeg]]LCOM = 3 (von 5)

**d)**
Der LCOM Wert spricht für eine geringe Kohäsion. Das ist zutreffend, da die Funktionalität zum laden eines Kassenbelegs in der Methode read(File) abgelöst von der eigentlichen Aufgabde der Klasse ist
**e)**
Nein, beide Methoden sind für die Erfüllung der Aufgabe der Klasse von nöten