
# 1)
###### a)
UNTÄTIG $:= \{m \in MITARBEITER : plan(m) = \emptyset \}$
###### b) 
geeignet(m, p) $:= \{m \in MITARBEITER;\ p \in PROJEKT : |ausbildungen-von(m) = ausbildungen-für(p)| \geq 1\}$
LÖSUNG:
$geeignet(m, \emptyset) = \emptyset$
$$geeignet(m, (x, xs)) = \left\{
\begin{array}{ll}
(x, geeignet(m, xs)) & \text{wenn } \exists a \in \text{ausbildung-von}(m): a \in \text{ausbildung-für(x)} \\
geeignet(m, xs) & \, \textrm{sonst} \\
\end{array}
\right.$$
###### c)
Sei die Funktion $head$ definiert wir in der Bemerkung:
aktuelles-projekt-für(m) $= head(plan(m)$

###### d)
projekt-aktiv(p) $:= \{b \in \mathbb{B}: p \in aktuelles-projekt-für(MITARBEITER))\}$

LÖSUNG:
projekt-aktiv: PROJEKT $\to \mathbb{B}$
$$\text{projekt-aktiv}(p) = \left\{
\begin{array}{ll}
w & \text{wenn } \exists m \in MITARBEITER \text{ ....}(m): a \in \text{ausbildung-für(x)} \\
f & \, \textrm{sonst} \\
\end{array}
\right.$$
###### e i)
ANFORDERUNG1 $\subseteq$ MITARBEITER $\to$ PROJEKT*
plan $\in$ ANFORDERUNG1 $\Leftrightarrow$ $\forall m \in$ MITARBEITER: geeignet(m, plan(m)) = plan(m)

###### e ii)
ANFORDERUNG2 $\subseteq$ MITARBEITER $\to$ PROJEKT*
plan $\in$ ANFORDERUNG2 $\Leftrightarrow$ $\forall p \in$ PROJEKT: projekt-aktiv(p) $\Rightarrow$ ...

LÖSUNG

###### g