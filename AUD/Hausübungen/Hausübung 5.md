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
	Da die "2" ein halbblatt ist, muss sie schwarz gefärbt sein. Die "1" muss dementsprechend rot gefärbt werden, damit die Schwarhöhe ab "2" auf beiden seiten gleich ist. Jetzt wissen wir, da die Wurzel immer schwarz sein muss dass die Wurzel eine Schwarzöhe von 2 besitzt. Gehen wir jetzt den rechten Teilbaum (ab "5") durch, fällt relativ schnell auf, dass der Baum eine Schwarzhöhe $> 2$ haben muss:
	Färben wir "5" Schwarz, muss jeder einzelne Knoten darunter rot sein, was aber nicht funktioniert, da sonst die nicht-rot-rot Regel verletzt wäre. Also färben wir "5" rot und müssen dann "4" und "10" schwarz färben. Um die Schwarzhöhe aufrecht zu erhalten, müssen wir jetzt alle Knoten unterhalb "10" rot färben, was wieder zur verletzung der nicht-rot-rot Regel führen würde, somit ist es unmöglich für diesen Baum eine korrekte Schwarz-Rot-Färbung zu finden.

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

##### c)
**Preorder:**
	a) *3, 2, 1, 5, 4, 10, 8, 7, 6, 9, 11*
	b) *5, 3, 2, 1, 4, 10, 7, 6, 8, 9, 11*
**Inorder:**
	a) *1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11*
	b) *1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11*
**Postorder:**
	a) *1, 2, 4, 6, 7, 9, 8, 11, 10, 5, 3*

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