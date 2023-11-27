### Motivation
###### Was bedeutet ein Programm?
- Bedeutung wird häufig informell angegeben
- Bedeutung kann von Compiler, Laufzeitumgebung usw. abhängen
###### Wie kann man die Bedeutung eines Programms präzise angeben?
- Formale Methoden bieten hierfür eine Möglichkeit
###### Eine formale Spezifikation ermöglicht...
- ein exaktes Verständnis von Programmen
- (beweisbare korrekte) Analysen von Programmen
- die Verifikation von Eigenschaften eines Programms

**Fokus dieses Moduls:** Formalisierung der Semantik einer einfachen imperativen Programmiersprache

### Syntax vs. Semantik
###### Spezifikationssprache in diesem Modul
- IMP - eine einfache imperative Programmiersprache 
###### Semantik der "Spezifikationssprache"
- Syntaxorientierte "Spezifikationssprache"
![[Bildschirmfoto 2023-11-27 um 15.32.11.png]]

### Parser, Interpreter und Compiler
###### Was machen *Parser*, *Interpreter* und *Compiler*?
- Ein *Programmierer* schreibt ein Programm als Text (konkrete Syntax)
- Ein *Parser* überprüft ein Programm auf seine *syntaktische Korrektheit* und erzeugt einen *Syntaxbaum* (abstrakte Syntax)
	- D.h. ein *Parser* übersetzt von konkreter in abstrakte Syntax
- Ein *Interpreter* arbeitet auf dem *Syntaxbaum* (abstrakte Semantik)
- Ein *Compiler* übersetzt den Syntaxbaum in eine maschinennähere Sprache.
	- D.h. ein Compiler erzeugt Text in einer anderen konkreten Syntax
###### Wo spielen *Syntax* und *Semantik* eine Rolle?
- Ein *Programmierer* schreibt ein Programm in einer vorgegebenen konkreten Syntax
	- Dabei hat er eine bestimmte *Intention* (intendierte Semantik)
- Ein *Parser* übersetzt von konkreter in abstrakter Syntax
- *Interpreter* und *Compiler* verarbeiten ein Programm gemäß einer formal definierten Semantik (bzw. definieren die Semantik falls keine andere Definition der Semantik existiert)

### Backus-Naur Form
###### Backus-Naur Form
- eine kompakte Schreibweise für Produktionsregeln
- kurz: BNF