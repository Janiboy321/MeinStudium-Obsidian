 ##### Was ist eine Äquivalenzrelation?
Eine _Relation R_ ist eine Äquivalenzrelation, wenn folgendes gilt:
1. Reflexivität
	Für jedes $x \in X$ gilt: $xRx$
2. Symmetrie
	Für alle $x, y \in X$ gilt: $xRy$ und $yRx$
3. Transitivität
	Für alle $x, y,z \in X$ gilt: $xRy \land yRz \Rightarrow xRz$ 

##### Was ist eine Ordnungsrelation?
Eine _Relation R_ ist eine Ordnungsrelation, wenn folgendes gilt:
1. Reflexivität
	Für jedes $x \in X$ gilt: $xRx$
2. Antisymmetrie
	Für alle $x, y \in X$ für die gilt $xRy$ und $yRx$ folgt, dass $x = y$
3. Transitivität
	Für alle $x, y,z \in X$ gilt: $xRy \land yRz \Rightarrow xRz$ 

##### Was ist ein Gruppenhomomorphismus?
Wir haben zwei Gruppen $(G, \circ)$ und $(H, *)$. Eine Abildung $f: G \rightarrow H$ heißt dann Gruppenhomomorphismus, wenn gilt:
	$f(g_1 * g_2) = f(g_1) \circ f(g_2) \text{ für alle } g1, g2 \in G$

##### Was ist ein Gruppenisomorphismus?
Ein bijektiver Gruppenhomomorphismus

##### Was sind Abelsche Gruppen?
Für eine Gruppe muss folgendes gelten:
1. Assoziativität
	Für alle $a, b, c \in G$ gilt: $a \cdot (b \cdot c) = (a \cdot b) \cdot c$
2. Neutrales Element
	Es gibt ein $n \in G$, sodass für alle $g \in G$ gilt: $n \cdot a = a$ und $a \cdot n = a$
3. Inverses Element
	Es gibt zu jedem $a \in G$ ein $a' \in G$, sodass gilt: $a \cdot a' = n$ und $a' \cdot a = n$  
Gilt zusätzlich folgendes, so ist die Gruppe abelsch
4. Kommutativität (Das macht eine abelsche Gruppe aus)
	Für alle $a, b \in G$ gilt: $a \cdot b = b \cdot a$

##### Was ist ein Ring?
Ein Ring ist eine _Menge R_ mit zwei Verknüpfungen $+: R \times R \rightarrow R$ und $\cdot : R \times R \rightarrow R$ für die fogendes gilt:
	1. $(R, +)$ ist eine abelsche Gruppe
	2. "$\cdot$" ist assoziativ 
	3. $\forall \space a, b, c \in R: a \cdot (b + c) = a \cdot b + a \cdot c \text{ und } (a + b) \cdot c = a \cdot c + b \cdot c$ 

##### Was ist ein Körper
Ein Körper ist ein Kommutativer Ring mit Einselement, für welchen gilt, dass für jedes $a \in K:a \neq 0$ ein Inverses Element existiert.

##### Was ist ein Vektorraum?
Sei $V$ eine Menge und $K$ ein Körper. Weiter seien zwei Verknüpfungen $+:V \times V \rightarrow V$ und $\cdot : K \times V \rightarrow V$ gegeben. Die Menge $V$ mit diesen beiden Verknüpfungen heißt dann K-Vektorraum, wenn folgendes erfüllt wird:
1. $(V, +)$ ist eine abelsche Gruppe
2. $\forall v \in V : 1 \cdot v = v$
3. $\forall v \in V  \space \forall \alpha , \beta \in K : (\alpha \beta) \cdot v = \alpha \cdot (\beta \cdot v)$ 
4. $\forall v \in V  \space \forall \alpha , \beta \in K : (\alpha + \beta) \cdot v = \alpha \cdot v + \beta \cdot v$
5. $\forall v, w \in V  \space \forall \alpha \in K : \alpha \cdot (v + w) = \alpha \cdot v + \beta \cdot w$
 
##### Was ist ein Untervektorraum?
Der Untervektorraum ist eine Teilmenge des Vektorraums, die selbst wieder ein Vektorraum ist.

##### Was ist der Körper der komplexen Zahlen?
$(\mathbb{R}^2, \bigoplus, \bigodot)$

##### Was ist eine singuläre Matrix?
Eine Matrix welche nicht invertierbar ist, also eine Matrix wessen Determinante = 0 ist.

##### Was ist die Euklidische Norm?
 $||x||_2: \space (1, 2, 3)^T = \sqrt{(1)^2 + (2)^2 + (3)^2}$  

##### Was ist die 1-Norm
$||x||_1 : \space (1, 2, 3)^T = |1|+|2|+|3| = 6$

##### Wie bestimmt man Eigenwerte von Matrizen?
1. Man Bildet $A - \lambda \cdot I$ (Also In die Diagonale $-\lambda$ hinzufügen)
2. Davon berechnen wir die Determinante (Diagonalen addieren und Substrahieren, siehe Lösung von Klausur 21/22 Aufgabe 3 a))
3. Von diesem Ergebnis berechnen wir dann die Nullstellen

##### Was ist die algebraische Vielfachheit einer Matrix?
$$
\begin{pmatrix}
4 & 2 & 2 \\
-1 & 1 & -1 \\
3 & 3 & 5
\end{pmatrix}
\begin{matrix}
\lambda_1 = 2 \\
\lambda_2 = 2 \\
\lambda_3 =6
\end{matrix}

$$
Diese Matrix hat die Eiegnwerte 2, 2 und 6. Da der Eigenwert 2 zweimal vorhanden ist, hat die Matrix eine maximale Vielfachheit von 2, und eine minimale Vielfachheit von 1, da es den anderen Eigenwert nur einmal gibt. Eine $3 \times 3$-Matrix, welche drei verschiedene eigenwerte hat, hat also eine Vielfachheit von 3.

##### Wann ist $A$ diagonalisierbar?
Vorgehen:
1. Charakteristisches Polynom bestimmen: Verfällt es nicht vollständig in Linearfaktoren, ist die Matrix nicht Diagonalisierbar
2. Eigenwerte (Nullstellen berechnen): Wenn $n \times n-$Matrix weniger als $n$ Nullstellen hat, ist die Matrix nicht diagonalisierbar
3. Die algebraische Vielfachheit der Matrix muss der vielfachheit der Nullstellen entsprechen

##### Was hat es mit der Form $A = S \cdot D \cdot S^-1$ auf sich?


##### Ist es möglich eine Darstellung für die Matrix  $A$ in der Form $A = S \cdot D \cdot S^-1$ zu finden?
Wenn $A$ diagonalisierbar ist, ist es möglich $A$ so anzugeben.

##### Wie funktioniert der Euklidische Algorythmus?
Beispiel aus Matheprüfung W21/22
$\text{Was ist der ggT von 1242 und 384?}$
$$
\begin{array} {rr} 
a & b & a|b \\
1242 & 384 & 3 \\
384 & 90 & 3 \\ 
90 & 24 & 3 \\
24 & 18 & 1 \\
18 & 6 & 3 \\
6 & 0
\end{array}
$$
1. Fülle die Werte in die erste Zeile, wobei $a$ und $b$ die Werte sind und $a|b$ wie oft $b$ in $a$ passt
2. Ab jetzt ist $a = vorherigeZeile(b)$ und $b = a - (b \cdot a|b)$ der vorherigen Zeile
3. Sobald $b = 0$, hat man den ggT von $a$ und $b$

##### Wie kann man beweisen, ob eine Zahl durch eine andere Teilbar ist?
Beispiel aus Matheprüfung W21/22:
$\text{Zeigen sie, dass } 5^{34} + 3^{15} \text{ durch 13 teilbar ist}$
$$
\begin{flalign}
&5^{34} + 3^{15} \mod 13= 0&  \\
&= \text{ } (5^2)^{2} +(3^3)^{5} \mod 13 = 0\\
&= \text{ } (25 \mod 13)^{17} + (27 \mod 13)^{5} \mod 13=0 \\
&= \text{ } (-1)^{17} + (1)^5 \mod 13 = 0 \\
&= \text{ } (-1) + (1) \mod 13 = 0 \\
&= \text{ } 0 \mod 13 = 0 \\
&\Rightarrow \text{Wird durch 13 geteilt}
\end{flalign}
$$
Hinweis: Versuche die Exponenten Schrittweise so zu erhöhen, dass innerhalb der Klammer eine 1 oder eine -1 steht

##### Was ist ein Erzeugendensystem?

##### Was bedeutet ein Isomorphismus?

##### Wie funktioniert ein Unterbestimmtes Gleichungssystem?
Beispiel:
| x   | y   | z   | b   |
| --- | --- | --- | --- |
| 2   | -6  | 5   | 7   |
| -3  | 9   | -1  | 9   |
$\rightarrow$ Da wir eine Variable mehr haben, als wir Zeilen haben, fügen wir eine Nullzeile hinzu (Wenn man schon eine Nullzeile hat, hat man auch ein unterbestimmtes Gleichungssystem)
| a   | b   | c   | b   |
| --- | --- | --- | --- |
| 2   | -6  | 5   | 7   |
| -3  | 9   | -1  | 9   |
| 0   | 0   | 0   | 0   | 
$\rightarrow$ Jetzt wollen wir das Typische 0er Treppchen erreichen
| a   | b   | c   | b   |                                         |
| --- | --- | --- | --- | --------------------------------------- |
| 2   | -6  | 5   | 7   |                                         |
| -3  | 9   | -1  | 9   | $3 I \cdot 2II$                         |          
| 0   | 0   | 0   | 0   |                                         |
| a   | b   | c   | b   |                                         |
| --- | --- | --- | --- |                                         |
| 2   | -6  | 5   | 7   | $2x-6t+5z=7 ⇒ 2x=-8+6t / :2 ⇒ x=-4+3t$ |
| 0   | 0   | 13  | 39  | $13z = 39 :13 ⇒ z=3$                       |
| 0   | 0   | 0   | 0   | $\Rightarrow y=t$                       |     
$\rightarrow$ Jetzt können wir unsere Matrix
$$
\vec{b}=
\begin{pmatrix}
x \\ y \\ z
\end{pmatrix}
=
\begin{pmatrix}
-4+3t \\ t \\ 3
\end{pmatrix}
$$
so umformen, dass wir alles was mit t zu tun hat, in eine weitere Matrix packen
$$
\Rightarrow \vec{b} =
\begin{pmatrix}
-4 \\ 0 \\ 3
\end{pmatrix}
+t
\begin{pmatrix}
3 \\ 1 \\ 0
\end{pmatrix}
, t \in \mathbb{R}
$$

##### Wie bestimmt man den Kern einer Linearen Abbildung?
Abbildung $\overset{!}{=}$ 0

##### Was bedeutet lineare Abhängigkeit?
