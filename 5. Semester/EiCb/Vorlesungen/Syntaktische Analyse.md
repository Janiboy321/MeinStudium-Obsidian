#### Häufiger Fehler: Grammatik ist nicht LL(1)
**Auszug aus Grammatik**
$$\begin{align*}
\text{single-Command } ::= &\text{ V-name := Expression}\\
& \text{| Identifier( Expression )}\\
& \text{| if Expression then single-Command else Single-Command}\\
& \text{| ...}
\end{align*}$$
**Anfangsmengen**
$$\text{starters }$$