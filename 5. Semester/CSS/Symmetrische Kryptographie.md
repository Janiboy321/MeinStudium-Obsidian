![[Symmetrische Kryptographie - Komplett 2.pdf]]

### Symmetrische Kryptographie
- Es gibt nur einen Schlüssel
	- Alle Parteien haben den gleichen Schlüssel (Sendende und Empfangende)
- Einigung auf einen geheimen Schlüssel
	- Physikalisches Treffen
	- Kryptographisches Protokoll
### Definition von Symmetrischen Chiffren
- Beschreibt Input/Output-Verhalten der Algorithmen
- Algorithmen: (Generator, Encoder, Decoder) *(Grafik auf Folie 5)*
- Wir brauchen eine Korrektheitseigenschaft
	> Die Entschlüsselung eines gültigen Chiffretexts resultiert in die original verschlüsselte Nachricht
- Effizienz
	- Verschlüsselung und Entschlüsselung sind effizient (> 1GB/s)

### Sicherheitsdefinition
- Ziel des Angreifers (Was ist ein erfolgreicher Angriff?)
	- Naiv: Der Angreifer lernt den Schlüssel K nicht -> **Sehr unsicher**
	- Kryptographie: Angreifer *lernt* **nichts neues** über **m**

- Angreifermodell (Was kann der Angreifer tun und sehen)
	- Angreifer lernt nur Chiffretexte (bsp. durch Abhören des Hörsaals)
	- Lernt paare von Klartexten/Chiffretexten (bsp. Bekannter teil der Verschlüsselten Nachricht kann bekannt sein)
	- Angreifer wählt Klartexte und lernt zugehörige Chiffretexte (bsp. Nutzer davon überzeugen Nachricht seiner Wahl zu entschlüsseln) (Chosen plaintext attack)

### Sicherheitsspiel
In der Kryptographie definiert man Sicherheit durch ein Spiel zwischen Angreifer und Nutzer.

**Wie funktioniert dieses Spiel?**
1. *Angreiferin* senden eine Nachricht $m$ an *Nutzerin*
2. *Nutzerin* erzeugt nun einen Schlüssel $k$
3. *Nutzerin* schickt der *Angreiferin* nun die mit dem Schlüssel $k$ verschlüsselte Nachricht $m$ als Chiffretext $c$ ($c = Enc(k,m )$) - Das kann die *Angreiferin* nun beliebig oft wiederholen
5. Am Ende dieses Schrittes muss die *Angreiferin* zwei Klartexte gleicher länge $M_{0}$ und $M_{1}$ ausgeben
6. Jetzt zieht die Nutzerin ein zufälliges Bit $b$ (0 oder 1) und verschlüsselt $M_{b}$. Diesen Geheimtext erhält die Angreiferin
7. Die Angreiferin darf jetzt beliebige Berechnungen oder Verschlüsselungen ausführen und muss am Ende ein $b'$ ausgeben
8. Die Angreiferin hat das Spiel gewonnen wenn $b = b'$ 
**Die Symmetrische Chiffre ist IND-CPA sicher, falls alle "effizienten" Angreifenden das Spiel mit einer max. Wahrscheinlichkeit von $\approx \frac{1}{2}$ gewinnen können**
##### IND-CPA-Sicher (Ciphertext Indistinguishability)
Was bedeutet Ciphertext Indistinguishability?
- Englisch für ununterscheidbarkeit von Geheimtexten

Ist ein Verschlüsselungsverfahren IND-CPA sicher, dann:
- Das beste was die Angreiferin tun kann, ist b raten
- Angreiferin kann Chiffretext $c^{*}$ im wesentlichen ignorieren
- Chiffretext $c^{*}$ gibt keine zusätzlichen Informationen über verschlüsselte Nachricht
### Wie zeigen wir (un)sicherheiten?
Wir machen über Angreifende keine Annahmen, außer dass sie effizient sind!

- Was bedeutet "Nicht effizient"?
	- beispielsweise Angriffe mit exponentieller Laufzeit
- Was bedeutet "effizent"?
	- Wird in dieser Vorlesung nicht genauer spezifiziert

Wie zeigt man unsicher (un)sicherheit?
- Konstruiere effizienten Angreifer der mit der Wahrscheinlichkeit $> \frac{1}{2}$ das Sicherheitsspiel gewinnt

Wie zeigt man sicher (un)sicherheit?
- Zeige, dass alle effizienten Angreifenden das Sicherheitsspiel mit Wahrscheinlichkeit $< \frac{1}{2}$ gewinnen
### One-Time Pad
Verschlüsselung von Bitstrings der Länge n
- *Gen*: Ausgabe zufälliger Schlüssek $k \leftarrow \{0, 1\}^{n}$
- *Enc*: Für $m \in M$: Ausgabe $Enc(k, m) = k \oplus m$
- *Dec*: Für $c \in C$: Ausgabe $Dec(k,c) = k \oplus c$ 

##### Wie sicher ist OTP
- Nicht CPA-Sicher
- Sicher gegen unbeschränkte Angreifer

**Aber wichtig:** OTP Ist unsicher, verwendet man einen Schlüssel mehrmals, denn es gilt: $c_{0}\oplus c_{1} = m_{0} \oplus m_{1}$

##### Nachteile von OTP
1. Der Schlüssel ist genauso lang wie die Nachricht
2. Der Schlüssel kann nur einmal benutzt werden
3. Sicherheit im beschränkten Angreifermodell

- Anwendung: Heißer Draht (Verschlüsselungsmethode)
	- -> Wikipedia

### Block Chiffre
Ver- und Entschlüsselung von Nachrichten bzw. Chiffretextblöcke mit fixer länge
![[Bildschirmfoto 2023-11-03 um 15.43.29.png]]
- Blocklänge $n = |m| = |c|$: häufig 64 bis 128 bits
- Schlüssellänge $k$: häufig 128 bis 256 bits
###### Unterschied zu OTP:
Der Schlüssel kann wiederverwendet werden
##### Eigenschaften von Blockchiffren
- Für jede Nachricht $M$ und jeden Schlüssel $K$ gilt korrektheit
- Sie sind Effizient (Enc. und Dec. sollte in Mikrosekunden berechenbar sein)
- Sicherheit, da der Angreifer nicht zwischen der Verschlüsselten Nachricht und einer zufälligen Permutation unterscheiden kann

### Data Encryption Standard (DES)
![[Bildschirmfoto 2023-11-03 um 15.49.34.png]]
- Blocklänge $n = 64$ Bits
- Schlüssellänge $k = 56 Bits$

##### DES: Angriffe
Theoretische Angriffe: Differenzielle und lineare Kryptoanalyse
> DES bietet Schutz gegen differenzielle Kryptoanalyse
###### Hauptschwachpunkt
Es gibt nur einen kurzen Schlüssel (nur 56 Bit), deshalb ist ein Brute-Force Angriff möglich. Ein DES Cracker bricht DES in wenigen Tagen
###### Probleme
- Nicht IND-CPA sicher
- Unmöglich Nachrichten beliebiger Länge zu verschlüsseln
### Modes of Operation
**Ziel**: Verschlüsselung von Nachrichten beliebiger länge
- Ohne Vergrößerung des Chiffretexts
- Blockchiffren können nicht direkt für die Verschlüsselung benutzt werden
- Sie werden immer in bestimmten "**Modes of Operations**" genutzt
	1. Electronic Codebook (ECB) Modus $\leftarrow$ nicht sicher![[Bildschirmfoto 2023-11-03 um 20.42.37.png]]
		- Schwäche: ECB Modus ist deterministisch
			- $M_{1} = M_{2} \rightarrow C_{1} = C_{2}$
	2. Cipher-Block Chaining (CDC) Modus![[Bildschirmfoto 2023-11-03 um 20.46.20.png]]![[Bildschirmfoto 2023-11-03 um 20.46.44.png]]
		- $M_{1} = M_{2}$ impliziert nicht automatisch $C_{1}= C_2$ da ein Zufälliger Anfangswert (IV) verwendet wird
		- CBC ist also sicher, wenn es richtig verwendet wird
	3. Counter (CTR) Modus![[Bildschirmfoto 2023-11-03 um 20.56.39.png]]![[Bildschirmfoto 2023-11-03 um 20.58.19.png]]
		- Idee: Man verwendet die Ausgabe der Blockchiffre als One-Time-Pad 
	...
##### Vergleich der Modi CBC und CTR
- CBC
	- Fehlerresistenz
		- Fehler verbreiten sich nicht über mehr als zwei Blöcke
	- Parallelisierung
		- Verschlüsselung: Nein 
		- Entschlüsselung: Ja
	- Sicherheit
		- Ja, aber Achtung bei Wahl des Paddings
- CTR
	- Fehlerresistenz
		- Fehler wirken sich nur auf den aktuellen Block aus
	- Parallelisierung
		- Verschlüsselung: Ja
		- Entschlüsselung: Ja

### Kryptographische Hashfunktionen
**Eingabe**: Nachricht von beliebiger Menge
**Ausgabe**: Chiffretext mit fixer Länge

##### Definition
Eine Hashfunktion $H: \{0,1\}^{*} \to \{0,1\}^{n}$ bildet von einer großen Definitionsmenge auf einen kleinen Bildbereich ab
##### Sicherheitsdefintionen![[Bildschirmfoto 2023-11-03 um 21.24.52.png]]
- Preimage resitance
	- Gegeben h ist es schwer $m'$ zu finden, so dass $H(m') = h$
- Second Preimage resitsance
	- Gegeben h ist es schwer $m' \neq m$ zu finden, so dass $H(m') = h$
- Collision resistance
	- Es gilt: $h := H(m') = H(m)$
##### Kollisionen
$H: \{0,1\}^{*} \to \{0,1\}^{n}$ bildet von einer großen Definitionsmenge auf einen kleinen Bildbereich ab.
**Problem?** $\rightarrow$ Da die Definitionsmenge größer als der Bildbereich ist, existieren immer Kollisionen
![[Bildschirmfoto 2023-11-03 um 21.31.31.png]]

**Angriffe**:
1. Generischer Brute-Force Angriff
	- $|H(x)| = n Bits$
	- Nach ca. $\sqrt{2^{n}} = 2^{\frac{n}{2}}$: Wahrscheinlichkeit eine Kollision zu finden ist $\geq \frac{1}{2}$ 
- Kryptoanalyse
	- MD5 Kollision in $2^{24.1}$ Schritten: Wenige Sekunden auf modernem PC
	- SHA1: Zwei kollidierende PDF Dokumente berechnet

### Message Authentication Codes
> Verschlüsselung Garantiert nicht Integrität

##### Schwäche des ECB Modes
> Der Angreifer kann Sinnvolle Veränderungen am Klartext vornehmen, ohne dass Empfänger das erkennen kann

Was wird benötigt? $\to$ **Message Authentication Codes (MACs)
- Algorithmen (Gen, Mac, Vrfy)
![[Bildschirmfoto 2023-11-03 um 21.43.26.png]]
- Korrektheit
	- Die Verifizierung eines valider Tag $t$ für $m$ und $k$ resultiert in $b = 1$
		$\Rightarrow$ $Vrfy_{k}(m, Mac_{k}(m)) = 1$ für alle Nachrichten $m$ und Schlüssel $k \leftarrow Gen$
- Effizienz
	- Authentifizierung und Verifizierung sind Effizient (> 10GB/s)

##### Sicherheitsdefinition
- Ziel des Angreifers: Was ist ein erfolgreicher Angriff?
	- Naive Option: Angreifer lernt den Schlüssel $k$ nicht 
	- In der Kryptographie: Angreifer kann keine validen Tag $t$ für $m$ erzeugen
- Arten von MACs
	- Informationstheoretisch sichere MACs $\rightarrow$ nicht effizient für Authentifizierung von vielen Nachrichten
	- Komplexitätstheoretisch sichere MACs
		- Für Nachrichten fixer Länge
		- Für Nachrichten mit beliebiger Länge (z.B. CBC-MAC und HMAC)

#### CBC-MAC
Sei $F_{K}: \{0,1\}^{n} \times \{0,1\}^{n} \to \{0,1\}^{n}$ ein Blockchiffre, $CBC - MAC_{k}(m_{1}, ..., m_{d})$ ist definiert wie folgt:
![[Bildschirmfoto 2023-11-03 um 21.56.11.png]]
**Wichtig: CBC-MAC ist nur sicher für Nachrichten der gleichen Länge

#### HMAC
Trivialer Ansatz: $MAC_{k}(y) = H(k||y)$
$\Rightarrow$ Diese Konstruktion ist aber nur sicher für bestimmte Hashfunktionen

**Besser:** Nutze HMAC $$MAC_{k}(y) = H(k \oplus op || H(k \oplus ip||m))$$
- $op$: Outer Padding; $ip$: Inner Padding

### Authentifizierte Verschlüsselung
Ein Angreifer sollte nicht ...
- ... nützliche Informationen über den Klartext lernen
- ... irgendwelche Änderungen am Klartext vornehmen können

##### "ENCRYPT-THEN-MAC"![[Bildschirmfoto 2023-11-03 um 22.03.09.png]]
##### "MAC-THEN-ENCRYPT"
- ENCRYPT-THEN-MAC
	- Beweisbar sicher
	- Nur Authentische Chiffretexte werden entschlüsselt
- MAC-THEN-ENCRYPT
	- Konkrete Angriffe bekannt
	- Nutzen aus, dass auch dann entschlüsselt wird, falls Chiffretext verändert wurde
