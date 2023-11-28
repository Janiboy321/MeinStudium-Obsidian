#### Häufige Fehler bei LL(k) Parsern
Hinweis: LL(k)-Parser sind Top-Down Parser, welche von Links nach rechts arbeiten und k Tokens vorausschauen können

###### Grammatik ist nicht LL(1)
![[Bildschirmfoto 2023-11-28 um 18.05.58.png]]
Es gibt zweimal identifier auf der rechten Seite

##### Linksausklammern vergessen![[Bildschirmfoto 2023-11-28 um 18.14.48.png]]
![[Bildschirmfoto 2023-11-28 um 18.15.45.png]]
##### Linksrekursion nicht beseitigt
![[Bildschirmfoto 2023-11-28 um 18.17.50.png]]

### Scanner
- Auch genannt lexikalische Analyse oder Lexer
- Ähnlich Parsing, aber auf einer Ebene feinerer Details
	- Parser: Arbeitet mit Tokens, die zu Phrasen gruppiert werden
	- Scanner Arbeitet mit Zeichen, die zu Tokens gruppiert werden
- Aufgaben des Scanners
	- Bilde Tokens aus Zeichen
	- Entferne unerwünschte Leerzeichen, Zeilenvorschüber, etc. (White space)
	- Führe Buch über Zeilennummern und Eingabedateinnamen

### Scanner-Sicht auf Tokens
Tokens werden durch REs definiert, bestehend aus:
- Einzelzeichen
- Operatoren
	- Konkatenation: A B
	- Alternative A | B
	- Optionalität: A?
	- Wiederholung: A*
	- Vordefinierte REs (sog. Macros)
- aber: keine rekursiv Definitionen

### Darstellung von Scannern als endliche Automaten
- Reguläre Ausdrücke können durch Übergangsdiagramme dargestellt werden
	- Endliche Automaten
	- Kanten/Transitionen beschriftet mit Eingabesymbolen
	- Zustände/Knoten
		- Genau ein Startzustand
		- Beliebig viele Endzustände (akzeptierende Zustände)
![[Bildschirmfoto 2023-11-28 um 18.38.49.png]]

#### Alternative: Rekursiver Abstieg
Systematische Konstruktion von Scannern
1. Formuliere lexikalische Grammatik in EBNF
	1. Falls nötig: Transformiere für rekursiven Abstieg
2. Implementiere Scan-Methoden scanN für jede Produktion $N ::= X$, mit Rumpf passend zu $X$
3. Implementier Scanner-Klasse, bestehend aus
	- protected Instanzvariable *currentChar*
	- protected Methoden *take* und *takeIT*
		- Analog zu *accept / acceptIt* im Parser
		- Lesen diesmal aber zeichenweise in currentChar
	- protected Scan-Methoden aus 2., erweitert um Erstellen von Token-Objekten
	- Eine public Methode scan, die den nächsten Token liefert
		- Überspringt dabei white space und Kommentare
![[Bildschirmfoto 2023-11-28 um 18.44.55.png]]
