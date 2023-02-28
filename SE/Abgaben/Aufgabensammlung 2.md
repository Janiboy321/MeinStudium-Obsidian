##### Factory Pattern
Sinn:
	Wie kann ich ein Objekt haben, sodass die Unterklassen dieses Objekts definieren können, welche Klasse instantiiert wird?
Beispiel:
	Wir haben verschiedene Dateiformate (PNG, MP3, MP4, usw), welche die konkreten Implementierungen des Interfaces Produkt darstellen. Außerdem haben wir mit MP3Factory eine konkrete Implementierung der abstrakten Klasse Factory (Wessen Methode operation() die abstrakte Methode makeOne() aufruft). IOn dieser Implementierung haben wir die FactoryMethode so Implementiert, dass sie neue Objekte der Klasse MP3 erstellt


### Aufgabe 1
