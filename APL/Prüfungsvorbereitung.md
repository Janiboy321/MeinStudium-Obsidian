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

##### Wie bringt man eine Formel in die Pränexe Normalform
1. Meistens kann man die Quantoren einfach rausziehen (Wenn man es in der richtigen Reihenfolge macht)
	- $( \forall x(x \lor \exists a \exists y (p(q(a) \land y) ) \lor \exists z z)) \equiv \exists z \forall x \exists a \exists y  (x \lor p(q(a) \land y) \lor z)$ 

##### Wie bringt man eine Formel in die Skolem Normalform?
Wichtig: Man kann Formeln nur in Skolem Normalform bringen, wenn die Formel in der Pränex Normalform ist

$F = \forall x \exists a \exists y ((x \lor (p(q(a), y))\lor z))$

1. Allabschluss über alle Freien Variablen
$F' = \forall z \forall x \exists a \exists y ((x \lor (p(q(a), y))\lor z))$

2. Skolemisieren
	- Für alle Existensquantifizierten Variablen führen wir ein neues K-Stelliges Funktionssymbol ein welches Abhängig von allen Variablen ist, die Allquantifiziert sind und links davon stehen
		- Neue Funktionssymbole: h für $\exists a$; i für $\exists y$
		- $F'' = \forall z \forall x((x \lor (p(q(h(x)), i(x)))\lor z))$

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
