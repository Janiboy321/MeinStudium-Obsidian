- Durch naives übertragen von Daten in Datenbanken kann es zu reduntanten Daten kommen, welche Anomalien hervorrufen können
- Welche Anomalien gibt es?
	- Update-Anomalie
	  - Zieht bspw. ein Kunde um, muss die Adresse in jedem Eintrag in einer Datenbank aktualisiert werden
	  - Passiert das nicht, gibt es eine Update-Anomalie und die Qualität der Daten ist nicht mehr gegeben
	- Einfüge-Anomalie
		- In einer Tabelle können Daten nur eingefügt werden, wenn bspw. auch der Primärschlüssel existiert
		- Zum Beispiel kann so in einer Datenbank mit einer Tabelle Bestellungen kein Lieferant eingefügt werden, ohne dass der Lieferant schonmal etwas geliefert hat
	- Lösch-Anomalie
		- Wenn wir Daten löschen kann es bei schlechter Datenbank-Qualität passieren, dass man Daten löscht, welche man eigentlich garnicht löschen wollte
		- Löcht man beispielsweise alle lieferungen eines Lieferanten, so löscht man den Lieferanten gleich mit, falls er nur in der Tabelle bestellungen existier

