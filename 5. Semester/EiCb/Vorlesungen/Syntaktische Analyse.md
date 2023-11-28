### Beispiel für nicht-LL(1) Grammatik
- Aus Algol Grammatik
	Block ::= begin Declaration (; Declaration)$*$; Command end

- Prüfe Regel für X$*$ 
	- starters$[[$; Declaration $]]$ = {;}
	- follow$[[$(; Declaration)$*]]$ = {;}
	- starters$[[$; Declaration$]]\ \cap$ follow$[[$(; Declaration)$*]]$ ≠ $\emptyset$ 

- Produktion ist aber transformierbar
	Block ::= begin Declaration ; (Declaration ;) $*$ Command end

- Annahme: starters$[[$Declaration;$]]$ $\cap$ starters$[[$Command$]]$ = $\emptyset$

### LL(k)-Parser
- Konstruktion von Top-Down-Parsern gut automatisierbar
- Für Java beispielsweise
	- ANTLR: LL(k) bis LL($*$)
	- JavaCC: LL(k)
	- 