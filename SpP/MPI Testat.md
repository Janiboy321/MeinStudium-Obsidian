### Task 1
##### Reduce
1. Zuerst holen wir und die Anzahl an Prozessen
	- Dafür rechnen wir last - first + 1
2. Dann checken wir, ob es nur ein Prozess gibt
	- Wenn ja, nutzen wir einfach den Wert, den der eine Prozess verwendet
3. Falls wir mehr als einen Thread haben, rufen wir reduce Rekursiv auf. Dazu teilen wir die Anzahl der Prozesse in zwei Hälften und rufen pro hälfte nochmal reduce auf, das passiert solange bis wir nurnoch einen Prozess für reduce haben.
4. Nach dem Rekursiven call passiert folgendes:
	- Wenn der Aktuelle Prozess der erste ist, Starten wir den Receive Call und speichern den entfangenen Wert in temp. Dann rechnen wir den Wert auf buf drauf.
	- Ist der Aktuelle Prozesse der mid Prozess, senden wir den inhalt des Buf
	- Im Prinzip rechnen wir so dir Ergebnise der aufrufe von reduce zusammen

##### Reduce
1. Zuerst initialisieren wir MPI
2. Dann holen wir uns die Anzahl der Threads und den Rank des aktuellen Threads
3. Dann Checken wir, ob wir einen Input gegeben haben
4. Dann holen wir uns den Input
5. Dann checken wir, ob die Anzahl der Punkte valide ist
6. Dann printed der erste Prozess, mit wievielen Prozessen das programm läuft
7. Jetzt gucken wir, ob die Anzahl der Punkte kleiner als die Anzahl der Prozesse ist, falls ja, setzen wir die Anzahl der Punkte auf die Prozesse
8. Dann Berechnen wir das Integral, dazu haben wir eine Funktion die eine Random zahl erstellt und zwei funktionen die Max bzw min ausrechnen.
9. Der letzte Prozess printet dann das Ergebnis
10. Zuletzt schließen wir MPI

##### Heatet Plate
1. Wir initialisieren MPI
2. Wir holen und die Anzahl der Prozesse und den Rank des Aktuellen Prozesses
3. Wir erstellen ein paar Variablen und initialisieren epsilon mit einem ganz kleinen Wert, om eine 0 Division zu verhindern
4. Zuerst checken wir, ob die Anzahl der Prozesse größer als die Anzahl der Zeilen in der Matrix ist, falls ja geben wir das aus und returnen mit 1
5. Dann Printet der Master Prozess ganz viele Informationen
6. Jetzt errechnen wir unsere Bucket size, also wie viele Zeilen jeder Prozess bekommt
7. Dann errechnen wir uns die Startadresse für den aktuellen Prozess und die End Adresse des aktuellen Prozesses
8. Falls die Verteilung nicht gerade aufgeht, bekommt der letzte Prozess die restlichen zeilen
10. Dann erstellen wir zwei vectoren in welche wir jeweil ein Vektor der größe BucketSize speichern welche wir jeweils nochmal einen Vektor der Länge N speichern
11. Jetzt füllen wir die Vektoren mit den Werten wie in der Aufgabenstellung
12. Jetzt berechnen wir den durchschnittswert der links und recht liegenden Ränder
13. Jetzt berechnen wir den durchschnittswert der Oberen bzw. unteren Zeile (was nur passiert, wenn der Prozess auch die obere bzw. untere Zeile inne hält)
14. Jetzt Summieren wir die Ergebnise der Rechnungen und speicher ihn in receive_mean und schreiben den wert dann in mean
15. Jetzt teilen wir das nochmal durch die Anzahl der Randelemente und geben das Ergebniss schlussendlich aus
16. Jetzt Broadcasten wir den wert auf alle Prozesse 
17. Jetzt Füllen wir die Zeilen mit dem durchschnittswert
18. Jetzt Updaten wir die alte Matrix. Wir ersetzen die Werte solange bis der Unterschied von u und w kleiner als epsilon ist
19. Jetzt Syncen wir die Prozesse
20. Jetzt erstellen wir Vectoren in denen wir ggf. die Vektoren, welche aus anderen Prozessen stammen abspeichern. Dazu erstellen wir noch hilfsvariablen, welche ausgeben, ob diese Vektoren befüllt wurden
21. Wenn es mehr als einen Prozess gibt, senden wir erstmal die Unterste Zeile eines jeden Prozesses (bis auf den letzten Prozess) an den nächsten Prozess und fügen diese dann an den vektor ganz unten an
22. Das gleiche machen wir jetzt andersherum und fügen die Zeile an den Anfang der Matrix
24. Jetzt Berechnen wir den Durchschnittswert von den 4 benachbarten Feldern
25. Dann löschen wir die Zeilen wieder aus der Matrix raus
26. Jetzt berechnet jeder Prozess die differenz seiner eigenen Zeilen aus (Also zwischen den Zeilen von u und w) was dann wieder reduziert wird und printen dann die Iterationen einmal aus
27. Dann syncen wir wieder
