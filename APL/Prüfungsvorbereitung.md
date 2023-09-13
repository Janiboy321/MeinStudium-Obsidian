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

DNF: $(\lnot A \lor \lnot B \lor C) \land (\lnot A \lor B \lor C) \land (A \lor \lnot B \lor C) \land (A \lor B \lor C)$
KNF: $(\lnot A \land \lnot B \land \lnot C) \lor (\lnot A \land B \land \lnot C) \lor (A \land \lnot B \land \lnot C) \lor (A \land B \land\lnot C)$

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

1. 