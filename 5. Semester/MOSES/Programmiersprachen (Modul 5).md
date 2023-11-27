### Motivation
##### Was bedeutet ein Programm?
- Bedeutung wird häufig informell angegeben
- Bedeutung kann von Compiler, Laufzeitumgebung usw. abhängen
##### Wie kann man die Bedeutung eines Programms präzise angeben?
- Formale Methoden bieten hierfür eine Möglichkeit
##### Eine formale Spezifikation ermöglicht...
- ein exaktes Verständnis von Programmen
- (beweisbare korrekte) Analysen von Programmen
- die Verifikation von Eigenschaften eines Programms

**Fokus dieses Moduls:** Formalisierung der Semantik einer einfachen imperativen Programmiersprache

### Syntax vs. Semantik
##### Spezifikationssprache in diesem Modul
- IMP - eine einfache imperative Programmiersprache 
##### Semantik der "Spezifikationssprache"
- Syntaxorientierte "Spezifikationssprache"
![[Bildschirmfoto 2023-11-27 um 15.32.11.png]]

### Parser, Interpreter und Compiler
##### Was machen *Parser*, *Interpreter* und *Compiler*?
- Ein *Programmierer* schreibt ein Programm als Text (konkrete Syntax)
- Ein *Parser* überprüft ein Programm auf seine *syntaktische Korrektheit* und erzeugt einen *Syntaxbaum* (abstrakte Syntax)
	- D.h. ein *Parser* übersetzt von konkreter in abstrakte Syntax
- Ein *Interpreter* arbeitet auf dem *Syntaxbaum* (abstrakte Semantik)
- Ein *Compiler* übersetzt den Syntaxbaum in eine maschinennähere Sprache.
	- D.h. ein Compiler erzeugt Text in einer anderen konkreten Syntax
##### Wo spielen *Syntax* und *Semantik* eine Rolle?
- Ein *Programmierer* schreibt ein Programm in einer vorgegebenen konkreten Syntax
	- Dabei hat er eine bestimmte *Intention* (intendierte Semantik)
- Ein *Parser* übersetzt von konkreter in abstrakter Syntax
- *Interpreter* und *Compiler* verarbeiten ein Programm gemäß einer formal definierten Semantik (bzw. definieren die Semantik falls keine andere Definition der Semantik existiert)

## Syntax der Programmiersprache IMP
### Backus-Naur Form
##### Backus-Naur Form
- eine kompakte Schreibweise für Produktionsregeln
- kurz: BNF

##### BNF und Grammatiken
- BNF spezifiziert die Produktionsregeln einer Grammatik $(\Sigma, V, X_{0}, P)$ 
- Sind $\Sigma, V$ und $X_0$ aus dem Kontext klar, dann verwendet man nur die BNF, um Grammatiken zu spezifizieren
###### Beispiel:
Folgende BNF:
$u ::= v_{1} | v_{2} | ... | v_{n}$
ist eine kompakte Schreibweise für folgende Mengen von Regeln:
$u \to v_{1}$
...
$u \to v_{n}$
### Syntax
##### IMP
- eine einfache imperative Programmiersprache
- sequentielle Sprache mit bedingter Verzweigung und Schleifen

##### Übersicht der relevanten Wertebereiche
- $Num$ - die ganzen Zahlen
	- Defintion: $Num = \{0\} \cup \{n | n \in \mathbb{N}\} \cup \{-n | n \in \mathbb{N}\}$
	- Intuition: Symbole die ganze Zahlen repräsentieren
- $Bool$ - die Wahrheitswerte
	- Definition: $Bool = \{true, false\}$
	- Intuition: Symbole, die Wahrheitswerte repräsentieren
- $Var$ - die Programmvariablen
	- Wertebereich $Var$ bleibt undefiniert
	- Intuition: Programmvariablen
- $AExp$ - die arithmetischen Ausdrücke
	- Definition: $a::=\ n\ |\ X\ |\ (a \oplus a)\ |\ (a \ominus a)\ |\ (a \odot a)$
	- Intuition: arithmetische Ausdrücke
- $BExp$ - die booleschen Ausdrücke
	- Definition: $b ::=\ true\ |\ false\ |\ (a\ eq\ a)\ |\ (a\ leq\ a)\ |\ not\ b\ |\ (b\ and\ b)\ |\ (b\ or\ b)$
	- Intuition: boolesche Ausdrücke
- $Com$ - die Kommandos
	- Definition: $c::=\ skip\ |\ X:=a |\ c;c\ |\ if\ b\ then\ c\ else\ c\ fi\ |\ while\ b\ do c\ od$
	- Intuition: Kommandos einer imperativen Programmiersprache
	- Kovention: "Programm" wird als Synonym für "Kommando" verwendet

**Konventionen für Metavariablen**
- $m, n$ - bezeichnet beliebige Elemente aus $Num$
- $t$ - bezeichnet ein beliebiges Element aus $Bool$
- $X, Y$ - bezeichnet beliebige Elemente aus $Var$

### Syntaktische Korrektheit
Ein Wort $c$ ist ein **syntaktisch korrektes Programm** genau dann wenn es in der Grammatik, die $Com$ spezifiziert, ableitbar ist.
Beispiel:
![[Bildschirmfoto 2023-11-27 um 16.01.43.png]]

### Syntaktische Gleichheit
##### Wann sind zwei Ausdrücke / Programme syntaktisch gleich?
- Sind die Ausdrücke $(3 \oplus 5)$ und $(5 \oplus 3)$ syntaktisch gleich?
	- Nein, die sind syntaktisch unterschiedlich, da sich ihre Ableitungen unterscheiden
- Sind die Ausdrücke $(5 \oplus 3)$ und $(5 \oplus 3)$ syntaktisch gleich?
	- Ja, da sie auf gleiche Weise abgeleitet werden

> Ob zwei Ausdrücke/Programme syntaktisch gleich sind, hängt nur davon ab, ob sie die gleichen Ableitungen haben.
> Für syntaktische Gleichheit spielt die intuitive Bedeutung von Ausdrücken/Programmen keine Rolle


## Semantik einer imperativen Programmiersprache
### Zustände
Ein **Zustand** ist eine Funktion $\sigma:\ Var \to Num$. Die **Menge aller Zustände** wird mit $\Sigma$ bezeichnet.
##### Intuition
Ein Zustand ordnet jeder Programmvariablen aus $Var$ einem Wert aus $Num$
zu, d.h. eine ganze Zahl
##### Definition
Sei $\sigma \in \Sigma$ ein Zustand. Dann ist $\sigma[X \backslash n]$ der Zustand, der der Programmiervariablen $X$ den Wert $n$ und jeder anderen Programmvariablen $Y$ den Wert $\sigma(y)$ zuordnet

### Substitution
Eine *Substitution* ist eine Funktion, die eine endliche Menge von Metavariablen als Definitionsbereich hat und jedem Element aus dieser Menge einen Ausdruck zuordnet.
Eine *Grundsubstitution* ist eine Substitution, deren Bildbereich nur Ausdrücke ohne Metavariablen enthält.
Wir verwenden die Notation $[X_{1} \to t_{1}, ..., X_{n} \to t_{n}]$ für die Substitution mit Definitionsbereich $\{X_{1}, \ldots, X_{n}\}$, die $X_{1}$ den Ausdruck $t_{1}, ...$   und $X_{n}$ den Ausdruck $t_{n}$ 
##### Definition
Die *Anwendung einer Substitution $\eta$ auf einen Ausdruck $\alpha$* (geschrieben $\alpha \eta$) resultiert in dem Ausdruck $\beta$, den man erhält, indem man in $\alpha$ jedes freie Auftreten jeder Metavariablen $X$ aus dem Definitionsbereich vin $\eta$ durch $\eta(X)$ ersetzt
###### Beispiel
*Substitution von Metavariablen in Ausdrücken*
$$(( 2 \oplus 1) \odot (Y \ominus X))[X \to (1 \oplus 2)] = ((2 \oplus 1) \odot (Y \ominus (1 \oplus Z)))$$
### Auswertungssemantik
Ein *Urteil* ist ein Schema für Ausdrücke, also ein Ausdruck, der Metavariablen als atomare Ausdrücke enthalten kann. Ein Urteil soll eine gegebene Intuition über ein Sachverhalt formalisieren.
Ein Ausdruck $\xi$ ist eine *Instanz* eines Urteils $\zeta$, wenn $\xi$ und $\zeta$ gleich sind, oder man $\xi$ durch Ersetzen einer oder mehrerer Metavariablen in $\zet$