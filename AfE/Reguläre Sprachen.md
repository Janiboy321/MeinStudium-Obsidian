#afe

## Reguläre Sprachen
> Erzeugung besonders einfacher formaler Sprachen, nach Induktiven prinzip, aus einfachsten Basiselementen durch einfache Operationen

#### Reguläre ∑-Sprache
	Da es sich um eine normale Menge handelt, gibt es die Booleschen operatoren 
	und andere:

$$\text{Komplement }L \mapsto \bar{L} : \Sigma ^* \backslash L$$
$$\text{Schnitt }(L_1 , L_2) \mapsto L_1 \cap L_2$$
$$\text{Vereinigung }(L_1 , L_2) \mapsto L_1 \cup L_2$$
$$\text{Konkatenation von Sprachen } (L_1, L_2) \mapsto L_1 \cdot L_2 := \{ u \cdot v : u \in L_1, v \in L_2 \}$$
$$\text{Stern-Operartion } L \mapsto L^* := {u_1 \cdot} \text{ ...} \cdot u_n  \in L, n \in \mathbb{N}$$

## Reguläre Ausdrücke
> Beschreibungen bzw. rekursive Bauanleitungen für die herstellung von bestimmten formalen Sprachen (Und Anleitungen zur erzeugung von reg. Sprachen)

$$\text{Die Menge } REG(\Sigma) \text{ der regulären Ausdrücke über  } \Sigma \text{, wird erzeugt gemäß:}$$*Startelemente:*
$$\text{(i) } \emptyset \text{ ist ein regulärer Ausdruck}$$
$$\text{(ii) } \textbf{a} \text{ ist ein regulärer Ausdruck, für } a \in \Sigma$$
*Aufbauschritte*
$$\text{(iii) für } \alpha, \beta \in REG(\Sigma) \text{ ist } (\alpha + \beta ) \in REG(\Sigma)$$
$$\text{(iii) für } \alpha, \beta \in REG(\Sigma) \text{ ist } (\alpha  \beta ) \in REG(\Sigma)$$
$$\text{(v) für } \alpha \in REG(\Sigma) \text{ ist } \alpha^* \in REG(\Sigma)$$
**Semantik:**
$$\text{Induktiv/rekursiv über }\alpha \in REG(\Sigma) \text{ definiere } L(\alpha):$$
*Startelemente:*
$$\text{(i) } L(\emptyset) := \emptyset$$
$$\text{(ii) }L(a) := \{ a \}$$
$$\text{(iii) }L(\alpha + \beta) := L(\alpha) \cup L(\beta)$$
*Aufbauschritte:*
$$\text{(iii) }L(\alpha  \beta) := L(\alpha) \cdot L(\beta)$$
$$\text{(iii) }L(\alpha ^*) := (L(\alpha))^*$$
###### Definition:
$$\text{Die Regulären } \Sigma \text{-Sprachen sind genau die } L(\alpha) \text{ für } \alpha \in REG(\Sigma)$$

> Die Regulären ∑-Sprachen werden erzeugt aus den Ausgangssprachen ∅ und (a) für a ∈ ∑ durch dir Operatoren **Vereinigung**, **Konkatenation** und **Stern**

*Anmerkung:
$$\Sigma = \{ 0, 1 \} ; \text{ } \alpha = 1^* \cdot 2^* \rightarrow L(\alpha) \text{ enthält z.B.: } \varepsilon, \text{ }1,\text{ } 11, \text{ ... }, \text{ } 11..10, \text{ } 1..10..0, usw. $$
$$\text{nicht in } L(\alpha) \text{ sind z.B. } 01, 1101$$
$$ \bar{L} = \Sigma ^* \backslash L(\alpha) = L(\alpha') \text{ ? geeignetes } \alpha' \text{?}$$
$$\text{Man kann auch sagen: }L(\alpha') = \text{min. ein Vorkommen des Teilwortes } 01$$
$$\text{extra für } \alpha' = (0+1)^* 01(0+1)^* = \Sigma^* 01 \Sigma ^*$$

*Anderes Beispiel:
$$\text{für } \Sigma = \{a_1 + ... +a_n\} \text{ ist }$$
$$\Sigma^* = L ((a_1 + ... + a_n)*)$$
$$\Sigma^+ = \Sigma \backslash \{ \varepsilon\} = L((a_1 + ... +a_n) (a_1 + ... +a_n)^*)$$


> ->Jede endliche ∑-Sprache ist regulär 