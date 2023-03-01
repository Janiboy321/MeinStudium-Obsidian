##### Factory Pattern
Sinn:
	Wie kann ich ein Objekt haben, sodass die Unterklassen dieses Objekts definieren können, welche Klasse instantiiert wird?
Beispiel:
	Wir haben verschiedene Dateiformate (PNG, MP3, MP4, usw), welche die konkreten Implementierungen des Interfaces Produkt darstellen. Außerdem haben wir mit MP3Factory eine konkrete Implementierung der abstrakten Klasse Factory (Wessen Methode operation() die abstrakte Methode makeOne() aufruft). IOn dieser Implementierung haben wir die FactoryMethode so Implementiert, dass sie neue Objekte der Klasse MP3 erstellt

##### Abstract Factory Pattern
Beispiel: 
	Wir haben mit HealPack und AmmoPack zwei Implementierung des Interfaces Product. Client ist in unserem Beispiel der Spieler. Jenachdem welche Klasse man spielt, also entweder Healer oder Weaponer, produziert man HealPacks oder eben AmmoPacks. Dies geschieht eben mit den Implementierungen HealPackFactory oder AmmoPackFactory für das interface Factory. 

### Aufgabe 1 ![[IMG_B5E8435C23D6-1.jpeg]]