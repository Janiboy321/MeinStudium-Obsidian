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
- Bekommen Bedeutung durch *Kontext*
	- Variablen, Konstanten, Funktion, ...
- Bei jeder Benutzung nach Namen suchen viel zu *langsam*
- Besser: Weitgehende Vermeidung von String-Operatoren
	- Nehme Zuordnung durch direktes Nachschlagen in Tabelle vor
	- Genannt: Symboltabelle, Identifizierungstabelle, ...
- Beispiel für zugeordnete Attribute
	- *Typ*: int, char, boolean, record, array pointer, ...
	- *Art*: Konstante, Variable, Funktion, Prozedur, Wert-Parameter, ...
	- *Sichtbarkeit*: Public, private, protected
	- *Anderes*: synchronized, static, volatile
- Typische Operatoren
	- *Eintragen* einer neuen Zuordnung Namen-Attribute
	- *Abrufen* der Attribute zu einem Namen
- Hierarchische Blockorganisation
- *Geltungsbereich* von Zuordnungen von Namen zu Attributen innerhalb des Programmes
- *Block* Konstrukt im Programmtext zur Beschreibung von Geltungsbereichen
	- In Java:
		- Geltungsbereiche durch {, } gekennzeichnet
- Unterschiedliche Handhabungsmöglichkeiten von Geltungsbereichen

### Blockstrukturen
##### Monolithische Blockstruktur
![[Bildschirmfoto 2023-11-28 um 20.02.58.png]]
- Charakteristika
	- Nur *ein* Block
	- Alle Deklarationen gelten global
- Regeln für Geltungsbereiche
	- Bezeichner darf nur genau einmal deklariert werden
	- Jeder benutzte Bezeichner muß deklariert sein
- Symboltabelle
	- Für jeden Bezeichner genau ein Eintrag in der Symboltabelle
	- Abruf von Daten muss schnell gehen (binärer Suchbaum, Hash-Tabelle)
- Beispiele: BASIC, COBOL, Skriptsprachen

##### Flache Blockstruktur
![[Bildschirmfoto 2023-11-28 um 20.06.28.png]]

