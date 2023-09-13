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

###### Terminologie:
- Was sind Terme?
	- Namen von Objekten im Beobachtungsbereich. Das können sowohl Objekte als auch Subjekte sein
	
- Variable
	- Stehen für noch nicht bekannte Objekte
	
- Prädikate
	- Stehen für Eigenschaften, Relationen und Klassen, (Im Sprachlichen Sinne, könnten das Verben oder Attribute sein)
	
- Quantoren
	- Quantoren erlauben Aussagen über Mengen von Objekten, für die das Prädikat gilt

Wie stellt man eine Formel in Prädikatenlogik auf?
	- Es regnet in Berlin: $A(x) \equiv$ Es regnet in $x$
	- Es regnet heut in Berlin: $A(x, y) \equiv$ Es regnet zu der Zeit $y$ ind $x$
	- Es regnet in allen Städten: $\$  
