#### 1. Selektions-Aufspaltung
- $\sigma_{C_{1}\land C_{2}\land ... \land C_{n}} \equiv \sigma_{C_{1}}(\sigma_{C_{2}}(...(\sigma_{C_{n}}(R))...))$    

#### 2. Selektions-Pushdown
Mittels folgender Regeln, werden Selektionen im Baum soweit runter wie möglich gedrückt:
*(2)* $\sigma$ ist Kommutativ ($\sigma_{C_{1}}(\sigma_{C_{2}})$)