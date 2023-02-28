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
		- Wora