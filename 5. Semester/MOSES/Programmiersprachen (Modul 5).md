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
Ein Ausdruck $\xi$ ist eine *Instanz* eines Urteils $\zeta$, wenn $\xi$ und $\zeta$ gleich sind, oder man $\xi$ durch Ersetzen einer oder mehrerer Metavariablen in $\zeta$ durch geeignete Ausdrücke konstruieren kann.
$\xi$ ist eine *Grundinstanz eines Urteils* $\zeta$, wenn $\xi$ eine Instanz des Urteils $\zeta$ ist und $\xi$ keine Metavariablen enthält.
### Notation für Kalkülregeln
![[Bildschirmfoto 2023-11-27 um 17.30.38.png]]
Ein *Kalkül* ist eine Menge von *Kalkülregeln*
##### Herleitbarkeit von Urteilen
Durch Angabe eines Kalküls wird definiert, welche Instanzen eines Urteils *herleitbar* sind.
##### Intuition
Ist eine Grundinstanz des Urteils herleitbar, dann sollte der durch diese ausgedrückte Sachverhalt auch zutreffen. (Angemessenheit)

### Semantik für $AExp$
##### Informelle Beschreibung der Auswertung eines Ausdrucks
Die Auswertung eines arithmetischen Ausdrucks z.B. der Form $(a_{1} \oplus a_{2})$ in einem Zustand $\sigma$ lässt sich wie folgt beschreiben:
- Werte den Ausdruck $a_{1}$ aus, um eine Zahl $n_{1}$ zu erhalten
- Werte den Ausdruck $a_{2}$ aus, um eine Zahl $n_{2}$ zu erhalten
- Der Wert des Ausdrucks $(a_{1} \oplus a_{2})$ ist dann das Resultat der Addition $n_{1}+ n_{2}$
##### Unterscheidung zwischen Syntax und Semantik
- Man beachte, dass das syntaktische Symbol $\oplus$ nicht mit dem Bezeichner $+$ der Addition übereinstimmt
##### Urteil
Wir führen das Urteil $\langle \alpha, \sigma \rangle \Downarrow n$ ein, um auszudrücken, dass
- ein arithmetischer Ausdruck $a \in AExp$ 
- in einem Zustand $\sigma \in \Sigma$
- zu einem Wert $n \in Num$ auswertet.
Der Kalkül enthält Regeln $rNum$, $rVar$, $r \oplus$, $r \ominus$ und $r\odot$, die wie folgt Definiert sind
##### Kalkülregeln
- $r\oplus$ $\ \frac{\langle a_{1} , \sigma \rangle \Downarrow n_{1}\ \ \langle a_{2}, \sigma \rangle \Downarrow n_{2}}{\langle ( a_{1}\oplus a_{2}), \sigma \rangle \Downarrow n}$ $n$ ist die Summe von $n_{1}$ und $n_{2}$
- $r\ominus$ $\ \frac{\langle a_{1} , \sigma \rangle \Downarrow n_{1}\ \ \langle a_{2}, \sigma \rangle \Downarrow n_{2}}{\langle ( a_{1}\ominus a_{2}), \sigma \rangle \Downarrow n}$ $n$ ist die Differenz von $n_{1}$ und $n_{2}$
- $r\odot$ $\ \frac{\langle a_{1} , \sigma \rangle \Downarrow n_{1}\ \ \langle a_{2}, \sigma \rangle \Downarrow n_{2}}{\langle ( a_{1}\odot a_{2}), \sigma \rangle \Downarrow n}$ $n$ ist das Produkt von $n_{1}$ und $n_{2}$
- $rVar$ $\ \frac{}{\langle X, \sigma \rangle \Downarrow n}$ $n = \sigma(X)$
- $rNum$ $\ \frac{}{\langle n, \sigma \rangle \Downarrow n}$ (Eine Regel ohne Prämissen und Seitenbedingungen)
##### Instanziierung von Kalkülregeln
Eine Regel $$\text{r-name} \ \ \ \frac{\xi_{1}, \xi_{2}, ..., \xi_{n}}{\xi}$$
ist die *Instanz (bzw. Grundinstanz) einer Kalkülregel* $$\text{r-name} \ \ \ \frac{\zeta_{1}, \zeta_{2}, ..., \zeta_{n}}{\zeta} \ \ \upphi_{1}, ..., \upphi_{m}$$
wenn es eine Substitution (bzw. Grundsubstitution) $\eta$ gibt, so dass $\xi = \zeta \eta,\ \xi_{1} = \zeta_{1} \eta \ , ...$ und $\xi_{n} = \zeta_{n} \eta$ und die Instanzen $\upphi, \eta, ...$ und $\upphi_{m}\eta$ der Seitenbedinungen erfüllt sind
###### Beispiel:
- Der Zustand $\sigma \in \Sigma$ ordnet allen Programmvariablen den Wert 0 zu. Beide folgenden Regeln sind dann Instanzen der kalkülregeln $r\oplus$!
![[Bildschirmfoto 2023-11-27 um 18.10.50.png]]
### Herleitbarkeit von Urteilen
Die Instanz $\xi$ eines Urteils ist in einem Kalkül *herleitbar* genau dann wenn eine der folgenden beiden Bedingungen erfüllt ist:
- Es gibt eine Kalkülregel der Form $$\text{r-name} \ \ \frac{}{\zeta}\ \ \upphi_{1},... \upphi_{m}$$ und eine Substitution $\eta$, so dass
	- $\zeta \eta = \xi$ und
	- die Instanzen $\upphi_{1}\eta, ...$ und $\upphi_{m}\eta$ der Seitenbedingungen erfüllt sind.
- Es gibt eine Kalkülregel der Form $$\text{r-name} \ \ \ \frac{\zeta_{1}, \zeta_{2}, ..., \zeta_{n}}{\zeta} \ \ \upphi_{1}, ..., \upphi_{m}$$ und eine Substitution $\eta$, so dass
	- $\zeta \eta = \xi;$
	- die Instanzen $\upphi_{1}\eta, ...$ und $\upphi_{m}\eta$ der Seitenbedingungen erfüllt sind 
	- und jede der Instanzen $\zeta_{1}\eta, ...$ und $\zeta_{n}\eta$ der Prämissen herleitbar ist
##### Beispiel (textuelle Herleitung)
Der Zustand $\sigma$ ordnet der Programmvariablen $X$ den Wert 5 zu. Dann ist $\langle (1 \oplus X), \sigma \rangle \Downarrow 6$ herleitbar, weil
- $\langle 1, \sigma \rangle \Downarrow 1$ durch eine Anwendung der Regeln $rNum$ hergeleitet werden kann
- $\langle X, \sigma \rangle \Downarrow 5$ durch eine Anwendung der Regeln $rVar$ hergeleitet werden kann
	- Die Instanz $\sigma(X) = 5$ der Nebenbedingung von $rVar$ ist gültig.
- $\langle (1 \oplus X), \sigma \rangle \Downarrow 6$ aus $\langle 1, \sigma \rangle \Downarrow 1$ und $\langle X, \sigma \rangle \Downarrow 5$ durch eine Anwendung der Regeln $r\oplus$ hergeleitet werden kann.
	- Die Instanz $1 + 5 = 6$ der Nebenbedingung von $r\oplus$ ist gültig.

> Eine Herleitung muss detailliert angegeben werden.
> Insbesondere sollten
> - die Namen der Verwendeten Regeln angegeben werden,
> - alle Prämissen einer Regel hergeleitet werden und
> - die Gültigkeit aller Nebenbedingungen gezeigt werden
##### Beispiel (graphische Herleitung)
![[Bildschirmfoto 2023-11-27 um 18.33.15.png]]
> Eine graphische Herleitung muss detailliert angegeben werden.
> Insbesondere sollten (genau wie bei einer textuellen Herleitung)
> - die Namen der Verwendeten Regeln angegeben werden,
> - alle Prämissen einer Regel hergeleitet werden und
> - die Gültigkeit aller Nebenbedingungen gezeigt werden

### Semantik für $BExp$
##### Urteil
Wie führen das Urteil $\langle b, \sigma \rangle \Downarrow t$ ein, um auszudrücken, dass
- ein boolescher Ausdruck $b \in BExp$
- in einem Zustand $\sigma \in \Sigma$
- zu einem Wert $t \in Bool$ auswertet
Der Kalkül enthält die Regeln rtrue, fralse, reqt, reqf, rleqt, rleqf, rnott, rnotf, randt, randf1, randf2, rort1, rort2 und rorf, die wie folgt definiert sind:
##### Kalkülregeln
$$\begin{flalign}
&\begin{matrix} \text{rtrue} & \frac{}{\langle true, \sigma\rangle\ \Downarrow\  true} &&& \text{rfalse} & \frac{}{\langle false, \sigma\rangle\ \Downarrow\  false}\\ \end{matrix}&
\end{flalign}$$
$$\begin{flalign}
&\begin{matrix}\text{reqt} & \frac{\langle a_{1}, \sigma\rangle\ \Downarrow\ n_{1}\ \ \ \langle a_{2}, \sigma\rangle\ \Downarrow\ n_{2}}{\langle(a_{1}\ eq \ a_{2}), \sigma\rangle\ \Downarrow\ true}& n_{1}\text{ und } n_{2} \text{ sind gleich}\end{matrix} &
\end{flalign}$$
$$\begin{flalign}
&\begin{matrix}\text{reqf} & \frac{\langle a_{1}, \sigma\rangle\ \Downarrow\ n_{1}\ \ \ \langle a_{2}, \sigma\rangle\ \Downarrow\ n_{2}}{\langle(a_{1}\ eq \ a_{2}), \sigma\rangle\ \Downarrow\ false} & n_{1}\text{ und } n_{2} \text{ sind nicht gleich}\end{matrix}&
\end{flalign}$$
$$\begin{flalign}
&\begin{matrix}\text{rleqt} & \frac{\langle a_{1}, \sigma\rangle\ \Downarrow\ n_{1}\ \ \ \langle a_{2}, \sigma\rangle\ \Downarrow\ n_{2}}{\langle(a_{1}\ leq \ a_{2}), \sigma\rangle\ \Downarrow\ true} & n_{1}\text{ ist kleiner oder gleich } n_{2}\end{matrix}&
\end{flalign}$$
$$\begin{flalign}
&\begin{matrix}\text{rleqf} & \frac{\langle a_{1}, \sigma\rangle\ \Downarrow\ n_{1}\ \ \ \langle a_{2}, \sigma\rangle\ \Downarrow\ n_{2}}{\langle(a_{1}\ leq \ a_{2}), \sigma\rangle\ \Downarrow\ false} & n_{1}\text{ ist größer als } n_{2}\end{matrix}&
\end{flalign}$$
$$\begin{flalign}
&\begin{matrix} \text{rnott} & \frac{\langle b, \sigma \rangle\ \Downarrow\ false}{\langle not\ b, \sigma\rangle\ \Downarrow\  true} &&& \text{rnotf} & \frac{\langle b, \sigma \rangle\ \Downarrow\ true}{\langle not\ b, \sigma\rangle\ \Downarrow\  false}\\ \end{matrix}&
\end{flalign}$$
$$\begin{flalign}
&\begin{matrix}\text{randt} & \frac{\langle b_{1}, \sigma\rangle\ \Downarrow\ true \ \ \ \langle b_{2}, \sigma \rangle\ \Downarrow\ true}{\langle(b_{1}\ and \ b_{2}), \sigma\rangle\ \Downarrow\ true}\end{matrix}&
\end{flalign}$$
$$\begin{flalign}
&\begin{matrix} \text{randf1} & \frac{\langle b_{1}, \sigma \rangle\ \Downarrow\ false}{\langle (b_{1}\ and\ b_{2}), \sigma\rangle\ \Downarrow\  false} &&& \text{radnf2} & \frac{\langle b_{2}, \sigma \rangle\ \Downarrow\ false}{\langle (b_{1}\ and\ b_{2}), \sigma\rangle\ \Downarrow\  false}\\ \end{matrix}&
\end{flalign}$$
$$\begin{flalign}
&\begin{matrix} \text{rort1} & \frac{\langle b_{1}, \sigma \rangle\ \Downarrow\ true}{\langle (b_{1}\ or\ b_{2}), \sigma\rangle\ \Downarrow\  true} &&& \text{rort2} & \frac{\langle b_{2}, \sigma \rangle\ \Downarrow\ true}{\langle (b_{1}\ or\ b_{2}), \sigma\rangle\ \Downarrow\  true}\\ \end{matrix}&
\end{flalign}$$
$$\begin{flalign}
&\begin{matrix}\text{rorf} & \frac{\langle b_{1}, \sigma \rangle\ \Downarrow\ false \ \ \ \langle b_{2}, \sigma \rangle\ \Downarrow\ false}{\langle(b_{1} \ or\ b_{2}), \sigma \rangle\ \Downarrow\ false}\end{matrix}&
\end{flalign}$$
### Semantik für Com
##### Urteil 
Wir führen das Urteil $\langle c, \sigma\rangle \to \sigma^{'}$ ein, um auszudrücken, dass
- ein Kommando $c \in Com$
- in einem Zustand $\sigma \in \Sigma$ 
- zu einem Zustand $\sigma^{'} \in \Sigma$ auswertet.
Der Kalkül enthält die Regeln rsk, r:=, r;, rift, riff, rwht und rwhf, die wie folgt definiert sind:
##### Kalkülregeln
$$\begin{flalign}
&\begin{matrix} \text{...} & \frac{}{} \end{matrix}&
\end{flalign}$$
$$\begin{flalign}
&\begin{matrix} \text{rsk} & \frac{}{\langle skip, \sigma \rangle \to \sigma} \end{matrix}&
\end{flalign}$$
$$\begin{flalign}
&\begin{matrix} \text{r:=} & \frac{\langle a, \sigma \rangle\ \Downarrow\ n}{\langle X\ :=\ a, \sigma \rangle \to \sigma^{'}} &&& \sigma^{'} = \sigma[X \backslash n]\end{matrix}&
\end{flalign}$$
$$\begin{flalign}
&\begin{matrix} \text{r;} & \frac{\langle c_{1}, \sigma \rangle \to \sigma^{''}\ \ \ \langle c_{2}, \sigma^{''} \rangle \to \sigma^{'}}{\langle c_{1}; c_{2},\ \sigma \rangle \to \sigma^{'}} \end{matrix}&
\end{flalign}$$
$$\begin{flalign}
&\begin{matrix} \text{rift} & \frac{\langle b, \sigma\rangle\ \Downarrow\ true \ \ \ \ {\langle c_{1}, \sigma \rangle \to \sigma^{'}}}{\langle if\ b\ then\ c_{1}\ else\ c_{2} \ fi,\ \sigma\rangle \to \sigma^{'}} \end{matrix}&
\end{flalign}$$
$$\begin{flalign}
&\begin{matrix} \text{riff} & \frac{\langle b, \sigma\rangle\ \Downarrow\ false \ \ \ \ {\langle c_{2}, \sigma \rangle \to \sigma^{'}}}{\langle if\ b\ then\ c_{1}\ else\ c_{2} \ fi,\ \sigma\rangle \to \sigma^{'}} \end{matrix}&
\end{flalign}$$
$$\begin{flalign}
&\begin{matrix} \text{rwht} & \frac{\langle b,\ \sigma\rangle\ \Downarrow\ true \ \langle c, \sigma \rangle \to \sigma^{''} \ \langle while\ b\ do\ c\ od,\ \sigma^{''}\rangle \to \sigma^{'}}{\langle while\ b\ do\ c\ od,\ \sigma\rangle \to \sigma} \end{matrix}&
\end{flalign}$$
$$\begin{flalign}
&\begin{matrix} \text{rwhf} & \frac{\langle b,\ \sigma\rangle\ \Downarrow\ false }{\langle while\ b\ do\ c\ od,\ \sigma\rangle \to \sigma} \end{matrix}&
\end{flalign}$$
### Semantische Äquivalenz
##### Wann sind zwei Ausdrücke semantisch äquivalent?
- Die Auswertungssemantik induziert auf natürliche Weise einen semantischen Äquivalenzbegriff
- Beachte den unterschied zu syntaktischer Gleichheit!
##### Definition
Zwei *boolesche Ausdrücke $b_{1}, b_{2}\in BExp$, die keine Metavariablen enthalten, sind zueinander semantisch äquivalent* wenn für alle Zustände $\sigma \in \Sigma$ die folgenden beiden Bedingungen gelten:
- $\langle b_{1},\ \sigma \rangle\ \Downarrow \ true$ ist herleitbar genau dann, wenn $\langle b_{2},\ \sigma \rangle\ \Downarrow \ true$ herleitbar ist.
- $\langle b_{1},\ \sigma \rangle\ \Downarrow \ false$ ist herleitbar genau dann, wenn $\langle b_{2},\ \sigma \rangle\ \Downarrow \ false$ herleitbar ist.
##### Können ungleiche Ausdrücke Äquivalent sein?
###### Ja, Beispiel:
- Die beiden booleschen Ausdrücke $(false,\ true)$ und $(false\ and\ true)$ sind nicht syntaktisch gleich.
- Aber:
	- Für alle Zustände $\sigma \in \Sigma$ ist nur das Urteil $\langle (false\ and\ true), \sigma \rangle \ \Downarrow false$ herleitbar
	- Für alle Zustände $\sigma \in \Sigma$ ist nur das Urteil $\langle (false\ and\ false), \sigma \rangle \ \Downarrow false$ herleitbar
- Also: Für alle Zustände $\sigma \in \Sigma$ und boolesche Werte $t \in Bool$ ist das Urteil $\langle (false\ and\ true), \sigma \rangle \ \Downarrow\ t$ herleitbar genau dann, wenn das Urteil $\langle (false\ and\ false), \sigma \rangle \ \Downarrow\ t$ herleitbar ist
- Das heißt, die beiden Ausdrücke sind semantisch äquivalent

> Die semantische Äquivalenz berücksichtigt nur die Bedeutung von Ausdrücken, unabhängig von ihrer Syntax.

##### Wann sind Ausdrücke mit Metavariablen semantisch äquivalent?
Zwei boolesche Ausdrücke $b_{1}, b_{2} \in BExp$ (die Metavariablen enthalten dürfen) sind zueinander semantisch äquivalent, wenn für alle Grundsubstitutionen $\eta$, deren Definitionsbereich alle Metavariablen in $b_{1}$ und $b_{2}$ einschließt, und für alle Zustände $\sigma \in \Sigma$ die folgenden beiden Bedingungen gelten:
- $\langle b_{1}\eta, \sigma \rangle\ \Downarrow\ true$ ist herleitbar genau dann, wenn $\langle b_{2}\eta, \sigma \rangle\ \Downarrow\ true$ herleitbar ist,
- $\langle b_{1}\eta, \sigma \rangle\ \Downarrow\ false$ ist herleitbar genau dann, wenn $\langle b_{2}\eta, \sigma \rangle\ \Downarrow\ false$ herleitbar ist
###### Beispiel
Seien $X und Y$ Programmvariablen, dann sind die beiden booleschen Ausdrücke $((X\ eq\ 5)\ and\ (Y\ eq\ X))$ und $((X\ eq\ Y)\ and\ (Y\ eq\ (3 \oplus 2)))$ semantisch äquivalent:

##### Definition
Zwei *arithmetische Ausdrücke $a_{1}, a_{2} \in AExp$ sind zueinander semantisch äquivalent* wenn für alle Grundsubstitutionen $\eta$, deren Definitionsbereich alle Metavariablen in $a_{1}$ und $a_{2}$ einschließt, und für alle Zustände $\sigma \in \Sigma$ und für alle ganzen Zahlen $n$ fie folgende Bedingung gilt:
- $\langle a_{1}\eta \rangle\ \Downarrow\ n$ ist herleitbar genau dann wenn $\langle a_{2}\eta, \sigma\rangle \ \Downarrow\ n$ herleitbar ist
##### Definition
Zwei *Kommandos $c_{1}, c_{2} \in Com$ sind zueinander semantisch äquivalent* wenn für alle Grundsubstitutionen $\eta$, deren Definitionsbereich alle Metavariablen in $c_{1}$ und $c_{2}$ einschließt, und für alle Zustände $\sigma, \sigma^{'} \in \Sigma$ die folgende Bedingung gilt:
- $\langle c_{1} \eta, \sigma\rangle \to \sigma^{'}$ ist herleitbar genau dann, wenn $\langle c_{2} \eta, \sigma\rangle \to \sigma^{'}$ herleitbar ist
##### Können ungleiche Programme äquivalent sein?
###### Ja, Beispiel:
- Die Programme $if\ b\ then\ c_{1}\ else\ c_{2} fi$ und $if\ not\ b\ then \ c_{2}\ else\ c_{1}\ fi$ sind nicht syntaktisch gleich
- Aber:
	- Für alle Zustande $\sigma, \sigma^{'} \in \Sigma$ und Grundsubstitutionen $\eta$ ist das Urteil $\langle (if\ b\ then\ c_{1}\ else\ c_{2}\ fi)\eta, \sigma\rangle \to \sigma^{'}$ herleitbar genau dann wenn das Urteil $\langle (if\ not\ b\ then\ c_{2}\ else\ c_{1}\ fi)\eta, \sigma\rangle \to \sigma^{'}$ herleitbar ist.
- Das heißt, die beiden Programme sind semantisch äquivalent.