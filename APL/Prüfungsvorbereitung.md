## Triviales / Grundlagen
### Aussagenlogik:

##### Wahrheitstabellen aufstellen und Formeln daraus lesen:	

| A   | B   | C   | $\varphi$   |
| --- | --- | --- | --- |
| 0   | 0   | 0   | 1  |
| 0   | 0   | 1   | 0   |
| 0   | 1   | 0   | 1   |
| 0   | 1   | 1   | 0   |
| 1   | 0   | 0   | 1   |
| 1   | 0   | 1   | 0   |
| 1   | 1   | 0   | 1   |
| 1   | 1   | 1   | 0   | 

KNF: $(\lnot A \lor \lnot B \lor C) \land (\lnot A \lor B \lor C) \land (A \lor \lnot B \lor C) \land (A \lor B \lor C)$
DNF: $(\lnot A \land \lnot B \land \lnot C) \lor (\lnot A \land B \land \lnot C) \lor (A \land \lnot B \land \lnot C) \lor (A \land B \land\lnot C)$

##### Junktor $\to$ verstehen und auflösen können

| A   | B   | A → B |
| --- | --- | --------- |
| 0   | 0   | 1         | 
| 0   | 1   | 1         |
| 1   | 0   | 0         |
| 1   | 1   | 1         |

$A \to B = \lnot A \lor B$

##### Junktor $\leftrightarrow$ verstehen und Auflösen

| A   | B   | A $\leftrightarrow$ B |
| --- | --- | --------------------- |
| 0   | 0   | 1                     |
| 0   | 1   | 0                    |
| 1   | 0   | 0                     |
| 1   | 1   | 1                     |

$A \leftrightarrow B = (A \to B) \land (B \to A) = (A \land B) \lor (\lnot A \land \lnot B)$

##### Formeln in DNF oder KNF umformen

1. $\to$ und $\leftrightarrow$ Auflösen
2. $\lnot$ vor Klammern mit De Morgan auflösen
	1. $\lnot(A \lor B) = (\lnot A \land \lnot B)$
	2. $\lnot(A \land B) = (\lnot A \lor \lnot B)$
3. Distributiv Gesetz anwenden
	1. $(A \land (B \lor C)) = (A \land B) \lor (A \land C)$

##### Eine Formel in KNF als Klauselmenge schreiben

$(\lnot A \lor \lnot B \lor C) \land (\lnot A \lor B \lor C) \land (A \lor \lnot B \lor C) \land (A \lor B \lor C)$
$\Rightarrow \{\{\ \lnot A , \lnot B , C\} ,  \{\lnot A , B , C\} ,  \{A , \lnot B , C\} ,  \{A , B , C\}\}$

##### Formeln selbst aufstellen
Tipps:
- Steht in dem Text ein nur, wird $\to$ umgedreht
	- Der Hund frisst (H) nur, wenn die Katze (K)  nicht Frisst $\Rightarrow (\lnot K \to H)$

### Prädikatenlogik

##### Terminologie:
- Was sind Terme?
	- Namen von Objekten im Beobachtungsbereich. Das können sowohl Objekte als auch Subjekte sein
	
- Variable
	- Stehen für noch nicht bekannte Objekte
	
- Prädikate
	- Stehen für Eigenschaften, Relationen und Klassen, (Im Sprachlichen Sinne, könnten das Verben oder Attribute sein)
	
- Quantoren
	- Quantoren erlauben Aussagen über Mengen von Objekten, für die das Prädikat gilt

##### Wie stellt man eine Formel in Prädikatenlogik auf?
-  Es regnet in Berlin: $A(x) \equiv$ Es regnet in $x$
- Es regnet heut in Berlin: $A(x, y) \equiv$ Es regnet zu der Zeit $y$ ind $x$

##### Wie negiert man Quantoren?
- $\lnot \forall x \ P(x) \Leftrightarrow \exists x \ \lnot P(x)$
- $\forall x \ \lnot P(x) \Leftrightarrow \lnot \exists x \ P(x)$
- $\forall x \ P(x) \Leftrightarrow \lnot \exists x \ \lnot P(x)$
-  $\lnot \forall x \ \lnot P(x) \Leftrightarrow \exists x \ P(x)$

##### Was ist die Pränexe Normalform?
- Alle Quantoren einer Formel stehen am Anfang
- Die Formel nach den Quantoren muss eine DNF sein
##### Wie bringt man eine Formel in die Pränexe Normalform
1. Meistens kann man die Quantoren einfach rausziehen (Wenn man es in der richtigen Reihenfolge macht)
	- $( \forall x(x \lor \exists a \exists y (p(q(a) \land y) ) \lor \exists z z)) \equiv \exists z \forall x \exists a \exists y  (x \lor p(q(a) \land y) \lor z)$ 

##### Wie bringt man eine Formel in die Skolem Normalform?
Wichtig: Man kann Formeln nur in Skolem Normalform bringen, wenn die Formel in der Pränex Normalform ist

$F = \forall x \exists a \exists y ((x \lor (p(q(a), y))\lor z))$

1. Allabschluss über alle Freien Variablen
$F' = \forall z \forall x \exists a \exists y ((x \lor (p(q(a), y))\lor z))$

2. Skolemisieren
	- Für alle Existensquantifizierten Variablen führen wir ein neues K-Stelliges (K = Anzahl der Allquantoren vor dem Existenzquantor) Funktionssymbol ein welches Abhängig von allen Variablen ist, die Allquantifiziert sind und links davon stehen
		- Neue Funktionssymbole: h für $\exists a$; i für $\exists y$
		- $F'' = \forall z \forall x((x \lor (p(q(h(x)), i(x)))\lor z))$
	- Steht links von von der Existensquantifizierten Variable kein Allquantor, wird die Variable durch eine Konstante und nicht durch ein K-Stelliges Funktionssymbol ersetzt

3. Teil nach den Quantoren in KNF bringen
	- $(p(q(h(x)), i(x)))$ ist quasi ein Fuktionswert, weshalb da nichts mehr verändert werden muss
	- $F''' = \forall z \forall x(x \lor p(q(h(x)), i(x))\lor z)$

##### Wie substituiert man?
Wichtig: man substituiert nur freie Variablen, welche an keine Quantoren gebunden sind.

Nur freie Variablen:
$S = \{ x \Rightarrow s, y \Rightarrow t\}$
$F = x \lor y$ 
$S(F) = s \lor t$ 

Gebundene Variablen:
$S = \{ x \Rightarrow s, y \Rightarrow t\}$
$F = \forall x (x \lor y)$
$S(F)= \forall x (x \lor t)$

Mit Prädikatensymbol oder Funktionssymbol:
$S = \{ x \Rightarrow s, y \Rightarrow t\}$
$F = \forall x (x \lor p(y \land x))$
$S(F) =  \forall x (x \lor p(t \land x))$ 

Mit Gebundener Variable, aber in anderem Scope:
$S = \{ x \Rightarrow s, y \Rightarrow t\}$
$F = \forall x (x \lor p(y \land x)) \lor x$
$S(F) =  \forall x (x \lor p(t \land x)) \lor s$ 

Komposition:
$(S \circ T)(F)$ = S(T(F))


##### Wie Unifiziert man?

*Mit only Variablen:*
$F = (x \lor p (y \land x)); \ G=(a \lor p(b \land a))$
$S = \{x \Rightarrow s, y \Rightarrow t , a \Rightarrow s, b \Rightarrow t\}$
$S(F)= (s \lor p(t \land s)) = S(G)$

*Mit Variablen und Konstanten:*
$F = (x \lor p (y \land x)); \ G=(C \lor p(b \land a))$
$S = \{x \Rightarrow C, y \Rightarrow t , a \Rightarrow C, b \Rightarrow t\}$
$S(F)= (C \lor p(t \land C)) = S(G)$

*Mit Variablen, Konstanten und Formeln:*
$F = (x \lor p (q(y) \land x)); \ G=(C \lor p(b \land a))$
$S = \{x \Rightarrow C, y \Rightarrow t , a \Rightarrow C, b \Rightarrow q(t)\}$
$S(F)= (C \lor p(q(t) \land C)) = S(G)$

*Beispiel für **nicht** Unifizierbar:**
$F = q(s) \to q(t); \ G = t \to s$
$S = \{t \Rightarrow q(s), \ s \Rightarrow q(t) \}$
$S(G) = q(s) \to q(t)$
$S(F) = q(q(t)) \to q(q(s))$
$\Rightarrow$ Resultiert in einer Infinity Loop

##### Wofür benötigt man die Herbrand-Struktur?
Mithilfe der Herbrand Struktur kann man die Erfüllbarkeit einer Formel in Skolemform nachweisen
##### Hebrand Universum:

$c_{H}$ ist die Herbrand Konstante
$H(F) :=$ Alle Funktionssymbole in Grundinstanz:

*Nur Variablen:*
$F = \forall x P(x, y, z)$
$H(F) = \{c_H\}$

*Nur Konstanten:*
$F= \forall x P(x, a, b, c)$
$H(F) = \{c_{H}, a, b, c\}$

*Unendlich:*
$F = \forall x P(f(x))$
$H(F) = \{ c_{H}, f(c_{H}), f(f(c_{H})), f(f(f(c_{h}))), ... \}$

*Beispiel:*
$F = \forall x \forall y (p(f(x)) \lor \lnot P(y))$
$H(F)=\{c_{H}, f(c_{H}), f(f(c_{H})), f(f(f(c_H)))\}$

##### Herbrand Interpretation
$I = (H(f), \cdot ')$

$F = \forall x \forall y (p(f(x)) \lor \lnot P(y))$
$H(F)=\{c_{H}, f(c_{H}), f(f(c_{H})), f(f(f(c_H)))\}$

Variablen: $x, y \Rightarrow c_{H}, c_{H}$
Konstanten: $a, b \Rightarrow a, b$
Funktionssymbole: $f(x) \Rightarrow f(c_{H})$
Unbekannte Funktion: $f(k(x)) \Rightarrow f(c_{H})$
Unbekanntes Funktionssymbol: $k(f(f(c_{H}))) \Rightarrow c_{H}$

##### Herbrand-Expansion
$$
\begin{align}
E(F) = &\{P(c_{H}) \lor \lnot P(c_{H}), &&&&& c_{H}\\
& P(f(c_{H})) \lor \lnot P(c_{H}) &&&&& f(\cdot) \\
& P(f(f(c_{H}))) \lor \lnot P(f(c_{H})) \\
& P(f(f(c_{H}))) \lor \lnot P(c_{H}) \\
& ... \}
\end{align}
$$
Gleich im ersten Fall haben wir eine Tautologie mit $P(c_{H})\lor \lnot P(c_h)$, daher ist die Formel erfüllbar

##### Was ist ein Semantischer Beweis?
$\varphi \models \psi$
Nutzt die Semantik der Formel, Hier argumentiert man über die Belegung der Formeln. In der Aussagenlogik benutzt man dafür Wahrheitstafeln, in der PL Modelle und Interpretationen
##### Was ist ein Syntaktischer Beweis?
Ein Formaler Beweis ist eine syntaktische Zeichenkette, die bestimmten Regeln gehorchen. In der Vorlesung auch als Herleitung oder Ableitung bezeichnet, die wir mithilfe eines Logikkalküls erstellen. Dazu gehören Resolution, Sequenzenkalkül, etc.

##### Beweisen, dass eine Sequenzenkalkülregel gilt:
Terminologie: $\frac{Prämisse}{Konklusion}$

1. $M \models$ linke seite Konklusion (mit $\land$)
2. Zu zeigen ist dann: $M \models$ rechte Seite$_1$ Konklusion ODER rechte Seite$_2$ Konklusion
3. Wenn $\Delta$, also allgemeine Formelmenge $\to$ Fallunterscheidung:

*Beispiel: Beweise, dass gilt: $\frac{\Gamma, \varphi \ \ \vdash  \ \ \Delta, \psi \ \ \ \ \ \ \Gamma, \psi \ \ \vdash \ \ \Delta, \eta}{\Gamma, \lnot \eta \ \  \vdash \ \ \Delta, \psi \to \varphi}$* 
Sei $\Gamma, \lnot \eta \ \  \vdash \ \ \Delta, \psi \to \varphi$ allgemeingültig und sei $M$ ein Model von $\Gamma, \lnot \eta$, also $M \models \Gamma, \lnot \eta$

1. Fall: $M \models \Delta \Rightarrow$ Fertig
2. Fall: $M \not\models \Delta$, also muss $M \models \psi \to \varphi$ erfüllen.
   $\to$ $M \not\models \Delta, M \models \Gamma, M \models \lnot \eta$
   Damit $\Gamma, \psi \ \ \vdash \ \ \Delta, \eta$ allgemeingültig ist, muss gelten $\lnot \psi$ 
   Da $\psi \to \varphi \equiv \lnot \psi \lor \varphi$, gilt $\lnot \psi$ somit gilt $M \models \psi \to \varphi$ und wir haben gezeigt, dass die Regel gilt.

##### Was sind Modelle?
Modell $M$ für Formelmenge F ist eine Belegung der Variablen 

Interpretation $I = \{x = 1, y = 0, z = 0\}$
$A = x \lor ( \lnot y \land z)$

$val(I, A) = 1 \lor (1 \land 0) = 1$

