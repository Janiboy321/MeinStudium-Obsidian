---
cards-deck: Mathe II
---


#### Was ist ein angeordneter Körper? #card
$\text{Ein Körper K mit einer Totalorndung } \leq \text{, für die gilt:}$
- $\forall a,b,c \in K: a \leq b \Rightarrow a+b \leq b+c$ und
- $\forall a,b,c \in K: (a \leq b \text{ und } 0 \leq c) \Rightarrow ac \leq bc$
^1684683802439

#### Wann ist eine Teilmenge $M \subseteq \mathbb{R}$ nach oben (unten) beschränkt? #card 
$\text{Wenn sie eine obere (untere) Schranke besitzt}$
^1684683802441

#### Wann ist eine Teilmenge $M \subseteq \mathbb{R}$ beschränkt? #card 
$\text{Wenn sie nach unten bzw. oben beschränkt ist}$
^1684683802442

#### Was ist die Betragsfunktion? #card
$\text{Die Funktion } | \cdot |: \mathbb{R} \rightarrow \mathbb{R} \text{ mit }$
$$|x| := \left\{
\begin{array}{ll}
x &  \text{ falls }x \geq 0 \\
-x & \, \textrm{falls } x < 0 \\
\end{array}
\right.$$
$\text{heißt Betragsfunktion und } |x| \text{ heißt Betrag von } x$
^1684683802443

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
^1684683802444

#### Wie lauten die Intervallkonvertionen? #card 
- $(a, b) := \{x \in \mathbb{R} : a < x < b \} \Rightarrow$ Offenes Intervall
- $[a, b] := \{x \in \mathbb{R} : a \leq x \leq b \} \Rightarrow$ Geschlossenes Intervall
^1684683802445

#### Wie vereinfacht man $x^n$, $x^{-n}$ sowie $x^0$? #card
^1684683802446 
- $x^{n}:= x \cdot x \cdot \dotsc \cdot x$
- $x^{-n} := \frac{1}{x^{n}} \text{, falls }x ≠ 0$
- $x^{0}=1$
^1684683802447

#### Seien $q \in \mathbb{Q}$ und $m, p \in \mathbb{Z}$ sowie $n, r \in \mathbb{N}^*$, so dass $q = m / n = p / r$. Dann gilt für jedes $x \in \mathbb{R}_+$: #card 
$$(\sqrt[n]{x})^{m}= (\sqrt[r]{x})^p$$
^1684683802448

#### Wie lauten die Potenzrechenregeln? #card 
$$
\begin{flalign}{}
 &\bullet x^{p}x^{q} = x^{p+q} &\bullet \frac{x^{p}}{x^{q}} = x^{p-q} \\ \\
 &\bullet x^{p}y^{p} = (xy)^{p} &\bullet \frac{x^{p}}{y^{p}} = (\frac{x}{y})^{p} \\ \\
 &\bullet(x^{p})^{q} = x^{pq}
\end{flalign}
$$
^1684683802449

#### Was berechnet die Fakultät $n!$ #card 
$$n! = 1 \cdot 2 \cdot \dotsc \cdot n$$
^1684683802450

#### Wie berechnet man den Binominalkoeffizient "n über k"? #card 
$$
\left( \begin{array}{rrr} 
n\\  
k   
\end{array}\right) = \frac{n!}{k!(n-k)!}
$$
^1684683802451

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
^1684683802452

#### Wann ist eine Folge konvergent? #card 
- Die Folge $(a_n)$ ist konvergent gegen $a$, falls für jedes $\varepsilon > 0$ ein $n_{0} \in \mathbb{N}$ existiert mit $|a_{n}- a| < \varepsilon \text{für alle n }\geq n_0$, also in anderen Worten, falls $(a_n)$ einen Grenzwert hat
- Wenn eine Folge konvergent ist, kann sie nur **einen** Grenzwert haben
^1684683802453

#### Wann ist eine Folge Divergent? #card 
Die Folge $(a_n)$ ist divergent, wenn sie nicht konvergent ist, also keinen Grenzwert hat
^1684683802454

#### Wann ist eine Folge beschränkt? #card 
- Nach oben beschränkt, wenn sie eine obere Schranke besitzt
- Nach unten beschränkt, wenn sie eine untere Schranke besitzt
- Beschränkt, wenn sie sowohl eine obere als auch eine untere Schranke 
^1684683802455

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
^1684683802456

#### Was ist das Sandwich-Theorem? #card 
Ist $a_{n} \leq c_{n} \leq b_{n}$ für alle $n \in \mathbb{N}$ und sind $(a_n)$ und $(b_{n})$ konvergent mit $\lim_{x\to\infty} a_{n} = \lim_{x\to\infty} b_{n} = a$, so ist auch die Folge $(c_{n})$ konvergent und es gilt $\lim_{x\to\infty} c_{n}= a$ 
![[Pasted image 20230521133256.png]]
^1684683802457

#### Was kann man machen, um von Brüchen den Grenzwert herauszufinden? #card 
Die größte Potenz ziehen:
$$
\begin{align}
&\text{Im folgendem Kürzen wir um } n^{2}\\ 
&a_{n} = \frac{n^{2}+ 2n + 3}{n^{2} + 3} = \frac{1 + \frac{2}{n} + \frac{3}{n^{2}}}{1+ \frac{3}{n^{2}}} \to \frac{1+0+0}{1+0} = 1 (n\to\infty)
\end{align}
$$
^1684683802458

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
^1684683802459

#### Wie lautet die geometrische Summenformel? #card 
Für $q ≠ 1$ gilt:
$$\sum_{k=1}^{n} q^{k} = \frac{1-q^{n+1}}{1-q}$$
^1684683802460

#### Wann ist eine reele Folge $(a_{n})$ *monoton wachsend*? #card 
Wenn $a_{n+1} \geq a_n$ für alle $n \in \mathbb{N}$ gilt
^1684683802461

#### Wann ist eine reele Folge $(a_{n})$ *monoton fallend*? #card
Wenn $a_{n+1} \leq a_n$ für alle $n \in \mathbb{N}$ gilt
^1684683802462

#### Wann ist eine reele Folge *monoton*? #card 
Wenn sie *monoton fallend* oder *monoton wachsend* ist
^1684683802463

#### Was ist eine *Cauchy-Folge*? #card 
Eine Folge $(a_{n})$ für welche gilt:
	Für jedes $\varepsilon > 0$ existiert ein Index $n_{0} \in \mathbb{N}$, so dass $$|a_{n} - a_{m} < \varepsilon| \ \ \ \text{ für alle }n, m \geq n_{0}$$
	Hinweis: Jede konvergente Folge ist eine Cauchy-Folge
^1684683802464

#### Welche Konvergenzkriterien gibt es? #card 
- Monotonie-Kriterium
- Cauchy-Kriterium
- Majoranten-/Minorantenkriterium
- Wurzel-/Quotiontenkriterium
^1684683802465

#### Wie funktioniert das Monotonie-Kriterium? #card 
- Für Folgen:
	- Ist die reele Folge $(a_{n})$ nach oben (bzw. unten) beschränkt, und monoton wachsend (bzw. fallend, so ist $(a_{n})$ konvergent und es gilt: $$\lim_{n\to\infty} a_{n} = \sup_{n \in \mathbb{M}}a_{n} \ \ \ \ \ (\text{bzw.} \ \ \lim_{n \to \infty}a_{n}= \inf_{n \in \mathbb{N}}a_n)$$
	- Für Reihen:
	- Ist $a_{n} \geq 0$ für alle $n \in \mathbb{N}$ und $(s_{k})_{k \in \mathbb{N}}$ nach oben beschränkt, so ist $\sum\limits_{n = 0}^{\infty} a_{n}$ konvergent.
 
#### Was ist ein *Häufungswert*? #card 
Sei $(a_{n})$ eine Folge in $\mathbb{K}$. Ein $a \in \mathbb{K}$ heißt *Häufungswert der Folge*, falls für jedes $\varepsilon > 0$ die Menge $\{ n \in \mathbb{N}: |a_{n} - a| < \varepsilon \}$ unendlich viele Elemente hat.
![[Screenshot 2023-05-21 at 15.23.53.png]]
Hinweis: Ein Grenzwert einer konvergenten Folge ist ein *Häufungspunkt* derselben.
^1684683802466

#### Was ist eine *Teilfolge*? #card 
Sei $(a_{n})$ eine Folge in $\mathbb{K}$. Ist $\{n_{1}, n_{2}, n_{3}, \dotsc\} \subseteq \mathbb{N}$ eine unendliche Menge von Indizes mit $n_{1} < n_{2} < n_{3} < \dotsc$, so heißt die Folge $(a_{n_{k}}) _{k \in \mathbb{N}}$ eine *Teilfolge von $(a_{n})$* 
Hinweis: Beispielsweise ist $(a_{0}, a_{2}, a_{4}, a_{6}, \dotsc)$ die Teilfolge von Folgegliedern mit geradem Index.
^1684683802467

#### Welche Regeln gibt es für Teilfolgen und Häufungswerte? #card 
1. Ein $\alpha \in \mathbb{K}$ ist genau dann ein Häufungswert von $(a_{n})$, wenn eine Teilfolge $(a_{n_{k}})$ von $(a_{n})$ existiert, die gegen $\alpha$ konvergiert
2. Ist $(a_{n})$ konvergent mit Grenzwert a, so konvergiert auch jede Teilfolge von $(a_{n})$ gegen $a$ 
3. Ist $(a_{n})$ konvergent, so hat $(a_{n})$ genau einen Häufungswert, nämlich den Grenzwert $\lim_{n \to \infty} a_{n}$   
^1684683802468

#### Was ist eine Reihe? #card 
- Sei $(a_{n})$ eine Folge in $\mathbb{K}$. Dann heißt $\sum_{n=0}^{\infty}an = a_{0}+a_{1}+a_{2}+a_{3}+ \dotsc$ *die Reihe über* $(a_{n})$. 
- Für jedes $k \in \mathbb{N}$ heißt dann $s_{k} := \sum_{n=0}^{\infty} a_{n}$ die *$k$-te Teilsumme* bzw. *Partialsumme der Reihe*  
- Ist die Folge $(s_{k})_{k\in\mathbb{N}}$ konvergent, so nennen wir die Reihe konvergent mit dem Reihenwert $\sum\limits_{n=0}^{\infty}a_{n}= \lim_{k\to\infty} s_{k} = \lim_{k\to\infty} \sum\limits_{n=0}^{k}a_{n}$. Ist $(s_{k})$ divergent, so nennen wir auch die Reihe divergent
^1684683802469

#### Welche vier wichtigen Reihen gibt es? #card
1. Geometrische Reihe
	$\displaystyle\sum_{n=0}^{\infty} q^n = \frac{1}{1-q}$
^1684683802470

2. Harmonische Reihe
	$\displaystyle\sum_{n=0}^{\infty} \frac{1}{n}$ 

3. Exponential Reihe
	$\displaystyle\sum_{n=0}^{\infty} \frac{z^n}{n!}$

4. Es gibt eine Reihe, welche wichtig ist, aber nicht wichtig genug um einen Namen zu bekommen. Sie lautet wie folgt $$\sum\limits_{n=1}^{\infty} \frac{1}{n(n+1)} = \frac{1}{2} + \frac{1}{6} + \frac{1}{12} + \frac{1}{20} + \frac{1}{30} + \dotsc$$
   *Mit einer kompliziert aussehenden Umrechnung (Siehe Skript 5.5.2 b), findet man heraus, dass $\lim_{k\to\infty} *\sum\limits_{n=1}^{\infty} \frac{1}{n(n+1)} = 1$* 

#### Wann ist eine Reihe eine *Nullfolge*? #card 
Ist $\sum\limits_{n=0}^{\infty} a_{n}$ eine konvergente Reihe in $\mathbb{K}$, so ist $(a_{n})$ eine Nullfolge in $\mathbb{K}$
^1684683802471

#### Wie funktioniert das Leibnitz-Kriterium? #card 
Sei $(a_{n})$ eine monoton fallende Folge in $\mathbb{R}$ mit $\lim_{n\to\infty} a_{n} = 0$. Dann ist die Reihe $\sum\limits_{n=0}^{\infty}(-1)^{n}a_{n}$ konvergent.
^1684683802472

#### Wann ist eine Reihe absolut konvergent? #card 
Eine Reihe $\sum\limits_{n = 0}^{\infty} a_{n}$ in $\mathbb{K}$ heißt absolut konvergent, wenn die Reihe $\sum\limits_{n = 0}^{\infty} |a_{n}|$ in $\mathbb{K}$ konvergiert
^1684683802473

#### Wie lautet die verallgemeinerte Dreiecksungleichung? #card 
$$\Biggl|\sum\limits_{n = 0}^{\infty} |a_{n}|\Biggr| \leq \sum\limits_{n =0}^{\infty} |a_{n}|$$
^1684683802474

#### Wann sollte man daran denken, die Dreiecksungleichung anzuwenden? #card 
Wenn man etwas über den Betrag der Summer herausfinden will und was über $\sum\limits a_{n}$ 
^1684683802475

#### Wie funktioniert das Majoranten und das Minoranten Kriterium? #card 
Hat man eine Reihe, von welchen wir wissen, dass sie divergieren, bzw. konvergieren, können wir andere Reihen mit ihnen vergleichen und somit auf die divergenz bzw. konvergent der Reihe schließen:
- Majorantenkriterium: Ist $|a_{n}| \leq b_{n}$ für alle $n \geq n_{0}$ und konvergiert die Reihe $\sum\limits_{n = 0}^{\infty} b_{n}$, so ist $\sum\limits_{n = 0}^{\infty} a_{n}$ absolut konvergent
- Minorantenkriterium: Ist $a_{n} \geq b_{n} \geq 0$ für alle $n \geq n_{0}$ und divergiert die Reihe $\sum\limits_{n = 0}^{\infty} b_{n}$, so divergiert auch die Reihe $\sum\limits_{n = 0}^{\infty} a_{n}$
Hinweis: Die Vergleichsfolge $(b_{n})$ heißt dann a) konvergente Majorante oder b) divergente Minorante
^1684683802476

#### Wann ist die Reihe $\sum_{n=1}^{\infty} \frac{1}{n^{\alpha}}$ konvergent? #card 
Wenn $\alpha > 1$
^1684683802477

#### Wie funktioniert das Wurzelkriterium? #card 
Existiert der Grenzwert $\lim_{n \to \infty} \sqrt[n]{|a_{n}|}$ so ist die Reihe:
- absolut konvergent, wenn $\lim_{n \to \infty} \sqrt[n]{|a_{n}|}< 1$ 
- divergent, wenn $\lim_{n \to \infty} \sqrt[n]{|a_{n}|} > 1$
^1684683802478

#### Wie funktioniert das Quotientenkriterium? #card 
Ist $a_{n} ≠ 0$ für alle $n \in \mathbb{N}$ und existiert der Grenzwert $\lim_{n \to \infty} |a_{n+1} / a_{n}|$, so ist die Reihe:    
- absolut konvergent, wenn $\lim_{n \to \infty} \frac{|a_{n+1}|}{a_{n}} < 1$
- divergent, wenn $\lim_{n \to \infty} \frac{|a_{n+1}|}{a_{n}} > 1$
^1684683802479

#### Welches kriterium sollte man verwenden, wenn wir Fakultäten in einer Reihe haben? #card 
Das Quotientenkriterium
Beispiel: ![[Screenshot 2023-05-21 at 17.29.54.png]] 
^1684683802480

#### Wie lautet die Cauchy-Produktformel? #card 
Seien $\sum\limits_{n = 0}^{\infty} a_{n}$ und $\sum\limits_{n = 0}^{\infty} b_{n}$ zwei absolut konvergente Reihen in $\mathbb{K}$, dann ist auch die Reihe $\sum\limits_{n = 0}^{\infty} a_{n} \cdot \sum\limits_{n = 0}^{\infty} b_{n}$ absolut konvergent und es gilt für die Reihenwerte: $$\sum\limits_{n=0}^{\infty} \sum\limits_{k=0}^{n} a_{k}b_{n-k} = \left( \sum\limits_{n = 0}^{\infty} a_{n} \right) \cdot \left( \sum\limits_{n = 0}^{\infty} b_{n} \right)$$
^1684683802481

#### Wie lautet die Funktionalgleichung der Exponentialfunktion? #card 
$E(z+w) = E(z)E(w)$ aka. $E^{z+w} = E^{z} \cdot E^{w}$ 
^1684683802482

#### Welche Regeln gelten für die Konvergenz im normierten Raum? #card 
Meistens die gleichen, wie für die normale Konvergenz, nur dass die Betragsstriche durch Normen ausgetauscht werden.
Also: Cauchy-Folge, Konvergenz / Divergenz, Häufungswert und Teilmenge
^1685188652789

#### Wann ist eine Menge $M \subseteq V$ beschränkt? #card 
Falls es ein $C \geq 0$ gibt, so dass $||x||_{V} \leq C$ für alle $x \in M$ gilt
^1685188652798

#### Wann ist ein Vektor konvergent und welchen Grenzwert hat er dann?
Es sei $(a_{n})_{n \in \mathbb{N}} = (\left(a_{n,1} a_{n, 2}, \dotsc, a_{n, d} \right) ^{T})_{n \in \mathbb{N}}$ eine Folge in $\mathbb{R}^d$. Dann ist $(a_{n})$  in $\mathbb{R}^{d}$ genau dann konvergent, wenn für jedes $j \in \{1, 2, \dotsc, d\}$ die Koordinatenfolge $(a_{n,j})_{n \in \mathbb{N}}$ in $\mathbb{R}$ konvergent. In diesem Fall ist 
$$
\lim_{n \to \infty} 
\begin{pmatrix} a_{n, 1} \\ a_{n, 2} \\ \vdots \\ a_{n, d} 
\end{pmatrix} =
\begin{pmatrix} \lim_{n \to \infty} a_{n, 1} \\ \lim_{n \to \infty} a_{n, 2} \\ \vdots \\ \lim_{n \to \infty} a_{n, d} 
\end{pmatrix}
$$

#### Inwiefern unterscheidet sich in einem endlich-dimensionalem Raum die Konvergenz einer Folge unter Verwendung verschiedener Normen? #card 
Garnich, egal welche Norm man verwendet, man bekommt immer das gleiche Resultat
^1685188652802

#### Wann ist eine Menge in einem endlich-dimensionalen Raum **offen**? #card 
Eine Menge $M \subseteq V$ heißt offen, falls es für jeden Punkt $x_{0}\in M$ einen Radius $r > 0$ gibt, so dass $B_{r}(x_{0}) \subseteq M$ gilt.
*In anderen Worten: Eine Kugel ist offen, wenn es für jeden Punkt innerhalb der Kugel einen Radius $r > 0$ gibt, sodass die daraus resultierende Kugel innerhalb der Menge $M$ liegt* 
*Oder: Eine Menge ist offen, wenn alle ihre Punkte innere Punkte sind*
**Hinweis: $\text{Menge ist offen } \nLeftrightarrow \text{ Menge ist abgeschlossen}$** 
^1685188652805

#### #### Wann heißt eine Menge in einem endlich-dimensionalen Raum **abgeschlossen**? #card 
Eine Menge $M \subseteq V$ heißt offen, wenn die Menge $M^{c}= V \ \textbackslash \ M$ offen ist
*In anderen Worten: Die Menge $M \in V$ ist abgeschlossen, wenn ihr Komplement offen ist*
^1685188652809

#### Wann ist ein Punkt $x_{0} \in M$ ein innerer Punkt von $M$? #card
^1685188652815 
Es sei $M \subseteq V$. Ein Punkt $x_{0} \in M$ heißt innerer Punkt von $M$, falls es ein $r > 0$ gibt, so dass $B_{r}(x_{0}) \subseteq M$ ist. Man nennt $$M° := \{ x \in M: x \text{ innerer Punkt von } M\}$$das **Innere von $M$**
^1685188652818

#### Wann ist eine Teilmenge $M$ von $V$ abgeschlossen? #card
Wenn für jede Folge in $M$, die in $V$ konvergiert, der Grenzwert ein Element aus M ist
^1685188652821

#### Wann ist eine Teilmenge $M \subseteq V$, mit $V$ endlich-dimensionaler, normierter $\mathbb{R}-$Vektorraum, kompakt? #card
Wenn die Menge $M$ abgeschlossen und beschränkt ist
^1685188652824

#### Sei $(V, || \cdot ||_{V})$ ein endlich-dimensionaler, normierter Raum und $M \subseteq V$. Wann besitzt jede Folge in M eine konvergente Teilfolge, mit Grenzwert in M? #card 
Wenn M kompakt ist
^1685188652828

#### Wann besitzt jede beschränkte Folge in $V$ mindestens einen Häufungswert? #card
Wenn $(V, ||\cdot||_{V})$ ein endlich-dimensionler normierter Raum ist.
*In anderen Worten: In einer beschränkten Teilmenge des $\mathbb{R}^d$ ist nicht genug Platz, als dass man mit einer Folge so wild herumspringen kann, dass sie sich nirgends häuft. Anders gesagt: Wenn man unendlich viele Punkte in einer beschränkten Menge unterbringen will, so müssen die irgendwo klumpen*
^1685188652831

#### Wann heißt ein normierter $\mathbb{R}-$Vektorraum $(V, ||\cdot||_{V})$ vollständig bzw. Banachraum? #card 
Wenn jede Cauchy-Folge in $V$ konvergiert
^1685188652834

#### #### Wann heißt ein normierter $\mathbb{R}-$Vektorraum $(V, ||\cdot||_{V})$ Hilbertraum? #card
^1685188652836 
Wenn die Norm $||\cdot||_{V}$ durch ein Skalarprodukt auf V indiziert wird
^1685188652840

#### Welche Rechenregeln gelten in Banachräumen? #card 
1. $(a_{n}) \text{ konvergent } \Leftrightarrow (a_{n}) \text{ Cauchy-Folge}$
2. $\text{Jede absolut konvergente Reihe konvergiert}$
3. $\text{Majorantenkriterium, Wurelkriterium und Qutotientenkriterium}$
^1685188652844

#### Sei $(V, ||\cdot||_V)$ ein Banachraum, $M \subseteq V$ abgeschlossen und $f: M \rightarrow M$ eine Funktion. Weiter existiert ein $q \in (0,1)$ so dass $$||f(x) - f(y)||_{V} \leq ||x-y||_{V} \ \ \ \ \text{ für alle x, y} \in M$$gilt. Welche Aussagen gelten jetzt? #card 
1. Es gibt genau ein $v \in M$ mit $f(v) = v$, f hat also genau einen Fixpunkt in M
2. ![[Pasted image 20230527135720.png]]

#### Sei $D \subseteq \mathbb{R}$ ein Menge, $f: D \rightarrow \mathbb{R}$ eine Funktion und $x_{0} \in \mathbb{R}$, wann nennen wir $x_{0}$ einen Häufungspunkt in $D$? #card 
Falls es eine Folge $(a_{n})$ in $D$ mit $a_{n} ≠ x_{0}$ für alle $n \in \mathbb{N}$ gibt, , die gegen $x_{0}$ konvergiert

#### Sei $D \subseteq \mathbb{R}$ ein Menge, $f: D \rightarrow \mathbb{R}$ eine Funktion und $x_{0} \in \mathbb{R}$, was gilt, wenn $x_{0}$ ein Häufungspunkt von $D$ ist? #card 
Wenn für jede Folge $(a_{n})$ in $D$, die gegen $x_{0}$ konvergiert und für die $a_{n} ≠ x_0$ für alle $n \in \mathbb{N}$ gilt, die Folgen $f(a_{n})$ gegen y konvergiert. Wir schreiben dafür $\lim_{x \to x_{0}} f(x) = y$ 

#### Sei $D \subseteq \mathbb{R}$ ein Menge, $f: D \rightarrow \mathbb{R}$ eine Funktion und $x_{0} \in \mathbb{R}$, was gilt, wenn $x_{0}$ ein Häufungspunkt von $D_{+} := \{x \in D: x > x_{0}\}$ ist? #card 
$f$ hat für $x$ gegen $x_0$ den **rechtsseitigen** Grenzwert $y$, wenn für jede Folge $(a_{n})$ in $D_{+}$, die gegen $x_0$ konvergiert, die Folge $(f(a_{n}))$ gegen $y$ konvergiert. Wir schreiben $\lim_{x \to x_{0}+} f(x) = y$  

#### Sei $D \subseteq \mathbb{R}$ ein Menge, $f: D \rightarrow \mathbb{R}$ eine Funktion und $x_{0} \in \mathbb{R}$, was gilt, wenn $x_{0}$ ein Häufungspunkt von $D_{-} := \{x \in D: x > x_{0}\}$ ist? #card 
$f$ hat für $x$ gegen $x_0$ den **linksseitigen** Grenzwert $y$, wenn für *jede Folge* $(a_{n})$ in $D_{-}$, die gegen $x_0$ konvergiert, die Folge $(f(a_{n}))$ gegen $y$ konvergiert. Wir schreiben $\lim_{x \to x_{0}-} f(x) = y$  
*Bemerkung:* Existieren $\lim_{x \to x_{0}-} f(x)$ und $\lim_{x \to x_{0}+} f(x)$ und sind beide Werte gleich, so existiert auch $\lim_{x \to x_{0}} f(x)$ und es gilt $$\lim_{x \to x_{0}-} f(x) = \lim_{x \to x_{0}+} f(x) = \lim_{x \to x_{0}} f(x)$$
#### Es sei $D \subseteq \mathbb{R}$ und $x_{0}$ ein Häufungspunkt von $D$. Desweiteren seien drei Funktionen $f, g, h:D \to \mathbb{R}$ gegeben, sodass die Grenzwerte $\lim_{x \to x_{0}} f(x)$ und $\lim_{x \to x_{0}} g(x)$ existieren. Dann gilt: #card 
1) Die Grenzwerte für x gegen $x_{0}$ von $f+g$, $fg$ und $|f|$ existieren und es gilt $$
\begin{align}
&\lim_{x \to x_{0}}(f(x)+g(x)) = \lim_{x \to x_{0}} f(x) + \lim_{x \to x_{0}} g(x) \\
&\lim_{x \to x_{0}} (f(x)g(x)) = \lim_{x \to x_{0}} f(x) \cdot \lim_{x \to x_{0}} g(x) \text{ und} \\
&\lim_{x \to x_{0}}|f(x)| = |\lim_{x \to x_{0}}f(x)|
\end{align}
$$
2) Gilt $f(x) \leq g(x)$ für alle $x \in D \ \backslash  \{x_0\}$, so ist $\lim_{x \to x_{0}} f(x) \leq \lim_{x \to x_{0}} g(x)$
3) Ist $\lim_{x \to x_{0}} f(x) = \lim_{x \to x_{0}} g(x)$ und gilt $$f(x) \leq h(x) \leq g(x) \ \ \ \text{für alle } x \in D \ \backslash \{x_0\}$$ so gilt auch $\lim_{x \to x_{0}} h(x) = \lim_{x \to x_{0}} f(x) = \lim_{x \to x_{0}} g(x)$.
4) Ist $y := \lim_{x \to x_{0}} g(x) ≠ 0$, so existiert ein $\delta > 0$, so dass $|g(x)| \geq |y|/2$ für alle $x \in (D \cap (x_{0}- \delta, x_{0}+\delta)) \backslash \{x_{0}\}$ ist. Wir können also die Funktion $$\frac{f}{g}: (D \cap (x_{0}- \delta, x_{0}+\delta)) \backslash \{x_{0}\} \to \mathbb{R} \text{ mit } \frac{f}{g}(x):= \frac{f(x)}{g(x)}$$ definieren. Für diese existiert dann der Limes für $x$ gegen $x_{0}$ mit $\lim_{x \to x_{0}} \frac{f(x)}{g(x)} = \frac{\lim_{x \to x_{0}}f(x)} {\lim_{x \to x_{0}}g(x)}$

#### Seien $D \subseteq \mathbb{R}, f: D \to \mathbb{R}$ eine Funktion und $x_0$ ein Häufungspunkt von D. Was schreiben wir, wenn für jede folge $(a_{n})$ in $D$, die gegen $x_{0}$ konvergiert und für alle $n \in \mathbb{N}$ gilt, dass die Folge $(f(a_{n}))$ bestimmt gegen $\infty$ (bzw. $-\infty$) divergiert? #card 
$$\lim_{x \to x_{0}} f(x) = \infty \text{ (bzw. }  \lim_{x \to x_{0}} f(x) = -\infty)$$
#### Seien $D \subseteq \mathbb{R}$ nicht nach oben (bzw. unten) beschränkt und $f: D \to \mathbb{R}$ eine Funktion und $y \in \mathbb{R} \cup \{ \infty, -\infty \}$. Was sagen wir dann, wenn für jede Folge $(a_{n})$ in D, die bestimmt gegen $\infty$ (bzw. $-\infty$) divergiert, $\lim_{n \to \infty} f(a_{n}) = y$ gilt? #card 
$$\lim_{x \to \infty}f(x) = y \ \ \ \ (\text{bzw.} \lim_{x \to -\infty}f(x) = y)$$

#### Es sei $D \subseteq \mathbb{R}$ und $x_{0} \in D$. Wann heißt eine Funktion $f: D \to \mathbb{R}$ stetig in $x_{0}$? #card 
Falls für jede Folge $(a_{n})$ in D, die gegen $x_{0}$ konvergiert, auch die Folge $(f(a_{n}))$ konvergiert und $\lim_{n \to \infty} f(a_{n}) = f(x_{0})$ 

#### Es sei $D \subseteq \mathbb{R}$ und $x_{0} \in D$ wann heißt eine Funktion $f:D\to \mathbb{R}$ stetig auf $D$? #card 
Wenn $f$ in jedem Punkt $x_{0} \in D$ stetig ist.

#### Sei $D \subseteq \mathbb{R}$ und $f:D \to \mathbb{R}$ eine Funktion. Wenn $x_{0}\in D$ ein Häufungspunkt von D ist, wann ist $f$ in $x_{0}$ stetig? #card 
Genau dann wenn $\lim_{x \to x_{0}} f(x) = f(x_{0})$ gilt.
*Bemerkung:* Stetigkeit ist wie folgt am einprägsamsten: Damit $f$ in $x_{0}$ stetig ist, muss folgendes gelten $$\lim_{x \to x_{0}}f(x) = f(x_{0})= f(\lim_{x \to x_{0}}x)$$ Stetigkeit bedeutet also, dass man den Grenzübergang mit der Funktionsauswertung vertauschen kann

#### Sei $D \in \mathbb{R}$ und $f, g:D \to \mathbb{R}$ seien stetig in $x_{0} \in D$. Was gilt dann? #card
Die Funktionen $f+g$, $fg$ und $|f|$ sind stetig in $x_{0}$
Ist $x_{0} \in D^* := \{x \in D:g(x) ≠ 0\}$, so ist die Funktion $\frac{f}{g}: D^{*} \to \mathbb{R}$ stetig in x_0 

#### Seien $D, E \in \mathbb{R}$ und $f:D \to E$, sowie $g:E\to \mathbb{R}$ Funktionen. Was gilt, wenn $f$ stetig in $x_{0}\in D$ und $g$ stetig in $f(x_{0})$ ist? #card 
Dann ist die Verkettung $g \circ f:D \to \mathbb{R}$ auch stetig

#### Sei $D \subseteq \mathbb{R}$. Wann heißt eine Funktion $f:D \to \mathbb{R}$ monoton wachsend? #card 
Wenn für alle $x, y \in D$ gilt $x \leq y \Rightarrow f(x) \leq f(y)$

#### Sei $D \subseteq \mathbb{R}$. Wann heißt eine Funktion $f:D \to \mathbb{R}$ monoton fallend? #card 
Wenn für alle $x, y \in D$ gilt $x \leq y \Rightarrow f(x) \geq f(y)$

#### Sei $D \subseteq \mathbb{R}$. Wann heißt eine Funktion $f:D \to \mathbb{R}$ streng monoton wachsend? #card 
Wenn für alle $x, y \in D$ gilt $x < y \Rightarrow f(x) < f(y)$

#### Sei $D \subseteq \mathbb{R}$. Wann heißt eine Funktion $f:D \to \mathbb{R}$ streng monoton fallend? #card 
Wenn für alle $x, y \in D$ gilt $x > y \Rightarrow f(x) > f(y)$

#### Sei $D \subseteq \mathbb{R}$. Wann heißt eine Funktion $f:D \to \mathbb{R}$ (streng) monoton? #card
Wenn sie (streng) monoton wachsend oder (streng) monoton fallend ist

#### Was gilt, wenn $I \subseteq \mathbb{R}$ ein Intervall und $f \in C(I)$ streng monoton ist? #card 
- $f:I \to f(I)$ ist bijektiv
- $f(I)$ ist ein Intervall
- $f^{-1}:f(I) \to I$ ist stetig auf $f(I)$ und streng monoton

#### Wann ist eine Funktion $f:D \to \mathbb{R}$, laut der $\varepsilon$-$\delta$-Regel, in $x_{0}$ stetig? #card 
Wenn es für jedes $\varepsilon > 0$ ein $\delta > 0$ gibt, so dass $$|f(x) - f(x_{0})| < \varepsilon \ \ \ \ \ \text{für alle } x \in D \text{ mit } |x - x_{0}| < \delta$$ gilt

#### Sei $D \subseteq \mathbb{R}$. Wann heißt eine Funktion $f : D \to \mathbb{R}$ Lipschitzstetig? #card 
Falls es ein $L > 0$ gibt, mit $|f(x)-f(y)| \leq L|x - y|$ für alle $x, y \in D$
*Bemerkung:* Diese Aussage ist nicht Umkehrbar

#### Was sagt der Zwischenwertsatz aus? #card 
Seien $a, b \in \mathbb{R}$ mit $a < b$ gegeben und $f \in C([a, b])$. Ist $y_{0}$ eine reele Zahl zwischen $f(a)$ und $f(b)$, so gibt es ein $x_{0} \in [a, b]$ mit $f(x_{0}) = y_{0}$  
*Folgerung:* Seien $a, b \in \mathbb{R}$ mit $a<b$ und $f \in C([a, b])$ erfülle $f(a)f(b) < 0$. Dann gibt es ein $x_{0} \in (a, b)$ mit $f(x_{0}) = 0$
**$\rightarrow$ Garantiert die Existenz von Nullstellen**

#### Sei $D \subseteq \mathbb{R}$. Wann heißt eine Funktion $f:D \rightarrow \mathbb{R}$ beschränkt? #card 
Wenn die Menge $f(D)$ beschränkt ist, das heißt falls ein $C \geq 0$ existiert, so dass $|f(x)| \leq C$ für alle $x \in D$ gilt.

#### Wie lauter der fundamentale Satz, welcher das Verhalten stetiger Funktionen auf kompakten Mengen beschreibt? #card 
Sei $K \subseteq \mathbb{R}$ kompakt und nicht-leer, sowie $f \in C(K)$. Dann gibt es $x_{*}, x^{*} \in K$, so dass $f(x_{*}) \leq f(x) \leq f(x^{*})$ für alle $x \in K$ gilt. Insbesondere ist f beschränkt.
**Bemerkung:** Damit existieren insbesondere $max \ f(K) = f(x^{*})$ und $min \ f(K) = f(x_{*})$. In Worte gefasst lautet dieser Satz damit: *"Eine stetige Funktion auf einem Kompaktum nimmt ihr Maximum und ihr Minimum auf dem Kompaktum an"*  

#### Seien $V$ und $W$ normierte $\mathbb{R}$-Vektorräume, $D \subseteq V$ und $f:D \to W$ eine Funktion. Wann nennen wir $x_{0} \in D$ einen Häufungspunkt?
Falls es eine Folge $(a_{n})$ in D mit $a_{n} ≠ x_{0}$ für alle $n \in \mathbb{N}$ gibt, die gegen $x_{0}$ konvergiert.

#### Sei $x_{0}$ ein Häufungspunkt von D, wann gilt dann, dass $\lim_{x \to x_{0}} f(x) = y$ ist? #card 
Falls für jede Folge $(a_{n})$ in D, die gegen $x_{0}$ konvergiert *und* $a_{n} ≠ x_{0}$ für alle $n \in \mathbb{N}$, die Folge $(f(a_{n}))$ gegen y konvergiert.

#### Seien $V$ und $W$ normierte $\mathbb{R}$-Vektorräume, $D \subseteq V$ und $x_{0} \in D$. Wann heißt eine Funktion $f:D \to W$  stetig in $x_{0}$ #card 
Wenn für jede Folge $(a_{n})$ in $D$, die gegen $x_{0}$ konvergiert, auch die Folge $(f(a_{n}))$ konvergiert und $\lim_{n \to \infty} f(a_{n}) = f(x_{0})$ gilt.

#### Seien $V$ und $W$ normierte $\mathbb{R}$-Vektorräume, $D \subseteq V$ und $x_{0} \in D$. Wann heißt eine Funktion $f:D \to W$  stetig in $D$ #card 
Wenn $f$ in jedem Punkt $x_{0} \in D$ stetig ist.

#### Wie ist $C(D;W)$ definiert? #card  
$C(D;W) := \{f: D \to W:f$ stetig auf $D\}$

#### Was ist eine Koordinatenfunktion? #card 
Eine Funktion mehrerer Funktionen hat $d$ reele Eingabewerte. Man nimmt in der Analysis an, dass die Funktion von $d$ reelen Eingangsparametern abhängt und schreibt nicht ganz korrekt $f(x_{1}, x_{2}, ..., x_{d})$ statt $f((x_{1}, x_{2}, ..., x_{d})^T)$. Der Wert $f(x)$ ist für jedess $x \in D$ ein Vektor $\mathbb{R}^p$. Man hat also $$f(x)=
\begin{pmatrix} f(x)_1 \\ f(x)_2 \\ \vdots \\ f(x)_p 
\end{pmatrix} =
\begin{pmatrix} f_1(x) \\ f_2(x) \\ \vdots \\ f_p(x)
\end{pmatrix}$$ mit den $p$ sogenannten *Koordinatenfunktionen* $f_{1}, f_{2},...,f_{p}: D \to R$ 

#### Sei $D \subseteq \mathbb{R}$ und $x_{0}\in D$. Wann ist $f:D\to \mathbb{R}^p$ in $x_{0}$ stetig? #card 
Genau dann wenn alle *Koordinatenfunktionen* $f_{1}, f_{2}, ..., f_{p}:D \to \mathbb{R}^p$ in $x_{0}$ stetig sind

#### Was gilt, wenn $||\cdot||$ und $|||\cdot|||$ zwei normen auf $\mathbb{R}^{d}$ sind? #card 
Dann gibt es Konstanten $0 < c < C$, so dass $c||x|| \leq |||x||| \leq C||x||$ gilt

#### Was gilt, wenn eine Folge $(a_{n})$ in $\mathbb{R^d}$ bezüglich einer Norm konvergieren? #card 
Sie konvergieren bezüglich jeder anderen Norm und der Grenzwert ist der Selbe. (Genauso wie Konvergenz von Reihen und Stetigkeit von Funktionen)

#### Welche bekannten Potenzreihen gibt es und wie sehen diese aus? #card
- Exponentialreihe: $e^{z}= \sum\limits_{n=0}^{\infty} \frac{z^{n}}{n!} = 1 + z + \frac{1}{2}z^{2} + \frac{1}{6}z^{3} + ...$, $z \in \mathbb{C}$.
- Geometrische Reihe: $\sum\limits_{n=0}^{\infty} = \frac{1}{1-x}$ 

#### Sei $(a_{n})$ eine Folge in $\mathbb{K}$ (also in den reelen oder in den komplexen Zahlen), so dass der Grenzwert $\varrho := \lim_{n \to \infty} \sqrt[n]{|a_{n}|}$ existiert oder die Folge $(\sqrt[n]{|a_{n}|})$ unbeschränkt ist. Welche Konvergenzaussagen gelten dann für die Potenzreihe $\sum\limits_{n=0}^{\infty} a_{n}x^{n}$? #card 
1. Ist die Folge $(\sqrt[n]{|a_{n}|})$ unbeschränkt, so konvergiert die Potenzreihe nur für $x=0$
2. Ist $\varrho = 0$, so konvergiert die Potenzreihe für alle $x \in K$ absolut
3. Ist $\varrho \in (0, \infty)$, so ist die Potenzreihe für alle $x \in \mathbb{K}$ mit $|x| < 1/ \varrho$ absolut konvergent und für alle $x \in \mathbb{K}$ mit $|x| > 1/\varrho$ divergent
Sei außerdem $\sum\limits_{n=0}^{\infty}a_{n}x^{n}$ eine Potenzreihe die obige vorraussetzungen erfüllt, dann heißt die Zahl $$r:=\begin{cases}0,&\text{falls 1. gilt}\\\infty,&\text{falls 2. gilt}\\\frac{1}{\varrho},&\text{falls 3. gilt}\end{cases}$$ der Konvergenzradius der Potenzreihe *Also der Radius des Kreises, in welchem die Potenzreihe Konvergiert*

#### Was ist eine Potenzreihe? #card 
Sei $(a_{n})$ eine Folge in $\mathbb{K}$, $n_{0} \in \mathbb{N}$ und $x_{0} \in \mathbb{K}$. Dann nennt man eine Reihe der Form $\sum\limits_{n=n_{0}}^{\infty}a_{n}(x-x_{0})^n$ Potenzreihe. Der Punkt $x_{0}$ wird Entwicklungspunkt der Potenzreihe genannt.
*Anmerkung:* "Im Prinzip verschieben wir den Ursprung, also den 0-Punkt des Koordinatensystems um $x_0$"

#### Wie berechnet man alle $x$ für die $(a_{n})$ konvergiert? #card 
Konvergenzradius bestimmen und Ränder abchecken
*Ein Beispiel dazu gibt es im Skript (5.9.8)*

#### Sei $(a_{n})$ eine Folge in $\mathbb{K}$ mit $a_{n} ≠ 0$ für alle $n \in \mathbb{N}$, so dass $\sigma := \lim_{n\to \infty}|\frac{a_{n+1}}{a_{n}}|$ existiert. Was gilt dann für den Konvergenzradius $r$ von $\sum\limits_{n=0}^{\infty} a_{n}x^{n}$? #card 
$$r:=\begin{cases}\frac{1}{\sigma},&\text{falls } \sigma \in (0, \infty)\\\infty,&\text{falls } \sigma = 0\end{cases}$$

#### Seien $\sum\limits_{n=0}^{\infty} a_{n}x^{n}$ und $\sum\limits_{n=0}^{\infty} b_{n}x^{n}$ Potenzreihen in $\mathbb{K}$ mit Konvergenzradien $r_{1},r_{2} <0$. Was gilt nun für die Potenzreihe $a=\sum\limits_{n=0}^{\infty} \sum\limits_{k=0}^{n} a_{k}b_{n-k}x^{n}$ und für alle $x \in \mathbb{K}$ mit $|x| < r$? #card 
Die Potenzreihe $a$ hat mindestens den den Konvergenzradius $r:=min\{r1, r2\}$ und es gilt für alle $x \in \mathbb{K}$ mit $|x| < r$, dass $\sum\limits_{n=0}^{\infty} \sum\limits_{k=0}^{n} a_{k}b_{n-k}x^{n} = (\sum\limits_{n=0}^{\infty} a_{n}x^{n})(\sum\limits_{n=0}^{\infty} b_{n}x^{n})$


#### Sei $\sum\limits_{n=0}^{\infty} a_{n}x^{n}$ eine Potenzreihe in $\mathbb{K}$ mit Konvergenzradius $r>0$. Was gilt nun? #card 
Die dadurch gegebene Funktion $f:\{x \in \mathbb{K} :{|x|}< r\} \to \mathbb{K}$ mit $f(x) = \sum\limits_{n=0}^{\infty}a_{n}x^{n}$ ist stetig auf $\{x \in \mathbb{K}:|x| < r\}$

#### Umkehrfunktion von der Exponentialfunktion $E: \mathbb{R} \to (0, \infty)$ #card-reverse
Umkehrfunktion vom natürlichen Logarithmus $ln:=E^{-1}:(0,\infty) \to \mathbb{R}$ 

#### Welche Eigenschaften hat der Logarithmus? #card 
1. Die Funktion $ln$ ist auf $(0,\infty)$ stetig und wächst streng monoton
2. Es gilt $\ln(1)=0$ und $\ln(e) = 1$
3. $\lim_{x\to \infty} \ln(x) = \infty$ und $\lim_{x \to 0+} \ln(x) = -\infty$ 
4. Für alle $x, y \in (0, \infty)$ und $q \in \mathbb{Q}$ gilt:
	1. $\ln(xy) = \ln(x)+\ln(y)$
	2. $\ln(\frac{x}{y})$ = $\ln(x) - \ln(y)$
	3. $\ln(x^{q})= q \ln(x)$

#### Wie lautet die allgemeine Potenzfunktion? #card 
Für alle $a \in (0, \infty)$ und alle $x \in \mathbb{R}$ definieren wir die allgemeine Potenz durch *$a^{x}:=e^{x \cdot \ln(a)}$*

#### Sei $a \in (0, \infty)$, was gilt dann für die Potenzfunktion $x \longmapsto a^{x}$ (Stetigkeit und Potenzregeln) #card 
Die Funktion ist stetig und es gelten folgende Potenzregeln:
1. $a^{x+y}=a^{x}a^{y}$
2. $a^{-1} = \frac{1}{a}$
3. $(a^{x})^{y}=a^{xy}$ 

#### Wie ist die Sinus-Funktion $\sin(z)$ definiert? #card 
$\sin(z):=\sum\limits_{n=0}^{\infty} \frac{(-1)^{n}}{(2n+1)!} z^{2n+1}$, $z \in \mathbb{C}$ (Der Sinus ist gerade)

#### Wie ist die Cosinus-Funktion $\cos(z)$ definiert? #card 
$\cos(z):=\sum\limits_{n=0}^{\infty} \frac{(-1)^{n}}{(2n)!} z^{2n}$, $z \in \mathbb{C}$ (Der Cosinus ist ungerade)

#### Wie lauten die wichtigen Werte von Sinus und Cosinus an den Winkeln? #card 
![[SCR-20230712-naen.png]]

#### Wie lautet die Eulersche Formel? #card 
$e^{iz} = \cos(z) + sin(z)i$
Damit gilt für alle $x \in \mathbb{R}$ $Re(e^{ix}) = cos(x)$ und $Im(e^{ix}) = sin(x)$

#### Was gilt für die Beträge der Sinus und Cosinus Funktionen? #card 
$|sin(x)| \leq 1$ und $|cos(x)| \leq 1$

#### Wie lauten die Additionstheoreme der Sinus und Cosinus Funktionen? #card 
- $\sin(x+y) = \sin(x)\cos(y)+ \sin(y)\cos(x)$ 
- $\cos(x+y)=\cos(x)\cos(y)-\sin(x)\sin(y)$

#### Welche Rechenregeln gelten für verschobene Sinus und Cosinus Funktionen? #card 
1. $\sin\left(x + \frac{\pi}{2}\right) = \cos(x)$
2. $\sin(x + \pi) = -\sin(x)$
3. $\sin(x+2\pi) = \sin(x)$
4. $\cos\left(x+ \frac{\pi}{2}\right) = -\sin(x)$
5. $\cos(x+\pi) = -\cos(x)$
6. $\cos(x+2\pi) = cos(x)$

#### Wie lautet die Beschreibung der Nullstellen von Sinus und Cosinus? #card 
- $\sin(z) = 0 \Leftrightarrow z= k\pi$ für ein $k \in \mathbb{Z}$
- $\cos(z) = 0 \Leftrightarrow z= \frac{\pi}{2}+k\pi$ für ein $k \in \mathbb{Z}$

#### Wie lautet die Tangens Funktion $\tan(z)$? #card 
$\tan(z) = \frac{\sin(z)}{\cos(z)}$

#### Sei $z = x + yi \in \mathbb{C} \ \{0\}$ mit $x, y \in \mathbb{R}$. Was sind die Polarkoordinaten von $z$? #card 
Die Polarkoordinaten von $z$ bestehen aus dem Betrag von $z$: $r:=\sqrt{x^{2}+y^{2}}$ und dem Argument von $z$, also der Winkel $\varphi$ der zwischen $z$ und der positiven reelen Achse eingeschlossen wird. Beide Werte $(r, \varphi)$ zusammen sind die Polarkoordinaten von $z$ 
*Anmerkung: Ist das Argument von $z$ auf den Bereich $(-\pi, \pi]$ festgelegt, so gelten die folgenden Umrechungsformeln zwischen den Darstellungen für eine komplexe Zahl $z = x + yi$ mit Polarkoordinaten $(r, \varphi)$:* ![[SCR-20230712-nxxg.png]]*Desweiteren gilt für jede komplexe Zahl $z$ auf dem Einheitskreis, also $|z| = 1$, dass $\cos(\varphi) + \sin(\varphi)i$ mit einem geeingeten $\varphi \in (-\pi, pi]$. Tatsächlich gilt für jedes $z = |z|\frac{z}{|z|} = r(\cos(\varphi) + \sin(\varphi)i) = re^{i\varphi}$.** 

#### Seien $z = re^{i\varphi}$, $w=se^{i\psi} \in \mathbb{C} \backslash \{0\}$ mit Polarkoordinaten $(r, \varphi)$, bzw. $(s, \psi)$ gegeben. Welche Polarkoordinaten haben dann $z \cdot w$ und $z/w$? #card 
- $z \cdot w$ hat die Polarkoordinaten $(rs, \varphi + \psi)$
- $z/w$ hat die Polarkoordinaten $(r/s,\varphi - \psi)$

#### Welche Hyperbolischen Funktionen gibt es und wie sind diese Definiert? #card 
- Sinus hyperbolicus: $\sinh(z) := \frac{e^{z}-e^{-z}}{2}$, $z \in \mathbb{C}$
- Cosinus hyperbolicus: $\cosh(z) := \frac{e^{z}+e^{-z}}{2}$, $z \in \mathbb{C}$
- Tangens hyperbolicus: $\tanh(z) = \frac{\sinh(z)}{cosh(z)}$, $z \in \mathbb{C} \backslash \{\left( k\pi + \frac{\pi}{2} \right)i : k \in \mathbb{Z}\}$  

