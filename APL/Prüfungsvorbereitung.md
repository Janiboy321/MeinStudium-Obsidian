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

