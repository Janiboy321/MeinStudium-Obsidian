#### Asymmetrische Kryptographie
> Es gibt ein Schlüsselpaar (Für Ver- und Entschlüsselung)

![[Bildschirmfoto 2023-11-16 um 15.37.34.png]]
Bob erstell ein Schlüsselpaar und veröffentlicht ok, dadurch ist kein Schlüsseltausch notwendig
###### Synonym:#
- Symmetrisch = *private Key*
- Asymmetrisch = public Key
##### Anzahl an Schlüsseln
- Symmetrische Kryptographie ![[Bildschirmfoto 2023-11-16 um 16.48.35.png]]
	- Schlüssel zwischen jedem Paar aus Parteien
	- Bei $n$ Parteien: $\frac{n \cdot (n - 1)}{2}$ Schlüssel
- Asymmetrische Kryptographie![[Bildschirmfoto 2023-11-16 um 16.50.30.png]]
	- Ein Öffentlicher Schlüssel pro Partei
	- Bei n Parteien: n Schlüsselpaare

### Asymmetrische Chiffren
##### Funktionale Definition
![[Bildschirmfoto 2023-11-16 um 16.52.39.png]]

Korrektheit: Die Entschlüsselung eines gültigen Chiffretexts resultiert in die original verschlüsselte Nachricht
$$\to Dec(sk, Enc(pk, m)) = m \text{ für alle Nachrichten } m \text{ und Schlüsselpaare } (pk, sk) \leftarrow Gen$$

##### Sicherheitsdefinitionen
- Was bedeutet sicher?
	- Angreifer lernt "nichts neues" über Nachricht $m$

- Angreifermodell: Was kann der Angreifer tun und sehen?
	- Öffentlicher Schlüssel ist auch für Angreifende sichtbar und dies genügt, um Chiffretext zu erstellen
		$\to$ Angreifende können beliebige Klartexte selber verschlüsseln
	- Stärkeres Modell: Angreifer wählt zusätzlich Chiffretext und erhält zugehörige Klartexte, z.B. Angreifer hat zugriff auf Smart Card, die für den Angreifer entschlüsseln kann

$\to$ Wie können wir das Formalisieren
![[Bildschirmfoto 2023-11-16 um 17.05.24.png]]
Sicherheit: Asymmetrische Chiffre ist **IND-CPA** sicher, falls alle "effizienten" Angreifer das Sicherheitsspiel maximal mit Wahrscheinlichkeit $\approx \frac{1}{2}$ gewinnen können

### RSA
- Parameterwahl GenRSA($n$): Bei Eingabe eines Sicherheitsparameters $n$:
	- Wähle zwei n-bit Primzahlen $p, q$ mit $p \neq q$ 
	- Berechne $N = pq$
	- Wähle $e > 1$ so dass $ggT(e, \varphi(N)) = 1$ (mit $\varphi(N) = (p1)(q-1)$) und berechne $d=e^{-1}\mod \varphi(N)$
	- Ausgabe: (N, e, d)
- Berechnung: $y = x^{e} \mod N$
- Invertierung: $x = y^{d}\mod N$
- Korrektheit: $(x^{e})^{d} \mod N = x \mod N$ da:![[Bildschirmfoto 2023-11-16 um 17.22.41.png]]
#### Annahme