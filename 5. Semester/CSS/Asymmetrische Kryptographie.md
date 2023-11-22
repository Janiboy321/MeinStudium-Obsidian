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
#### RSA Funktion
- Parameterwahl GenRSA($n$): Bei Eingabe eines Sicherheitsparameters $n$:
	- Wähle zwei n-bit Primzahlen $p, q$ mit $p \neq q$ 
	- Berechne $N = pq$
	- Wähle $e > 1$ so dass $ggT(e, \varphi(N)) = 1$ (mit $\varphi(N) = (p1)(q-1)$) und berechne $d=e^{-1}\mod \varphi(N)$
	- Ausgabe: (N, e, d)
- Berechnung: $y = x^{e} \mod N$
- Invertierung: $x = y^{d}\mod N$
- Korrektheit: $(x^{e})^{d} \mod N = x \mod N$ da:![[Bildschirmfoto 2023-11-16 um 17.22.41.png]]
#### RSA Annahme
Ohne Kenntnis von $d = e^{-1} \mod \varphi(N)$, ist die Invertierung der RSA Funktion schwer
- Seien $(N, e, d) = GenRSA(n)$
- Wähle $y$ zufällig in $Z^{*}_{N}$
- Gegeben $(N, e, y)$ ist es schwer $x$ zu berechnen, so dass: $x^{e}= y \mod N$

Möglicher Angriff auf RSA Annahme:
- Faktorisiere $N = p \cdot q$
- Berechne $d = e^{-1} \mod \varphi(N)$
$\to$ Schwierigkeit der Faktorisierung ist notwendige Annahme für Sicherheit des RSA Verfahrens

#### Wahl der RSA Parameter
BSI Empfehlung: 
- Faktorisierungsmodulus: 3000 Bits
- Weitere Anforderungen an $p, q, e, d$

#### Textbuch RSA
**Schlüsselerzeugung** (Sicherheitsparameter $n$)
- Berechne $(N, e, d) := GenRSA(n)$
- Ausgabe: $pk = (N, e), sk = (N, d)$

**Verschlüsselung** (Nachricht $m \in Z^{*}_N$)
- $c= m^{e}\mod N$

**Entschlüsselung** (Chiffretext $c \in Z^{*}_N$)
- $m = c^{d} \mod N$

###### Sicherheit des Textbuch RSAs
Nicht IND-CPA sicher:
- Grund: Die Verschlüsselung ist deterministisch
	- Wie kann ein Angreifer das CPA-Spiel gewinnen?
		1. Er wählt zwei Nachrichten $m_{0}, m_{1}$
		2. Er berechnet $c_{0} = Enc(pk, m_{0})$ mit Hilfe des öffentlichen Schlüssels
		3. Er vergleicht den Challenge Chiffretext $c^{*}$ mit $c_{0}$

Weitere Probleme mit Textbuch RSA: 
Das Verschlüsselungsverfahren ist homomorph
- $Enc(pk, m_{0}) \cdot Enc(pk, m_{1}) = Enc(pk, m_{0} \cdot m_{1})$
$\to$ Hauptsächlich Problem für Chosen Ciphertext Sicherheit

### Alternative: Elgamal Verfahren
#### Diskrete Logarithmus Annahme
- Setup: zyklische Gruppe $\mathbb{G}$ der Ordnung $q$ mit Generator $g$ und $q$ prim
- Gegeben: zufälliges $h \in \mathbb{G}$
- Suche: $x$, sodass $g^{x}= h$
- Annahme: Diskreten Logarithmus zu finden ist hart für geeignete Gruppe $\mathbb{G}$

Weiter wichtige Varianten: Computational Diffie Hellman (CDH), Decisional Diffi Hellman (DDH)

#### Elgamal Verschlüsselung
**Öffentliche Parameter**: Gruppe $\mathbb{G}$ der Ordnung $q$ mit Generator $g$

**Schlüsselerzeugung:**
- Wähle zufällig $sk = x \xleftarrow{\$} \mathbb{Z}_q$
- Berechne $pk = g^{x} \in \mathbb{G}$

**Verschlüsselung:**
- Wähle zufällig $r \xleftarrow{\$} \mathbb{Z}_q$
- Berechne $c_{0} = g^{r}$ und $c_{1}=m \cdot pk^{r}$
- Ausgabe $c = (c_{0}, c_{1})$

**Entschlüsselung:**
- $m = c_{1} \cdot c_{0}^{-x}$

Korrektheit:![[Bildschirmfoto 2023-11-16 um 17.55.58.png]]

#### Sicherheit von Elgamal
Ist die ElGamal Verschlüsselung deterministisch? Nein! $c_{0}=g^{r}$ ist zufällig in $\mathbb{G}$

Für geeignete Parameterwahl ist ElGamal IND-CPA sicher unter der DDH Annahme

**Einsatz in der Praxis:** eher selten, da wir stärkere Sicherheitseigenschaften benötigen

### Schlüsselaustausch
##### Wiederholung: Schlüssel in symm. Kryptographie
Symmetrische Kryptographie: Parteien kennen identischen Schlüssel
- Wie kommen Parteien zu diesem Schlüssel
Lösung: Schlüsselaustauschprotokoll basierend auf asymmetrischer Kryptographie
![[Bildschirmfoto 2023-11-16 um 18.00.34.png]]

#### Diffie-Hellman Schlüsselaustausch
Öffentlich: Gruppe $\mathbb{G}$ der Ordnung $q$ mit Generator $g$
![[Bildschirmfoto 2023-11-16 um 18.02.59.png]]

##### Sicherheit des Schlüsselaustauschs
Diskrete Logarithmus Annahme muss hart sein in $\mathbb{G}$!

Angreifer sieht $X, Y$
- Löse diskreten Logarithmus $x = \log_{g}{X}$ 
- Berechne Schlüssel: $K = Y^{x} = (g^y)^{x}=g^{xy}$

Diffie-Hellman Schlüsselaustausch ist sicher unter der DDH Annahme

### Hybride Verschlüsselung
#### Vor- und Nachteile (a)symmetrischer Verschlüsselung
- symmetrische Verschlüsselung
	- Vorteile
		- sehr effizient
		- Verschlüsselung langer Nachrichten möglich
	- Nachteile
		- benötigt gemeinsamen Schlüssel
- asymmetrische Verschlüsselung
	- Vorteile
		- Protokol für Schlüsselaustausch
	- Nachteile
		- Erlauben zunächst nur Verschlüsselung kurzer Nachrichten (z.B. < 3000 Bits für RSA)
		- ineffizienter

Schlüsselaustausch mittels asymmetrischer Verschlüsselungen + Effiziente symmetrische Verschlüsselung der Daten = Hybride Verschlüsselung

#### Ver- und Entschlüsselung
Verschlüsselung:
1. Wähle **kurzen** Schlüssel $k$ für symmetrisches Verfahren
2. Verschlüssle $k$ mit **asymmetrischem** Verfahren unter $pk$
3. Verschlüssle **lange Nachricht** $m$ mit **symmetrischen** Verfahren unter $k$
$c = (PubKeyEnc(pk,k), SymEnc(k, m))$

Entschlüsselung:
1. Entschlüssle kurzen Schlüssel $k$ mit asymmetrischem Verfahren unter $pk$
2. Entschlüssle lange Nachricht $m$ mit symmetrischen Verfahren $pk$

### Signaturen (Motivation und Definition)
#### Physikalische Signaturen
> Unterschrift auf physikalischem Dokument
- Lassen sich leicht fälschen
- Digitale Welt: Fälschung noch leichter
#### Digitale Signaturen
> Digitale Version von physikalischen Signaturen (hängt stark vom Dokument ab)
![[Bildschirmfoto 2023-11-22 um 15.26.05.png]]

### Anwendung für Softwareupdates
- Softwarehersteller signiert Codeupdate
- Benutzer haben Zugriff auf den pk des Softwareherstellers
- Software nur installieren, falls Signatur gültig

### Mehrfachauthentifizierung
![[Bildschirmfoto 2023-11-22 um 15.31.44.png]]

##### funktionale Definition
- Algorithmen: (Gen, Sig, Ver)![[Bildschirmfoto 2023-11-22 um 15.32.31.png]]
- Korrektheit: Die Verifikation einer gültigen Signatur ist erfolgreich:
	$\to$ $Var(pk, m, Sig(sk, m)) = 1$ für alle Nachrichten m und Schlüsselpaare $(pk, sk) \leftarrow Gen$

##### Sicherheit (Informal)
> Angreifer kann keine Signaturen auf neue Nachricht fälschen

Einfache Folgerung: Digitale Signatur hängt stark von Nachricht ab! Sonst: ![[Bildschirmfoto 2023-11-22 um 15.36.19.png]]
##### Folgerung aus Sicherheitspiel:
Der Angreifer gewinnt das Sicherheitsspiel wenn:
1. $m^{*}$ neu ist, d.h. $m^{*} \neq m$ für alle Anfragen $m$ in der ersten Phase des Sicherheitsspiels
2. Signatur $(m^{*}, s^{*})$ ist korrekt, d.h. $Ver(pk, m^{*}(m^{*}, s^{*})) = 1$

**Sicherheit:**
Signaturverfahren ist **EU-CMA sicher**, falls alle "effizienten" Angreifer das Sicherheitsspiel maximal mit Wahrscheinlichkeit $\approx 0$ gewinnen können.

Im gegensatz zu **IND-CPA Sicherheit** ist die Erfolgswahrscheinlichkeit des Angreifers $\approx 0$
- Angreifer kann kein gültiges Nachricht/Signatur-Paar $(m^{*}, s^{*})$ raten
- Tivialer Angriff: Wähle $s^{*} \in \{0,1\}^{\ell}$ zufällig
	$\to$ erfolgreich mit Wahrscheinlichkeit $2^{- \ell}$

#### MACs vs. Signaturen
##### MACs
Wenn eine Person signiert und *eine* zweite Person verifiziert
#### Signaturen
Wenn eine Person signiert und *viele* Personen verifizieren