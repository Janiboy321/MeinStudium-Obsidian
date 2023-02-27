## Aufgabe 3

### a) (Kopplungen bestimmen)

java.lang.object
java.net.InetAddress
com.google.common.collect.Range
org.example.app.types.UserType
java.io.Serializable
UserType
ExampleAppGroup
java.lang.system
StringBuilder
Comparable
Range
NullPointerException
RuntimeException
String
Long
java.net.Inet6Address


| Nr  | Beschreibung | Wertebelegung       | Erwartetes Ergebnis  |
| --- | ------------ | ------------------- | -------------------- |
| 4   | Null test    | arr = null, key = 0 | NullPointerException |
| 5   |              |                     |                      |

Testfall 1
5 - false
-> return -1 (Zeile 16)

Testfall 2
5 - true
10 - true
5 - true
10 - false
-> return 0 (Zeile 13)

Testfall 3
5 - true
10 - true
5 - false 
-> return -1 (Zeile 16)

10 