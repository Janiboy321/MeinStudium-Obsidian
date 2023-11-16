#### Was bedeutet Angemessenheit?
> Ein Modell ist für einen realen, informell beschriebenen Sachverhalt angemessen, wenn alle Aspekte des Sachverhalts so wiedergegeben werden, dass Beobachtungen, welche am formalen Modell gemacht werden, auch für den realen Sachverhalt gültig sind.

##### Beachte:
Angemessenheit eines Modells hängt auch davon ab, wie die Beobachtungen in der Realität interpretiert werden und welche Art von Fragestellung von Interesse sind

##### Wie argumentiert man, dass ein Modell angemessen ist?
- Eine Argumentation stell einen Zusammenhang zwischen einem formalen Modell und einem informell beschriebenen Sachverhalt her
- Die Argumentation kann nur informell geschehen, da einer der beiden Bezugspunkte nicht formal beschrieben ist

### Alternativen in der Modellierung
> Oft gibt es mehr als eine Möglichkeit, eine informelle Beschreibung angemessen zu formalisieren. Allerdings können unterschiedliche Modellierungen auch unterschiedlich angemessen sein

#### Verwendung von Indexmengen
- Im ersten Modul
	- Modellierung der Delegierten durch Symbole
		$DEL = \{d_{1}, d_{2}, d_{3}, f_{1}, f_{2}, f_{3}, it_{1}, ...\}$
- Alternative
	- Delegiere durch Paare anstatt durch Symbole modellieren
		$INDEX = \{1, 2, 3\}$
		$DEL' = NATION \times INDEX$
		$(d, 2)$ Modelliert beispielsweise den zweiten deutschen Delegierten

##### Angemessenheit der Modellierung durch $DEL'$
- Alle 12 Delegierten werden durch ein Element in $DEL'$ repräsentiert
- Jedes Element in $DEL'$ repräsentiert einen Delegierten
$\Rightarrow$ Menge $DEL'$ ist also eine angemessene Modellierung der Menge aller Delegierten

##### Konsequenz der Änderung
Die Modellierung anderer Konzepte muss gegebenenfalls angepasst werden

#### Implizite Modellierung von Objekten
- Im ersten Modul
	- Modellierung der Arbeitskreise durch Symbole
		$AKS = \{ak_{1}, ak_{2}, ak_{3}\}$
- Alternative
	- Keine Bezeichner für Arbeitskreise einführen sondern die AKs direkt durch Mengen von Delegierten modellieren
		$AKS' = \mathcal{P}(DEL)$ 
		
	**Vorteile**: Es müssen keine neuen Symbole eingeführt werden
	**Nachteile**: Sind zwei Arbeitskreisen exakt die gleichen Delegierten zugeordnet, lassen sich diese im Modell nicht unterscheiden

##### Anpassung der Modellierung
Die Zuordnung der Delegierten zu Arbeitskreisen könnte bspw. durch ein Tripel von Mengen modelliert werden:
$ZUORDNUNG' \in AKS' \times AKS' \times AKS'$

#### Unterspezifizierte Wertebereiche

- Modellierung der Nationen durch Symbole
	- $NATION = \{d, f, it, au\}$
	- ##### Angemessenheit
		- Es gibt Nationen welche durch die Modellierung nicht erfasst werden, da aber nur die vier Modellierten relevant sind, ist das Modell trotzdem angemessen
		- Würde man alle Nationen der EU Modellieren wollen, ist das Modell nicht Angemessen, stattdessen könnte man das Modell um $\text{WEITERE-NATIONEN}$ erweitern: 
			$NATION' = \{d, f, it, au\} \cup \text{WEITERE-NATIONEN}$
- Modellierung der Sprachen durch Symbole
	- $SPRACHE = \{s-d, s-f, s-it\}$
	- ##### Angemessenheit
		- Es gibt Sprachen, welche durch das Modell nciht erfasst werden, sollten manche delegierte eine Sprache sprechen welche nicht erfasst wird, ist das Modell nicht mehr angemessen
		- In diesem Fall könnte man das Modell wie im oberen Beispiel um $\text{WEITERE-SPRACHEN}$ erweitern

**Vorteile und Nachteile**:
- Um die Menge SPRACHE extensional definieren zu können muss man alle Sprachen kennen, die von einem Delegierten gesprochen werden können
- Die Modellierung durch die Menge $SPRACHE = \{s-d, s-f, s-it\} \cup \text{WEITERE-SPRACHEN}$	kann angegeben werden, ohne alle Sprachen zu kennen, sie lässt die Definition der Menge der Sprachen allerdings offen

> Man kann Oberbegriffe formal modellieren, ohne die Instanzen des Oberbegriffs zu kennen, indem man eine Menge einführt, ohne zu definieren welche Elemente die Menge enthält

#### Kardinalität
> Die Kardinalität einer endlichen Menge $M$ ist die Anzahl ihrer Elemente. Man schreibt $|M|$ für die Kardinalität der Menge $M$. 
![[Bildschirmfoto 2023-11-06 um 19.22.29.png]]
![[Bildschirmfoto 2023-11-06 um 19.23.20.png]]

#### Disjunkte Vereinigung
##### Definition: 
Sei $I = \{1, ..., n\}$ eine Indexmenge mit $n > 1$, Dann ist die *disjunkte Vereinigung* von Mengen $W(1), ..., W(n)$ wie folgt definiert:
	$W(1) \uplus ... \uplus W(n) = \{(i, w) | i \in I \land w \in W(i)\}$   
![[Bildschirmfoto 2023-11-06 um 19.53.06.png]]
![[Bildschirmfoto 2023-11-06 um 19.53.28.png]]

#### Unendliche Folgen
##### Definition
Die Menge aller nicht leeren, endlichen Folgen über einer Menge $M$ ist die wie folgt definierte Menge $M^{+} = M^{j}$.
Die Menge alle enflichen Folgen über M ist die Menge $M^{*} = M^{+} \cup \{()\}$.

##### Alternative definition von endlichen Folgen
Alternativ könnte eine Folge über $M$ mit der Länge $n$ auch durch eine Funktion $f$ aus dem Funktionenraum $\{1, ..., n\} \to M$ repräsentierteren, wobei der Wert der Funktion $f$ an der Stelle $i \in \{1, ..., n\}$ das i'te Element des Tupels $t$ ist, d.h. $f(i) = t_{j}$

##### Definition der Menge aller unendlichen Folgen über M
$M^{\infty} = \mathbb{N} \to M$

##### Verwendung von unendlichen Folgen
Mit unendlichen Folgen können die möglichen Verhalten von Systemen beschrieben werden, die nicht immer terminieren

> Wie modelliert man terminierende Verhalten mit unendlichen Folgen?

#### Prädikate
##### Definition:
Ein Prädikat über eine Menge $M$ ist eine Funktion $p:M \to \mathbb{B}$, also eine totale Funktion mit den booleschen Werten als Bildbereich ($\mathbb{B} = \{\mathfrak{w}, \mathfrak{f} \}$).
##### Beobachtung
Es gibt enge Beziehungen zwischen Prädikaten und Mengen:
- Die charakteristische Funktion einer Teilmenge $K \subseteq M$ ist das wie folgt definierte Prädikat über $M$:
$$\mathcal{X}(m) = \left\{
\begin{array}{ll}
\mathfrak{m} & \textrm{falls }m \in K  \\
\mathfrak{f} & \, \textrm{falls } \lnot m \in K  \\
\end{array}
\right.$$
- Ein Prädikat $p: M \to \mathbb{B}$ induziert zwei Mengen
	- Die Menge aller Elemente aus $M$ für die $p$ wahr ist
		$W_{p}=\{m \in M | p(m) = \mathfrak{w}\}$
	- Die Menge aller Elemente aus $M$ für die $p$ falsch ist
		$W_{p}=\{m \in M | p(m) = \mathfrak{f}\}$

*Beispiel:*
Wir modellieren, ob ein gegebener Delegierter einem gegebenen Arbeitskreis zugeordnet wurde, indem wir ein Prädikat $\textrm{ist-zugeordnet}$ über der Menge $DEL \times AKS$ wie folgt definieren:
$$\textrm{ist-zugeordnet}(v, ak) = \left\{
\begin{array}{ll}
\mathfrak{m} & \textrm{falls }v \in \textrm{zuordnung}(ak)  \\
\mathfrak{f} & \, \textrm{falls } \lnot v \in \textrm{zuordnung}(ak)  \\
\end{array}
\right.$$

#### Multimengen
##### Definition
Eine Multimenge über einer Menge $M$ ist eine Funktion $m: M \to \mathbb{N}_{0}$, also eine totale Funktion mit den natürlichen Zahlen als Bildbereich.

##### Verwendung 
Multimengen eignen sich um Ressourcen zu Modellieren

*Beispiel:*
Einen Vorrat von 200 Bausteinen kann man z.B. durch die Funktion aus dem Funktionenraum $\{Stein\} \to \mathbb{N}$ modellieren, die dem Symbol $\textrm{stein}$ die Zahl 200 zuordnet.

#### Partiell Geordnete Mengen
##### Definitionen:
- Aus Modul 1
	- Eine Zweistellige Relation $R \subseteq M \times M$ heißt Ordnung (oder auch partielle Ordnung), wenn sie reflexiv, antisymmetrisch und transitiv ist
	- Eine zweistellige Relation $R \subseteq M \times M$ heißt totale Ordnung (oder auch lineare Ordnung) wenn sie alternativ, reflexiv, antisymmetrisch und transitiv ist
- Eine partiell geordnete Menge ist ein Paar $(M, \leq)$, wobei 
	- $M$ eine Menge ist, die Trägermenge genannt wird, und
	- $\leq\subseteq M \times M$ eine partielle Ordnung ist.
- Eine Geordnete Menge ist eine partiell geordnete Menge $(M, \leq)$ wobei $\leq \subseteq M \times M$ eine totale Ordnung ist

##### Visualisierung
Partiell geordnete Mengen können durch **Hasse Diagramme** als Graph visualisiert werden. 

###### Wie zeichnet man das Hasse Diagramm für eine partiell geordnete Menge $(M, \leq)$ 
- Jedes $m \in M$ wird durch einen Knoten im Graph repräsentiert
- Wenn $m_{1} < m_{2}$ für zwei Knoten $m_{1}, m_{2} \in M$ gilt, dann
	- zeichnet man den Knoten für $m_{2}$ oberhalb des Knotens für $m_{1}$ und,
	- falls es kein $m \in M$ mit $m_{1} \leq m$, $m \leq m_{2}$, $\lnot m = m_{1}$ und $\lnot m = m_{2}$ gibt, dann verbindet man die Knoten $m_{1}$ und $m_{2}$ mit einer Kante
![[Bildschirmfoto 2023-11-07 um 16.07.27.png]]
![[Bildschirmfoto 2023-11-07 um 16.07.47.png]]

![[Bildschirmfoto 2023-11-07 um 16.08.03.png]]
![[Bildschirmfoto 2023-11-07 um 16.08.18.png]]
![[Bildschirmfoto 2023-11-07 um 16.08.44.png]]

#### Obere und Untere Schranken
![[Bildschirmfoto 2023-11-07 um 16.09.21.png]]

#### Verbände
##### Defintion
Ein Verban ist ein Tupel $(M, \leq, \sqcup, \sqcap)$, so dass
- $(M, \leq)$ eine geordnete Menge ist
- $\sqcup$ ein Vereinigungsoperator auf $(M, \leq)$ ist
- $\sqcap$ ein Schnittoperator auf $(M, \leq)$ ist

##### Typische Fragestellungen
- Welche Sicherheitsstufe muss ein Subjekt mindestens haben um zwei gegebene Objekte lesen zu dürfen
- Welche Sicherheitsstufe darf ein Objekt höchstens haben, damit es von zwei gegebenen Subjekten gelesen werden darf?