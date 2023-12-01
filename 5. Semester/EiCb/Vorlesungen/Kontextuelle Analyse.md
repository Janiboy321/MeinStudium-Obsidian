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

### Speicherung von Attributen 1
###### Imperativer Ansatz (explizite Speicherung) ![[Bildschirmfoto 2023-11-28 um 20.28.50.png]]
###### Objektorientierter Ansatz (explizite Speicherung)
![[Bildschirmfoto 2023-11-28 um 20.30.09.png]]
###### Beobachtungen
- Schon bloße Aufzählungen in Form von Klassen langatmig
- Noch nicht berücksichtigt: Kombinationen
	- `array [1:10] of record int x; char y end`
- Explizite Strukturen können leicht sehr komplex werden

- *Idee*: Im AST stehen bereits alle Daten
	- Deklarations-Unterbaum
- Als Attribute einfach Verweise auf ursprüngliche Definition eintragen
	- Dabei Geltungsbereiche beachten!

### AST-basierte Attribute
![[Bildschirmfoto 2023-11-28 um 20.37.19.png]]

## Identifikation
##### Identifikation
- Erster Schritt der Kontextanalyse
- Beinhaltet Aufbau einer geeigneten Symboltabelle
- Aufgabe: Ordne Verwendungen von Bezeichnern ihren Definitionen zu
- Durch Pass über den AST realisierbar ...

- aber besser: Kombinieren mit nächstem Schritt
$\to$ Typprüfung
##### Typen
- Was ist ein Typ?
	- "Eine Einschränkung der möglichen Interpretationen eines Speicherbereiches oder eines anderen Programmkonstrukts."
	- Eine Menge von Werten
- Warum Typen benutzen?
	- Fehlervermeidung: Verhindere eine Art von Programmierfehlern ("eckiger Kreis")
	- Laufzeitoptimierung: Bindung zur Compile-Zeit erspart Entscheidungen zur Laufzeit
- Muss man immer Typen verwenden?
	- Nein , viele Sprachen kommen ohne aus
		- Assembler, Skriptsprachen, LISP, ...

### Typüberprüfung
- Bei statischer Typisierung ist jeder Ausdruck *E* entweder
	- Misstypisiert, oder
	- Hat einen statischen Typ *T*, der ohne Evaluation von *E* bestimmt werden kann
- *E* wird bei jeder (fehlerfreien) Evaluation den statischen Typ T haben
- Viele moderne Programmiersprachen bauen auf statische Typüberprüfung
	- OO-Sprachen haben aber auch dynamische Typprüfungen zur Laufzeit (Polymorphismus)
###### Generelles Vorgehen
1. Berechne oder leite Typen von Ausdrücken her
	1. Aus den Typen der Teilausdrücke und der Art der Verknüpfung
2. Überprüfe, das Typen der Ausdrücke Anforderungen aus dem Kontext genügen
	1. Beispiel: Bedingungen in if/then muss einen Boolean liefern
###### Genauer: Bottom-Up Verfahren für statisch typisierte Programmiersprache
- Typen an den Blättern des AST sind bekannt
	- Literale - Direkt aus Knoten (true/false, 23, 42, 'a')
	- Variablen - Aus Symboltabelle
- Typen der internen Knoten herleitbar aus
	- Typen der Kinder
	- Typregel für die Art der Verknüpfung im Ausdruck

#### Typüberprüfung einer Funktionsdefinition
`func f (x : ParamType) : ResultType ~Expression`
- Typprüfung des Körpers Expression
- Stelle sicher, dass Ergebnis von ResultType ist
- Dann Herleitung: `f: ParamType ` $\to$ `ResultType`

Idee: Vereinheitliche Typüberprüfung von Funktionen und Operatoren
- $+ : \text{Interger } \times \text{ Integer } \to \text{ Integer}$
- $< :\text{Integer } \times \text{ Integer } \to \text{ Boolean}$
##### Beispiel: Typherleitung für Ausdrücke
![[Bildschirmfoto 2023-12-01 um 18.42.49.png]]
- Typregeln für Binären Ausdruck:
	- Wenn op Operation vom Typ $T_{1} \times T_{2}\to R$ ist, dann ist $E_{1}\ op\ E_{2}$ typkorrekt und vom Typ R wenn $E_{1}\ and\ E_{2}$ typkorrekt und typkompatibel zu $T_1$ bzw. $T_2$ sind.
##### Beispiel: Typherleitung für Anweisungen
Typregel für ifCommand:
	`if E then C1 else C2`
ist typkorrekt genau dann, wenn
	- E vom Typ Boolean ist und
	- C1 und C2 selbst typkorrekt sind
##### Beispiel: Typherleitung für Funktionsaufruf
![[Bildschirmfoto 2023-12-01 um 18.50.22.png]]
Aus Symboltabelle: idOdd: int $\to$ bool
### Algorithmus für Kontextanalyse
- Kombiniere Identifikation und Typprüfung in einem Pass
- Funktioniert, solange Bindung immer vor Verwendung
	- In (mini-)Triangle der Fall
- Mögliche Vorgehensweise
	- Tiefensuche von links nach rechts durch AST
	- Dabei sowohl Identifikation und Typüberprüfung
	- Speichere Ergebnisse durch Dekorieren des ASTs
		- Hinzufügen weiterer Informationen
![[Bildschirmfoto 2023-11-28 um 21.05.54.png]]
![[Bildschirmfoto 2023-11-29 um 15.29.38.png]]
##### Klassendefintionen für AST
$$\begin{align*}
\text{Epression } ::=  &\text{ Integer-Literal} &&&&\text{IntegerExps}\\
& | \text{ V-Name} &&&&\text{VnameExpr}\\
& | \text{ Operator-Expression} &&&&\text{UnaryExpr}\\
& | \text{ Expression Operator Expression} &&&&\text{BinaryExpr}\\
\end{align*}$$
```java
public class BinaryExpr extends Expression{
	public Expression E1, E2;
	public Operator O;
}

public class UnaryExpr extends Expressions{
	public Expression E;
	public Operator O;
}
...
```

**Klassenstruktur für AST:**
![[Bildschirmfoto 2023-11-29 um 15.37.25.png]]
**Gewünschtes Ergebnis:**
![[Bildschirmfoto 2023-11-29 um 15.39.06.png]]
![[Bildschirmfoto 2023-11-29 um 15.42.39.jpg]]

#### Dekorierung des AST: Datenstruktur
Benötigt Erweiterung einiger AST Knoten um zusätzliche Instanzvariablen.
```java
public abstract class Expression extends AST{
	// Every expression has a type
	public Type type;
	...
}

public class Identifier extends Token{
	// Binding occurrence of this identifier
	public Declaration decl;
	...
}
```

## Implementierung
### 1. Versuch: Dekoration mit OO-Ansatz
- Erweitere jede AST-Subklasse um Methoden für
	- Typprüfung, Code-Erzeugung, Pretty-Printing, ...
- In jeder Methode: Durchlauf über Kinder
```java
public abstract AST(){
	public abstract Object check(Object arg);
	public abstract Object encode(Object arg);
	public abstract Object PrettyPrint(Object arg);
	// Der Rückgabewert propagiert Daten aufwärts im AST
	// Extra arg propagiert Daten abwährts im AST
}
...
Programm programm;
program.check(null);
```
- Vorteil
	- OO-Vorgehen leicht verständlich und implementierbar
- Nachteil
	- Verhalten (Prüfung, Erzeugung, ...) ist verteilt über alle AST-Klassen, nicht sonderlich modular
##### Beispiel einer möglichem Implementierung
![[Bildschirmfoto 2023-11-29 um 16.04.38.png]]

### 2. Versuch: "Funktionaler" Ansatz
*Besser(?):* Hier alles Verhalten zusammen in einer Methode
```java
Type check(Expr e){
	if(e instanceof InitLitExpr)
		return representation of type int
	else if(e instanceof BoolLotExpr)
		return representation of type bool
	else if(e instanceof EqExpr){
		Type t = check(((EqExpr)e).left);
		Type u = check(((EqExpr)e).right);
		if(t == representation of type int && u == representation of type int)
			return representation of type bool
	}
}
```
Nicht sonderlich OO, ignoriert eingebauten Dispatcher

#### Alternative: Entwurfsmuster "Besucher"
- Neue Operationen auf Teilelementen (part-of) eines Objekts (z.B. AST)
- ... ohne Änderungen der Klassen der Objekte
- Besonders nütlzich wenn
	- viele unterschiedliche und
	- unzusammenhängende Operationen
- ... ausgeführt werden müssen
- ohne die Klassen der Teilelemente aufzublähen

##### Eigenschaftes des Visitor-Pattern
- Operationen können mit dem Visitor-Pattern leicht hinzugefügt werden
- Visitor sammelt zusammengehörige Operationen und trennt sie von unverwandten
- Visitor durchbricht Kapselung
- Parameter und Return-Typen müssen in allen Visitors gleich sein
- Hängt stark von Klassenstrukturen ab
- ... Visitor problematisch, wenn die Struktur sich noch ändert

##### Benutzung von Visitors 1
- Definiere Visitor-Schnittstelle für Besuch von AST-Knoten
- Füge zu jeder AST-Subklasse XYZ eine einzelne visit-Methode hinzu
	- In der Literatur auch accept genannt, hier missverständlich mit Parser
- Rufe dort Methode visitXYZ der Visitor-Klasse auf
```java 
public abstract class AST {
	public abstract <RetTy, ArgTy> RetTy visit(Visitor<RetTy, ArgTy>) v, ArgTy arg);
}

public class AssignCommand extends Command(){
	public <RetTy, ArgTy> RetTy visit(Visitor<RetTy, ArgTy> v, ArgTy arg){
		return v.visitAssignCommand(this, arg);
	}
	// Unterschiedliche Implementierungen der Methode realisieren die geforderte Funktionalität (Typüberprüfung, Code-Erzeugung, ...)
}
```
```java
public interface Visitor<RetTy, ArgTy>{
	RetTy visitProgram (Program prog, ArgTy arg);
	RetTy visitAssignCommand (AssignCommand cmd, ArgTy arg);
	RetTy visitSequentialCommand (SequentialCommand cmd, ArgTy arg);
	...
	RetTy visitVnameExpression (VnameExpression expr, ArgTy arg);
	RetTy visitBinaryExpression (BinaryExpression expr, ArgTy arg);
}
```
- Allgemeines Schema: Visitor-Interface definiert visitXYZ für alle Subklassen XYZ von AST `public RetTy visitXYZ(XYZ x, ArgTy arg)`;
- `visitXYZ` wird von visit-Methode aufegrufen, die jede Klasse XYZ überschreibt:
```java 
public class XYZ extends ... {
	public <R, A> R visit(Visitor<R, A> v, A arg){
		return v.visitXYZ(this, arg);
	}
}
```

### Kontextanalyse als Visitor
- Erster Ansatz
```java
public class Checker implements Visitor<AST, AST>{
	private IdentificationTable idTab;

	public void check(Program prog){
		idTab = new IdentificatonTable();
		prog.visit(this, null);
	}

	... // Implementierung der Visitor-Methoden
}
```

- Problem (vorweg): Im AST werden unterschiedliche Informationen durch die Rückgabewerte und Argumente propagiert
- Durch AST als Typparameter hat man nicht viel gewonnen
### Kontextanalyse mit mehr Typsicherheit (bei der Implementierung)
```java
	public class Checker {
		private IdentificationTable idTab;
		public void check(Program prog){
			idTable = new IdentificationTable();
			prog.visit(programChecker, null);
		}
	}

	private class CommandChecker extends VisitorBase<Void, Void> {
		public Void visitAssignCommand(AssignCommand cmd, void __) {...}
		...
	}
	private class ExpressionChecker extends VisitorBase<TypeDenoter, Void> {...}
	
	private commandChecker commandChecker = new CommandChecker();
	private ExpressionChecker exprChecker = new ExpressionChecker();
	...
	private ProgramChecker programChecker = new ProgramChecker();
```

##### Beispiel: AssignCommand
```java 
private class CommandChecker extends VisitorBase<Void, Void>{
	public void visitAssignCommand(AssignCommand ast, void __){
		TypeDenoter vType = ast.V.visit(vnameChecker, null);
		TypeDenoter eType = ast.E.visit(expressionChecker, null);
		if(!ast.V.variable){
			reporter.reportError("LHS of assignment is not a variable", "", ast.V.position);
		}
		if(!eType.equals(vType)){
			reporter.reportError("assignment incompatibility", "", ast.position);
		}
		return null
	}
}
```
##### Beispiel: LetCommand
```java
private class CommandChecker extends VisitorBase<Void, Void>{
	...
	public void visitLetCommand(LetCommand ast, void __){
		idTable.openScope();
		ast.D.visit(declarationChecker, null);
		ast.C.visit(commandChecker, null);
		idTable.closeScope();
		return null;
	}
	...
}
```
##### Beispiel: IfCommand
```java
private class CommandChecker extends VisitorBase<Void, Void>{
	public void visitIfCommand(IfCommand ast, void __){
		TypeDenoter eType = ast.E.visit(expressionChecker, null);
			rep
	}
}
```