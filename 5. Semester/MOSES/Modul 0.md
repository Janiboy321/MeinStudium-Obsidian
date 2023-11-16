#### Was ist ein Modell?
- Eine abstrakte Darstellung der realen Welt
*Beispiele:*
- Liniennetzplan![[Bildschirmfoto 2023-10-23 um 15.02.32.png]]
	- Hervorgehoben: Linien, Haltestellen ,Tarifzonen
	- Weggelassen: RMV Verbindungen außerhalb des abgebildeten Bereichs, andere Verkehrsmittel,  geographische Begebenheiten
- Fahrplan ![[Bildschirmfoto 2023-10-23 um 15.04.21.png]]
	- Hervorgehoben: Abfahrtszeiten, weitere Haltestellen, Linie F, Haltestelle Alexanderstraße, Richtung Haaststraße
	- Weggelassen: Gegenrichtung, andere Haltestellen, andere Busse an dieser Haltestelle

> Ein Modell ist absichtlich nicht originalgetreu, um bestimmte Aspekte der Realität deutlicher hervorzuheben.

> Unterschiedliche Aspekte der Realität können durch unterschiedliche Modelle verdeutlicht werden

##### Von der Realität zum Modell 
![[Bildschirmfoto 2023-10-23 um 15.19.48.png]]
##### Analyse am Modell ![[Bildschirmfoto 2023-10-24 um 14.00.13.png]]

##### Vom Modell in die ![[Bildschirmfoto 2023-10-24 um 14.02.58.png]]

> Eigenschaften eines Modells sollten der Realität entsprechen, dann sind sie *Angemessen*

#### Beispiel einer formalen Modellierung:
Ein Mann steht mit einem Wolf, einer Ziege und einem Kohlkopf am linken Ufer eines Flusses, welchen er überqueren will. Er hat ein Boot, das gerade groß genug ist, ihn und ein weiteres Objekt zu transportieren, so dass er immer nur eines der drei mit sich hinübernehmen kann. Falls der Mann allerdings den Wolf mit der Ziege oder die Ziege mit dem Kohlkopf an einem Ufer zurücklässt, wird einer gefressen

##### Wie kann man formale Modellierung zur Lösung einsetzen?
- Wie kann man das Szenario formal modellieren?
- Wie kann man die Frage und Antworten formal modellieren?
- Wie kann man eine Lösung am Modell entwickeln?
- Wie ist die Lösung in der Realität zu interpretieren

##### Formale Modellierung
- *Identifikation* relevanter Objekte im Szenario
	- Mann, Wolf, Ziege, Kohlkopf
- *Modellierung* der Objekte durch eine Menge von Symbolen
	- $O = \{m, w, z, k\}$
- *Identifikation* relevanter Aspekte einer Situation im Szenario
	- Welches Objekt befindet sich an welchem Ufer?
- *Modellierung* einer Situation durch ein Paar (L, R) von Mengen
	- Menge **L** enthält die Symbole der Objekte welche am Linken Ufer stehen
	- Menge **R** enthält die Symbole der Objekte welche am rechten Ufer stehen
	Beispiel: Der Anfangszustand $z_0$ wird durch das Paar $(L_0, R_0)$ modelliert, wobei $L_{0}=\{m, w, z, k\}$ und $R_{0}= \{\}$ gelten.
- *Identifikation* von Beschränkungen an möglichen Situationen
	- Keines der Objekte kann sich an mehr als einem Ufer befinden
	- Der Mann und der Wolf können nicht verschwinden
- *Modellierung* möglicher Situationen durch Menge von Paaren
	- Menge von Zuständen
		$Z:= \{(L, R) | L \subseteq O \land R \subseteq O \land L \cap R = \{\} \land \{m, w\} \subseteq L \cup R \}$ 
- *Identifikation* relevanter Aktionen im Szenario
	- Transport von Objekten mit dem Boot zum anderen Ufer
- *Identifikation* von Beschränkungen an relevanten Aktionen
	- Das Boot kann nicht ohne den Mann fahren
	- Das Boot kann den Mann und maximal ein weiteres Objekt aufnehmen.
- *Modellierung* relevanter Aktionen durch eine Menge von Termen
	- Menge von Ereignissen
		$E:= \{ \text{fahre}(T) | T \subseteq \{m, w, z, k\} \land m \in T \land |T| \leq 2 \}$
	Beispiel: 
		- Die Ereignisse $\text{fahre}(\{m\})$ und $\text{fahre}(\{m, z\})$, modellieren zulässige Aktionen.
		- $\text{fahre}(\{m, z, w\})$ und $\text{fahre}(\{w\})$ modellieren unzulässige Aktionen
- *Identifikation* von Vorbedingungen der Aktionen
	- Die durch $\text{fahre}(T)$ modellierte Aktion ist zulässig wenn alle Objekte in T an einem Ufer sind und nicht Wolf & Ziege oder Ziege & Kohlkopf zurückbleiben
- *Identifikation* von Nachbedingungen der Aktionen
	- Nach dem Ereignis $\text{fahre}(T)$ befinden sich die Objekte in $T$ am anderen Ufer
- *Modellierung* der Effekte von Aktionen durch Zustandsübergänge
	- Zustandsübergangsrelation $\to \subseteq Z \times E \times Z$![[Bildschirmfoto 2023-10-24 um 15.21.44.png]]
	- Interpretation: Der Zustand $(L', R')$ resultiert durch Ausführen der Aktion $\text{fahre}(T)$ im Zustand $(L, R)$
	- Wir schreiben auch $(L, R) \longrightarrow (L', R')$ statt $((L,R), \text{fahre}(Z), (L', R')) \in \to$ 
	Beispiel:
		- $(\{m, w, z, k\}, \{\}) \xrightarrow{\mbox{\tiny{fahre({m, z})}}}(\{w, k\}, \{m, z\})$ modelliert einen zulässigen Zustandsübergang
		- Interpretation: "Der Mann fährt mit der Ziege vom linken zum rechten Ufer"

##### Mögliche Graphische Darstellung ![[Bildschirmfoto 2023-10-24 um 15.52.34.png]]

##### Zusammenfassung
- Problemstellung im Modell
	- Gibt es eine Folge von Aktionen, mit der man vom Anfangszustand $(\{m, w, z, k\}, \{\})$ in den Zustand $(\{\}, \{m , w, z, k\})$ gelangen kann?
- Antwort im Modell
	- Ja, z.B. die Folge $$( fahre(\{𝑚, 𝑧\}), fahre(\{𝑚\}), fahre(\{𝑚, 𝑘\}), fahre(\{𝑚, 𝑧\}), fahre(\{𝑚, 𝑤\}), fahre(\{𝑚\}), fahre(\{𝑚, 𝑧\}) )$$
- Interpretation:
	- Mann fährt Ziege nach Rechts
	- Mann fährt nach links
	- Mann fährt Kohl nach rechts
	- Mann fährt Ziege nach links
	- Mann fährt Wolf nach recht
	- Mann fährt nach links
	- Mann fährt Ziege nach rechts

##### Vorgangsweise:
1. Ausgangspunkt war eine informelle, aber präzise Beschreibung der Problemstellung.
2. Alle relevanten Objekte wurden identifiziert und dann durch Symbole formal modelliert.
3. Situationen wurden durch Zustände, d.h. Paare von Mengen, formal modelliert.
4. Bedingungen an mögliche Situationen wurden identifiziert und die Teilmenge 𝑍 der möglichen Zustände wurde definiert.
5. Alle relevanten Aktionen wurden identifiziert und durch Ereignisse der Form fahre(𝑇) formal modelliert.
6. Bedingungen an zulässige Aktionen wurden identifiziert und die Teilmenge 𝐸 der zulässigen Ereignisse wurde definiert.
7. Die Vor- und Nachbedingung der Aktionen wurden identifiziert und durch die Zustandsübergangsrelation $\to$ formal modelliert.
8. Die Fragestellung wurde am Modell unter Verwendung einer graphischen Veranschaulichung untersucht.
9. Die Lösung im Modell wurde in der Realität interpretiert.

##### Dazu:
- Es kann mehrere sinnvolle formale Modelle geben
- Kleine Änderungen an Modellen können große Auswirkungen haben
	- Ein Sinnvolles Modell kann durch eine kleine Änderung unsinnig werden

#### Modelle auf unterschiedlichen Abstraktionsstufen
![[Bildschirmfoto 2023-10-24 um 15.56.28.png]]

#### Komponentenbasierte Modellierung
![[Bildschirmfoto 2023-10-24 um 15.57.13.png]]

#### Einsatz formaler Methoden
![[Bildschirmfoto 2023-10-24 um 15.57.50.png]]