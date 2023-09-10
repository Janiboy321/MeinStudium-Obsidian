#### 1. Selektions-Aufspaltung
- $\sigma_{C_{1}\land C_{2}\land ... \land C_{n}} \equiv \sigma_{C_{1}}(\sigma_{C_{2}}(...(\sigma_{C_{n}}(R))...))$    

#### 2. Selektions-Pushdown
Mittels folgender Regeln, werden Selektionen im Baum soweit runter wie möglich gedrückt:
*(2)* $\sigma$ ist Kommutativ $\Rightarrow$ $\sigma_{C_{1}}(\sigma_{C_{2}}(R)) \equiv \sigma_{C_{2}}(\sigma_{C_{1}}(R))$
*(4)* Vertauschen von $\sigma$ und $\pi$ $\Rightarrow$ $\pi_{A_{1},...,A_{n}}(\sigma_{C}(R)) \equiv \sigma_{C}(\pi_{A_{1},...,A_{n}}(R))$
*(6)* Vertauschen von $\sigma$ mit $\bowtie$ $\Rightarrow$ $\sigma_{C_{1}}(R \bowtie S) \equiv \sigma_{C_{1}}(R) \bowtie S$ oder $\sigma_{C_{1} \land C_{2}}(R \bowtie S) \equiv \sigma_{C_{1}}(R) \bowtie \sigmaS$ 