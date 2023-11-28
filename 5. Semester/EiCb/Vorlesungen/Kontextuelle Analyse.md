![[Bildschirmfoto 2023-11-28 um 19.05.43.png]]

### Kontextuelle Einschränkungen
- ##### Geltungsbereiche (Scope)
- ##### Typen
	- Jeder Wert hat einen Typ
	- Jede Operation
		- hat Anforderungen an die Typen der Operanden
		- hat Regeln für den Typ des Ergebnisses

...auch nicht bei allen Programmiersprachen
- Hier: statische Typisierung (zur Compile-Zeit)
- Alternativ: dynamische Typisierung (Zur Laufzeit)

##### Was Prüfen?
- Benutzung eins Bezeichners muss passende Deklaration haben
- Funktionsaufrufe müssen zu Funktionsdefinitionen passen
- LHS eines Zuweisung muss eine Variable sein
- Ausdruck *if* oder *while* muß Boolean sein
- Beim Aufruf von Unterprogrammen müssen Anzahlen und Typen der aktuellen Parameter mit den formalen Parametern passen
- ...

### Zerlegung von Namen zu Attributen
- Bezeichner sind zunächst Zeichenketten
- Bekommen Bedeutung durch Kontext
	- Variablen, Konstanten, Funktion, ...
- Bei jeder Benutzung nach Namen suchen viel zulangsam
- Besser: Weitgehende Vermeidung von String-Operatoren
	- Nehme Zuordnung durch direktes Nachschlagen in Tabelle vor
	- Genannt: Symboltabelle, Identifizierungstabelle, ...
- Beispiel für zugeordnete Attribute
	- *Typ*: int, char, boolean, record, array pointer, ...
	- *Art*: Konstante, Variable, Funktion, Prozedur, Wert-Parameter, ...
	- *Sichtbarkeit*: Public, private, protected
	- *Anderes*: synchronized, static, volatile
- Typische Operatoren
	- Eintragen einer neuen Zuordnung Namen-Attribute
	- Abrufen der Attribute zu einem Namen
- Hierarchische Blockorganisation
- Geltungsbereich von Zuordnungen von Namen zu Attributen innerhalb des Programmes
