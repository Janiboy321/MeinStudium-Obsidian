
#### Was ist ein angeordneter Körper? #card
$\text{Ein Körper K mit einer Totalorndung } \leq \text{, für die gilt:}$
- $\forall a,b,c \in K: a \leq b \Rightarrow a+b \leq b+c$ und
- $\forall a,b,c \in K: (a \leq b \text{ und } 0 \leq c) \Rightarrow ac \leq bc$

#### Wann ist eine Teilmenge $M \subseteq \mathbb{R}$ nach oben (unten) beschränkt? #card 
$\text{Wenn sie eine obere (untere) Schranke besitzt}$

#### Wann ist eine Teilmenge $M \subseteq \mathbb{R}$ beschränkt? #card 
$\text{Wenn sie nach unten bzw. oben beschränkt ist}$

#### Was ist die Betragsfunktion? #card
$\text{Die Funktion } | \cdot |: \mathbb{R} \rightarrow \mathbb{R} \text{ mit }$
$$|x| := \left\{
\begin{array}{ll}
x &  \text{ falls }x \geq 0 \\
-x & \, \textrm{falls } x < 0 \\
\end{array}
\right.$$
$\text{heißt Betragsfunktion und } |x| \text{ heißt Betrag von } x$

#### Welche Rechenregeln gelten für Betragsfunktionen? #card 
$$
\begin{align}
& (a) &&|x| \geq 0 \\
& (b) &&|x| = |-x| \\
& (c) &&\pm x \leq |x| \\
& (d) && |xy| = |x| \cdot |y| \\
& (e) && |x| = 0 \Leftrightarrow x= 0 \\
& (f) && |x+y| \leq |x|+|y|
\end{align}
$$

#### Wie lauten die Intervallkonvertionen? #card 
- $(a, b) := \{x \in \mathbb{R} : a < x < b \} \Rightarrow$ Offenes Intervall
- $[a, b] := \{x \in \mathbb{R} : a \leq x \leq b \} \Rightarrow$ Geschlossenes Intervall

#### Wie vereinfacht man $x^n$, $x^{-n}$ sowie $x^0$? #card 
- $x^{n}:= x \cdot x \cdot \dotsc \cdot x$
- $x^{-n} := \frac{1}{x^{n}} \text{, falls }x ≠ 0$
- $x^{0}=1$

#### Seien $q \in \mathbb{Q}$ und $m, p \in \mathbb{Z}$ sowie $n, r \in \mathbb{N}^*$, so dass $q = m / n = p / r$. Dann gilt für jedes $x \in \mathbb{R}_+$: #card 
$$(\sqrt[n]{x})^{m}= (\sqrt[r]{x})^p$$

#### Wie lauten die Potenzrechenregeln? #card 
$$
\begin{flalign}{}
 &\bullet x^{p}x^{q} = x^{p+q} &\bullet \frac{x^{p}}{x^{q}} = x^{p-q} \\ \\
 &\bullet x^{p}y^{p} = (xy)^{p} &\bullet \frac{x^{p}}{y^{p}} = (\frac{x}{y})^{p} \\ \\
 &\bullet(x^{p})^{q} = x^{pq}
\end{flalign}
$$

#### Was berechnet die Fakultät $n!$ #card 
$$n! = 1 \cdot 2 \cdot \dotsc \cdot n$$

#### Wie berechnet man den Binominalkoeffizient "n über k"? #card 
$$
\left( \begin{array}{rrr} 
n\\  
k   
\end{array}\right) = \frac{n!}{k!(n-k)!}
$$

#### Welche Rechnregeln gelten beim Binominialkoeffizienten? #card
$$
\begin{align}
& (a) &&\left( \begin{matrix} n \\ 0 \end{matrix} \right) = 
\left( \begin{matrix} n \\ n \end{matrix} \right) = 1
\text{ und } \left( \begin{matrix} n \\ k \end{matrix} \right) + \left( \begin{matrix} n \\ k-1 \end{matrix} \right) = \left( \begin{matrix} n+1 \\ k \end{matrix} \right) \\
&(b)  &&a^{n+1}- b^{n+1}= (a-b) \sum_{k=0}^{n}a^{n-k}b^{k} \\
&(c) && (a+b)^{n}= \sum_{k=0}^{n} \left( \begin{matrix} n \\ k \end{matrix} \right) a^{n-k}b^{k}
\end{align}
$$

#### Wann ist eine Folge konvergent? #card 
- Die Folge $(a_n)$ ist konvergent gegen $a$, falls für jedes $\varepsilon > 0$ ein $n_{0} \in \mathbb{N}$ existiert mit $|a_{n}- a| < \varepsilon \text{für alle n }\geq n_0$, also in anderen Worten, falls $(a_n)$ einen Grenzwert hat
- Wenn eine Folge konvergent ist, kann sie nur **einen** Grenzwert haben

#### Wann ist eine Folge Divergent? #card 
Die Folge $(a_n)$ ist divergent, wenn sie nicht konvergent ist, also keinen Grenzwert hat

#### Wann ist eine Folge beschränkt? #card 
- Nach oben beschränkt, wenn sie eine obere Schranke besitzt
- Nach unten beschränkt, wenn sie eine untere Schranke besitzt
- Beschränkt, wenn sie sowohl eine obere als auch eine untere Schranke 

#### Wie lauten die Grenzwertsätze? #card 
$\text{Es seien } (a_{n}), (b_{n})\text{ und } (c_{n}) \text{ Folgen in } \mathbb{K}, \text{ dann gilt:}$
$$
\begin{align}
&(a) && \lim_{x\to\infty} a_{n}= a, \text{so gilt } \lim_{x\to\infty} |a_{n|}= |a| \\
&(b) && \text{Gilt } \lim_{x\to\infty} a_{n} = a und \lim_{x\to\infty} b_{n}= b, \text{so folgt:} \\
&&&(1) \lim_{x\to\infty} (a_{n} \pm b_{n}) = a \pm n\\
&&&(2) \lim_{x\to\infty} (\alpha a_{n}) = \alpha a \text{ für alle } \alpha \in \mathbb{K} \\
&&&(3) \lim_{x\to\infty} (a_{n} \cdot b_{b}) = a \cdot b \\
&&&(4) \text{ Ist zusätzlich } b_{n} ≠ 0 \text{ für alle } n  \in \mathbb{N} \text{ und } b ≠ 0, \text{ so ist } \lim_{x\to\infty} a_{n} / b_{n} = a / b \\
&&&\text{Ist } \mathbb{K} = \mathbb{R} \text{ so gilt außerdem:} \\
&(c) && \text{Ist } a_{n}\leq b_{n} \text{ für alle } n \in \mathbb{N} \text{ und} \lim_{x\to\infty} a_{n} = a \text{sowie, } \lim_{x\to\infty} b_{n} = b, \text{so folgt } a\leq b \\
&(d) &&\text{Siehe Sandwich-Theorem}
\end{align}
$$

#### Was ist das Sandwich-Theorem? #card 
Ist $a_{n} \leq c_{n} \leq b_{n}$ für alle $n \in \mathbb{N}$ und sind $(a_n)$ und $(b_{n})$ konvergent mit $\lim_{x\to\infty} a_{n} = \lim_{x\to\infty} b_{n} = a$, so ist auch die Folge $(c_{n})$ konvergent und es gilt $\lim_{x\to\infty} c_{n}= a$ 
![[Pasted image 20230521133256.png]]

#### Was kann man machen, um von Brüchen den Grenzwert herauszufinden? #card 
Die größte Potenz ziehen:
$$
\begin{align}
&\text{Im folgendem Kürzen wir um } n^{2}\\ 
&a_{n} = \frac{n^{2}+ 2n + 3}{n^{2} + 3} = \frac{1 + \frac{2}{n} + \frac{3}{n^{2}}}{1+ \frac{3}{n^{2}}} \to \frac{1+0+0}{1+0} = 1 (n\to\infty)
\end{align}
$$

#### Wichtige Beispiele für Konvergente Folgen #card 
1)  Ist $(a_{n})$ eine konvergente Folge in $\mathbb{R}$ mit Grenzwert $a$, und gilt $a_{n} \geq 0$ für alle $n \in \mathbb{N}$, so ist auch für jedes $p \in \mathbb{N}^*$ auch $\lim_{x\to\infty} \sqrt[p]{a_{n}} = \sqrt[p]{a}$
2) Die Folge $(q^{n})_{n \in \mathbb{N}}$ mit $q \in \mathbb{R}$ konvergiert genau dann, wenn $q \in (-1, 1]$ ist und es gilt:
   $$\lim_{x\to\infty} q^{n} = \left\{\begin{array}{ll}1 &  \text{falls }q = 1 \\0 & \, \textrm{falls } -1 < q <1 \\\end{array}\right.$$
Ist $q \in \mathbb{C}$ mit $|q| < 1$, soi gilt ebenfalls $\lim_{n\to\infty} q^{n} = 0$
3) $\lim_{n\to\infty} \sqrt[n]{c} = 1$ für jedes $c \in \mathbb{R}_{+}$ 
4) $\lim_{n\to\infty} \sqrt[n]{n}$ = 1
5) Die Folge (des Exponentillen Wachstums) $$a_{n} := \left(1+\frac{1}{n}\right)^{n}, \ \ \ \ \ \ \ \ n \geq 1, $$
   Ist konvergent. Ihr Grenzwert $$\text{e} := \lim_{n \to \infty} \left( 1 + \frac{1}{n}\right)^{n}$$
   heißt *Eulersche Zahl* 
$$$$
#### Was tun bei einer Differenz von Wurzeln? #card 
Das 3. Binom arbeiten lassen:
$$
\begin{align}
&0 \leq \sqrt{n+1} + \sqrt{n} = \frac{(\sqrt{n+1}-\sqrt{n})(\sqrt{n+1}+\sqrt{n})}{\sqrt{n+1} +\sqrt{n}} = \frac{(n+1)-n}{\sqrt{n+1} +\sqrt{n}} \\
& \frac{1}{\sqrt{n+1}+\sqrt{n}} \leq \frac{1}{2\sqrt{n}}=\frac{1}{2}\sqrt{\frac{1}{n}}
\end{align}
$$

#### Wie lautet die geometrische Summenformel? #card 
Für $q ≠ 1$ gilt:
$$\sum_{k=1}^{n} q^{k} = \frac{1-q^{n+1}}{1-q}$$

#### Wann ist eine reele Folge $(a_{n})$ *monoton wachsend*? #card 
Wenn $a_{n+1} \geq a_n$ für alle $n \in \mathbb{N}$ gilt

#### Wann ist eine reele Folge $(a_{n})$ *monoton fallend*? #card
Wenn $a_{n+1} \leq a_n$ für alle $n \in \mathbb{N}$ gilt

#### Wann ist eine reele Folge *monoton*? #card 
Wenn sie *monoton fallend* oder *monoton wachsend* ist

#### Was ist eine *Cauchy-Folge*? #card 
Eine Folge $(a_{n})$ für welche gilt:
	Für jedes $\varepsilon > 0$ existiert ein Index $n_{0} \in \mathbb{N}$, so dass $$|a_{n} - a_{m} < \varepsilon| \ \ \ \text{ für alle }n, m \geq n_{0}$$
	Hinweis: Jede konvergente Folge ist eine Cauchy-Folge

#### Welche Konvergenzkriterien gibt es? #card 
- Monotonie-Kriterium
- 

#### Wie funktioniert das Monotonie-Kriterium? #card 
Ist die reele Folge $(a_{n})$ nach oben (bzw. unten) beschränkt, und monoton wachsend (bzw. fallend, so ist $(a_{n})$ konvergent und es gilt: $$\lim_{n\to\infty} a_{n} = \sup_{n \in \mathbb{M}}a_{n} \ \ \ \ \ (\text{bzw.} \ \ \lim_{n \to \infty}a_{n}= \inf_{n \in \mathbb{N}}a_n)$$

#### Was ist ein *Häufungswert*?
Sei $(a_{n})$ eine Folge in $\mathbb{K}$. Ein $a \in \mathbb{K}$ heißt *Häufungswert der Folge*, falls für jedes $\varepsilon > 0$ die Menge $\{ n \in \mathbb{N}: |a_{n} - a| < \varepsilon \}$ unendlich viele Elemente hat.
Hinweis: Ein Grenzwert einer konvergenten Folge ist ein *Häufungspunkt* derselben, denn für jedes $\varepsilon$