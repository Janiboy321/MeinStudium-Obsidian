###### Was ist ein Token?
- Atomares Symbol des Progamms
- Verwendung zwischen Scanner und Parser
- Kann auch aus mehreren Zeichen bestehen
- Zeichen selbst sind i.d.R uninteressant, Ausnahmen:
	- Bezeichnernamen
	- Konstante Werte (Zahlen, Zeichen), sog. Literale
```java
class Token {
	TokenKind kind; // enum TokenKind{...}
	String spelling;
	SourcsPosition position; Z // Zeilennummer, Spalte
}
```

###### Übersetzen von Grammatiken in Code
1. $A \to aB*C$
```java
private A parseA(){
	var loc = currentToken.sourceLocation;
	accept("a")
	while(currentToken.type != C){
		parseB;
	}
}
```