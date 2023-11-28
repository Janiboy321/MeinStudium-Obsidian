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

### Darstellung von Scannern als endliche Autom