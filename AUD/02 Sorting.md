#### Das Sortierproblem
- Gegeben ist eine Folge von Objekten
- Gesucht wird eine Sortierung dieser Objekte (Gemäß ausgewählten Schlüsselwerten)
- Diese Schlüßßelwerte müssen nicht eindeutig, aber sortierbar sein

###### Recap: Was ist eine totale Ordnung
Eine totale Ordnung ist eine Relation für die gilt: 
1. Reflexiv $\forall x \in M: x \leq x$
2. Transitiv $\forall x, y, z \in M: x \leq y \land y \leq z \Rightarrow x \leq z$
3. Antisymmetrisch $\forall x, y \in M: x \leq y \land y \leq x \Rightarrow x = y$
4. Total $\forall x, y \in M: x \leq y \lor y \leq x$

#### Insertion Sort
Beim Insertion Sort nimmt man ein Element aus einer Reihe und fügt es an die Richtige stelle ein. (Beispiel mit Karten nach Helligkeit Sortieren)

###### Korrektheit
_Beispiel aus Vorlesung:_
Schleifeninvariante:
	Bei jedem Eintritt für Zählerwert **i** (und nach letzter Ausführung) entsprechen die aktuellen Einträge in **A[0], ..., A[i-1]** den sortierten ursprünglichen Eingabewerten a[0], ..., a[i-1]. Ferner gilt **A[i] = a[i], ..., A[n-1] = a[n-1]**

In der Vorlesung wurde ein Algorithmus (passend zur Schleifeninvariante) vorgestellt und mithilfe der Induktion wurde dessen Korrektheit bewiesen:
