#### G1
a) Eine aus endlich vielen Schritten ausführbare Handlungsvorschrift zur Umwandlung von Ein und Ausgaben

b) Ein Sortieralgorithmus ist ein Algorithmus, welcher dazu da ist um Listen in endlich vielen Schritten zu Sortieren. Ein InsertionSort Algortihmus tut das, indem er Schritt für Schritt ein Element aus der Liste zieht und dieses dann an die richtige Stelle wieder einfügt

c) Eine Totale Ordnung ist ein Menge mit einer Operation, welche die Menge der Größe nach sortieren kann. Beispielsweise ">" oder "<"

d) Die Schleifeninvariante beschreibt, was vor und nach der Schleife gelten muss bzw. gleich sein muss

#### G2
Wir sagen, dass ein Algorithmus _terminiert_, wenn er für jede _Eingabe_ nur _endlich_ viele Schritte durchläuft und dann eine _Ausgabe_ produziert. Entspricht diese stets den Erwartungen gemäß der Spezifikation des Algorithmus, so nennen wir den Algorithmus _korrekt_. Oft gibt es mehrere Algorithmen, die das gleiche _Problem_ lösen können. Dann kann es sich lohnen, einen Algorithmus zu verwenden, der möglichst _effizient_ im Hinblick auf die Ressourcen _
_, __ und __ ist. Ein Algorithmus  erfüllt das Kriterium der _determiniertheit_, wenn er für jede _Eingabe_ stets die gleiche _Ausgabe_ berechnet. Eine verschärfung der Determiniertheit, bei der zusätzlich gefordert wird, dass der Algorithmus für jede _Eingabe_ dieselben _Schritte_ durchlaufen muss, wird Determinismus genannt.

1) Mögliche Anwendungsfälle findet man bestimmt in der IT-Sicherheit, wo die Korrektheit wichtiges ist, als die Effizienz
2) Laufzeit, Ressourcennutzung, korrektheit, Parallelisierung, wiederverwendbarkeit, modularität, usw.
Lösung: Varianz der Laufzeit, größe des Algorithmus, parallelisierbarkeit, anzahl Quelltext

#### G3
**Algorithmus 1:** Der erste Algorithmus checkt zuerst, ob die gegebene Array aufsteigend Sortiert ist. Ist der das nicht, werden zufällig zwei Elemente vertauscht. 
Der Algorithmus ist nicht Determinierend und kein Determinisumus. Er Terminiert nicht aber ist Korrekt, und nicht Effizient, da alle Elemente zufällig miteinander vertauscht werden

**Algorithmus 2:** Der Algorithmus überprüft ob die eingabe eine Primzahl ist. Determiniert, Determinismus, korrektheit ist nicht gegeben, da Zwei eine Primzahl ist, der Algorithmus aber false zurück geben würde. Der Algorithmus terminiert aber ist nicht effizient, da man beim Checken für Primzahlen nur bis zur Wurzel der Zahl checken muss

