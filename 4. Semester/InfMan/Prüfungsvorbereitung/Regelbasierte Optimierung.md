#### 1. Selektions-Aufspaltung
$\sigma_{C_{1}\land C_{2}\land ... \land C_{n}} \equiv \sigma_{C_{1}}(\sigma_{C_{2}}(...(\sigma_{C_{n}}(R))...))$    

#### 2. Selektions-Pushdown
Mittels folgender Regeln, werden Selektionen im Baum soweit runter wie möglich gedrückt:
*(2)* $\sigma$ ist Kommutativ $\Rightarrow$ $\sigma_{C_{1}}(\sigma_{C_{2}}(R)) \equiv \sigma_{C_{2}}(\sigma_{C_{1}}(R))$
*(4)* Vertauschen von $\sigma$ und $\pi$ $\Rightarrow$ $\pi_{A_{1},...,A_{n}}(\sigma_{C}(R)) \equiv \sigma_{C}(\pi_{A_{1},...,A_{n}}(R))$
*(6)* Vertauschen von $\sigma$ mit $\bowtie$ $\Rightarrow$ $\sigma_{C_{1}}(R \bowtie S) \equiv \sigma_{C_{1}}(R) \bowtie S$ oder $\sigma_{C_{1} \land C_{2}}(R \bowtie S) \equiv \sigma_{C_{1}}(R) \bowtie \sigma_{C_{2}}(S)$ 

#### 3. Join-Ersetzung
$\sigma_{c}(R \times S) \equiv R \bowtie_{c}S$ (Geht nur wenn c von der Form R.temp *op* S.temp)

#### 4. Projektions-Pushdown
Mittels folgender Regeln, werden Projektionen im Baum soweit runter wie möglich gedrückt
*(3)* $\pi$-Kaskaden auflösen: Falls $L_{1} \subseteq L_{2} \subseteq ... \subseteq L_{n} \rightarrow \pi_{L_{1}}(\pi_{L_{2}}(...(\pi_{L_{n}}(R))...)) \equiv \pi_{L_{1}}(R)$
*(4)* Vertauschen von $\sigma$ und $\pi$ $\Rightarrow$ $\pi_{A_{1},...,A_{n}}(\sigma_{C}(R)) \equiv \sigma_{C}(\pi_{A_{1},...,A_{n}}(R))$
*(7)* Vertauschen von $\pi$ mit $\bowtie$ $\Rightarrow$ $\pi_{L}(R \bowtie_{C} S) \equiv (\pi_{A_{1}, ..., A_{n}}(R)) \bowtie_{C} (\pi_{B_{1},..., B_{m}}(S))$ oder $\pi_{L}(R \bowtie_{C} S) \equiv (\pi_{A_{1}, ..., A_{n}, A_{1}',..., A_{p}'}(R)) \bowtie_{C} (\pi_{B_{1},..., B_{m}, B_{1}',..., B_{q}'}(S))$
*(10)* $\pi$ ist distributiv mit $\cup$ $\Rightarrow$ $\pi_{C}(R \cup S) \equiv (\pi_{C}(R)) \cup (\pi_{c}(S))$

#### 5. Operationsfolgen gleicher Operatoren zusammenfassen
*(1)* $\sigma_{C_{1}\land C_{2}\land ... \land C_{n}} \equiv \sigma_{C_{1}}(\sigma_{C_{2}}(...(\sigma_{C_{n}}(R))...))$   
*(3)* $\pi$-Kaskaden auflösen: Falls $L_{1} \subseteq L_{2} \subseteq ... \subseteq L_{n} \rightarrow \pi_{L_{1}}(\pi_{L_{2}}(...(\pi_{L_{n}}(R))...)) \equiv \pi_{L_{1}}(R)$

