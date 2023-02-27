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
| Rechtsabteilung                | Indirekt           | - Gesetzliche Vorgaben wie zum Beispiel Datenschutz müssen eingehalten werden               |

### Aufgabe 2
1. Die Anforderung ist überprüfbar. Man kann sie eindeutig im Code lokalisieren 
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
| Erfolgsgarantien                         | Die Frage wird der Fragesammlung hinzugefügt                                                           |
| Hauptakteur                              | Spieledesignerin                                                                                       |
| Vorbedingung                             | Die Fragesammlung ist geöffnet                                                                         |
| Haupterfolgsszenario                     | 1. Spieledesignerin wählt Fragetyp aus                                                                 |
|                                          | 2.                                                                                                        |
|                                          |                                                                                                        |