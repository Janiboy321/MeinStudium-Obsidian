#### Häufige Fehler bei LL(k) Parsern
Hinweis: LL(k)-Parser sind Top-Down Parser, welche von Links nach rechts arbeiten und k Tokens vorausschauen können

###### Grammatik ist nicht LL(1)
![[Bildschirmfoto 2023-11-28 um 18.05.58.png]]
Es gibt zweimal identifier auf der rechten Seite

##### Linksausklammern vergessen![[Bildschirmfoto 2023-11-28 um 18.14.48.png]]
![[Bildschirmfoto 2023-11-28 um 18.15.45.png]]
##### Linksrekursion nicht beseitigt
![[Bildschirmfoto 2023-11-28 um 18.17.50.png]]
