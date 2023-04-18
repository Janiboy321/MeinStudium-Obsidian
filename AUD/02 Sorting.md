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

