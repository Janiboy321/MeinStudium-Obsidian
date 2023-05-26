#### H1
##### a)
![[Pasted image 20230523103859.png]]
![[Pasted image 20230523103925.png]]
![[Pasted image 20230523103936.png]]
![[Pasted image 20230523104010.png]]
![[Pasted image 20230523104142.png]]
![[Pasted image 20230523104206.png]]
![[Pasted image 20230523104235.png]]
![[Pasted image 20230523104315.png]]
![[Pasted image 20230523104907.png]]
![[Pasted image 20230523104930.png]]
![[Pasted image 20230523105003.png]]
Es existiert keine mögliche Schwarz-Rot-Färbung für den Baum:
	Da die "2" ein halbblatt ist, muss sie schwarz gefärbt sein. Die "1" m

##### b)
![[Pasted image 20230523115336.png]]
![[Pasted image 20230523222118.png]]
![[Pasted image 20230523225653.png]]
![[Pasted image 20230523230311.png]]
![[Pasted image 20230523230512.png]]
![[Pasted image 20230523230608.png]]
![[Pasted image 20230523230747.png]]
![[Pasted image 20230523231136.png]]
![[Pasted image 20230523231300.png]]
![[Pasted image 20230523231453.png]]
![[Pasted image 20230523231752.png]]

#### H2
##### a)
Zu zeigen:
	Ein Baum mit $n$ Knoten hat genau $n-1$ Kanten

I.A.:
	$n = 1 \rightarrow 1 - 1 = 0$
	Diese Aussage stimmt, da ein Baum mit nur einem Knoten keine Kante zur Verbindung mit einem anderen Knoten benötigt

I.S.:
	$n = n + 1$

I.V.:
	Ein Baum mit $n$ Knoten hat genau $n - 1$ Kanten

I.B.: 
	Ein Baum mit $n+1$ Knoten hat genau $n$ Knoten
	Fügt man einem Baum mit $n$ Knoten einen Knoten hinzu, fügt man per Definition auch immer eine Kante hinzu. Nach *I.V* besitzt der Baum schon n-1 Kanten. Nach Hinzufügen eines Knotens hat man also eine Kante mehr: $n - 1 + 1 = n$
	Darauf folgt, dass die zu beweisende AUssage wahr ist.

##### b)
Die Zeitkomplexität wäre in beiden Fällen $O(n)$, da wir bei beiden  