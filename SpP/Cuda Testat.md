##### Abgabe: 14.02.2023

## Aufgabe 8
##### Ziel:Anzahl der Schnitttests zwischen Dreiecken und Sichtstrahlen minimieren 
- Dafür generiert der Code eine Hüllkugel, die jeweils eine gewisse Menge an Dreiecken umschließt.
- Diese kann einen Teil eines Modells oder das ganze Modell einschließen
- Die Funktion `__device__ bool traceRay` prüft für jeden Sichtstrahl mithilfe der Funktion `__device__ bool rayInteresectSphere` ob diese Hüllkugel getroffen wird
- Nur falls sie getroffen wird, werden die Dreiecke des Meshs getestet
##### Gegeben:
- Es gibt einen Sichtstrahl $I(\lambda) = o + \lambda v$
	- Anfangspunkt $o = (o.x, o.y, o.z)$
	- Richtungsvektor $v = (r.x, r.y, r.z)$
- Es gibt die Hüllkugel $s$
	- Mittelpunkt $c = (s.x, s.y, s.z)$
	- Radius $r = s.w$
##### Formeln:
- $I(\lambda) = o + \lambda v$
- $(p-c) \cdot (p-c) = r^2$
	- setzt man $i$ für $p$ ein, multipliziert aus und sortiert kommt folgendes raus
		- $\lambda = - \beta \pm \sqrt{\beta ^2 - \gamma}$
			- $\beta = v \cdot (o-c)$
			- $\gamma = (o-c) \cdot (o-c) - r^2$
- Sollte die Formel mindestens ein Ergeniss haben, so schneided der Sichstrahl die Hüllkugel
##### Idee:
- Ist das Ergebnis in der Wurzel kleiner als 0, gibt die Methode false zurück, da die Formel dann kein Ergebnis liefert
	- Ja, der Part ist klar
- Weiter?