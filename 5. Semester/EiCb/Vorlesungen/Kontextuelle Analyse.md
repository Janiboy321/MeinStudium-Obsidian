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
![[Bildschirmfoto 2023-11-28 um 20.07.43.png]]
- Charakteristika
	- Mehrere überlappungsfreie Blöcke
	- Zwei Geltungsbereiche: Global und Lokal
- Regeln für Geltungsbereiche
	- Global/lokal deklarierte Bezeichner dürfen nicht global/im selben Block redeklariert werden
	- Jeder benutzte Bezeichner muss global oder lokal zu seiner Verwendungsstelle deklariert sein
- Symboltabelle
	- Bis zu zwei Einträge pro Bezeichner (global und lokal)
	- Nach Bearbeiten eines Blocks müssen lokale Deklarationen verworfen werden
	- Beispiel: FORTRAN

##### Verschachtelte Struktur
![[Bildschirmfoto 2023-11-28 um 20.10.56.png]]
- Charaktristika
	- Blöcke ineinander verschachtelt
	- Beliebige Schachtelungstiefe der Blöcke
- Regeln für Geltungsbereiche
	- Kein Bezeichner darf mehr als einmal innerhalb eines Blocks deklariert werden
	- Kein Bezeichner darf verwendet werden, ohne Deklaration im lokalen oder umschließenden Block
- Symboltabelle
	- Mehrere Einträge je bezeichner möglich
	- Aber maximal ein Paar (Tiefe, Bezeichner)
	- Schneller Abruf des Eintrags mit der größten Verschachtelungstiefe
- Beispiele: Pascal, Modula, Ada, Java, ...

### Implementierung der Symboltabelle
- Verschiedene Varianten
	- Verkettete Liste und lineare Suche
		- Einfach aber langsam
		- Ursprünglich in Triangle verwendet (natürlich ...)
	- Hier: Bessere Möglichkeiten mit Hash-Tabelle (effizienter)
	- Hash-Tabelle, die Stacks enthält
- Design-Kriterium
	- Gleiche Bezeichner tauchen häufiger in Tabelle auf
	- Aber auf unterschiedlichen Ebenen
	- Abgerufen wird immer der am tiefsten gelegene

#### Effizientere Implementierung
```java 
public final class IdentificationTable{
	private Map<String, Stack<Attribute>> idents;
	private Stack<List<String>> scopes;
	...
}
```
###### idents
- Bildet von Strings auf Attribute-Objekte ab
- Bezeichnernamen dienen als Schlüssel
- Wert ist ein Stack aus Attributen, obenauf liegt die Deklaration mit der tiefsten Verschachtelungsebene
###### scopes
- Stack bestehend aus Listen von Strings
- Bei Öffnen eines neuen Geltungsbereichs:
	- Lege leere Liste auf Scopes
	- Jeder in diesem Bereich gefundene Bezeichner wird in einer Liste eingetragen
- Bei schließen des aktuellen Geltungsbereiches
	- Gehe Liste oben auf scopes durch
	- Lösche alle diese Bezeichner aus idents (entferne jeweils oberstes Stapelelement)
	- Entferne dann oberstes Element von scopes

### Attribute
- Welche Informationen konkret zu einem Bezeichner speichern?
- Wofür werden Attribute gebraucht?
- Mindestens für
	- Überprüfung der Regeln für Geltungsbereiche von Deklarationen
		- Bei geeigneter Implementierung der Symboltabelle: Einfaches Abrufen reicht
		- Alle Regeln bereits in Datenstruktur realisiert
	- Überprüfung der Typregeln
		- Erfordert Abspeicherung von Typinformationen
	- (Code-Erzeugung)
		- Benötigt später z.B. Andresse der Variable im Speicher