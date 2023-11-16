#### Was ist Kryptographie?
##### "Theorie" der IT-Sicherheit
Aber: Unzählige Anwendungen in der Praxis

#### Klassische vs. Moderne Kryptographie
- Klassisch
	- Sichere Kommunikation über unsichere Kanäle
	- Hauptanwendung: Militär
- Modern
	- Starke Sicherheitsgarantien für Daten und Berechnungen in Anwesenheit eines Angreifers
	- Anwendung in nahezu jedem Lebensbereich

#### Motivation und Ziele der Kryptographie
- Motivation
	- Sichere Kommunikation
- Ziele
	- Vertraulichkeit (Angreifer kann Inhalt einer Nachricht nicht lernen)
	- Integrität (Angreifer kann Nachrichten nicht ändern, ohne dass Änderung erkannt wird)
	- Authentizität (Angreifer kann nicht behaupten), dass eine Nachricht von Alice kam, die diese aber nicht gesendet hat.

#### Wesentlicher Baustein: Schlüssel
- Kurzer Schlüssel (Kryptoverfahren verwenden zufällig gewählte, kurze Schlüssel)
- Symmetrische Kryptograpie: Alle Nutzenden verwenden den gleichen Schlüssel
- Asymmetrische Kryptograpie: 
	- Öffentlicher Schlüssel: z.B. veröffentlicht im Internet
	- Geheimer Schlüssel: Nur einzelnen Nutzenden eines Kryptoverfahren bekannt
#### Kerckhoffs Grundsatz
> Die Sicherheit eines Verschlüsselungsverfahren beruht auf der Geheimhaltung des Schlüssels anstatt auf der Geheimhaltung des Verschlüsselungsalgorithmus

#### Verschlüsselung
![[Bildschirmfoto 2023-10-20 um 22.06.30.png]]

#### Klassische Chiffren
- Shift-Chiffre (Zyklischer Shift um k stellen im Alphabet 
	- Bsp: k = 3: A -> D; B -> E; usw
	- Unsicher: Mithilfe von Brute-Force umgehbar indem man alle 25 anderen möglichen Schlüssel austestet
- Substitutionschiffre
	- Beliebige Permutation $\Pi$ des Eingabealphabets
	- Mithilfe von Buchstabenhäufigkeit in der Deutschen Sprache entschlüsselbar
		- E ist der häufigste Buchstabe in der Deutschen Sprache, wir gucken also, welcher Buchstabe der häufigste im verschlüsselten Text ist und ordnen ihm den Buchstaben E zu

#### Moderne Kryptographie
##### Art vs. Science
- Früher: Kein exaktes Verständnis, was Sicherheit bedeutet, ad-hoc Designs, häufig unsicher
- Heute: Formale Definitionen, systematisches Design, sehr sichere kryptographische Konstruktionen mit Sicherheitsbeweisen
##### Ansatz der Modernen Kryptograpie
1. Formale Definitionen
	- Ziel des Angreifers (z.B. bei Verschlüsselung soll Angreifer nichts über Klartext lernen)
	- Angreifermodell (Was kann der Angreifer tun und sehen)
2. Konstruktion
	- z.B. Konstruktion komplexer Kryptoverfahren aus einfachen Kryptoprimitiven
	- Aus einem Einfachen Baustein (bsp. einer Annahme) entwickeln wir etwas komplizierteres
1. Sicherheitsbeweis
	- Annahme hält -> Kryptoverfahren ist sicher gemäß der formalen Definition
	- Reduktionsbeweis: Angreifer gegen Kryptoverfahren -> Annahme hält nicht
##### Kryptoprimitiven
- Vertraulichkeit
	- Symmetrische Kryptoverfahren
		- One-Time Pad
		- Block-Chiffren & Modes of Operation
	- Asymmetrische Kryptoverfahren
		- RSA Verschlüsselung
		- EIGamal Verschlüsselung
- Integrität und Authentizität
	- Symmetrische Kryptoverfahren
		- MACs
	- Asymmetrische Kryptoverfahren
		- Digitale Signaturen

