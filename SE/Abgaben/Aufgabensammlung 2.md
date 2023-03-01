##### Factory Pattern
Sinn:
	Wie kann ich ein Objekt haben, sodass die Unterklassen dieses Objekts definieren können, welche Klasse instantiiert wird?
Beispiel:
	Wir haben verschiedene Dateiformate (PNG, MP3, MP4, usw), welche die konkreten Implementierungen des Interfaces Produkt darstellen. Außerdem haben wir mit MP3Factory eine konkrete Implementierung der abstrakten Klasse Factory (Wessen Methode operation() die abstrakte Methode makeOne() aufruft). IOn dieser Implementierung haben wir die FactoryMethode so Implementiert, dass sie neue Objekte der Klasse MP3 erstellt

##### Abstract Factory Pattern
Beispiel: 
	Wir haben mit HealPack und AmmoPack zwei Implementierung des Interfaces Product. Client ist in unserem Beispiel der Spieler. Jenachdem welche Klasse man spielt, also entweder Healer oder Weaponer, produziert man HealPacks oder eben AmmoPacks. Dies geschieht eben mit den Implementierungen HealPackFactory oder AmmoPackFactory für das interface Factory. 

### Aufgabe 1 
**a)**![[IMG_B5E8435C23D6-1.jpeg]]
**b)**
```java
public Section createSection(){
	return new HTMLSection();
}
```
**c)**
```java
public documentEditor(String docType){
	if(docType == "html"){
		factory = new HTMLFactory;
	}
	else if(docType == "latex"){
		factory = new LATEXFactory;
	}
	else{
		throw new RuntimeException("Dateiformat unbekannt");
	}
}
```
**d)**
```java
protected void addSectionToDocument(Document document, String title){
	Section section = factory.createSection();
	section.setTitle(title);
	document.assSection(section);
}
```
**e)**
- Abstrakte Produkte
	- Document
	- Section
- Konkrete Implementierungen der abstrakten Produkte
	- HTMLDocument
	- HTMLSection
	- LATEXDocument
	- LATEXSection
- Abstrakte Fabrik
	- DocFactory
- Konkrete Implementierungen der abstrakten Fabrik
	- HTMLFactory
	- LATEXFactory
- Methoden zum erstellen von Produkten:
	- createDocument();
	- createSection();

### Aufgabe 2
**a)**
Statement Coverage:
| Test Case magic(a, b, c) | Erwartetes Ergebniss | Zeilennummer |
| ------------------------ | -------------------- | ------------ |
| true, true, ""           | 2                    | 3, 6, 12     |
| false, false, ""         | -1                   | 15           |

**b)** ![[IMG_5B575484F5F6-1.jpeg]]
Branch Coverage:
| Test Case magic(a, b, c) | Erwartetes Ergebnis | Kanten     |
| ------------------------ | ------------------- | ---------- |
| true, true, ""           | 2                   | E1, E2, E3 |
| false, false, ""         | -1                  | E4, E5     | 

**c)**
Path Coverage
| Test Case magic(a, b, c) | Erwartetes Ergebnis | Kanten     |
| ------------------------ | ------------------- | ---------- |
| true, false, "blub"      | -2                  | E1, E2, E5 |
| true, true, ""           | 2                   | E1, E2, E3 |
| false, false, "lala"     | -1                  | E4, E5     | 

**d)**
Condition Coverage
| Test Case magic(a, b, c) | Erwartetes Ergebnis | Zeile der Condition                     |
| ------------------------ | ------------------- | --------------------------------------- |
| false, false, "blubb"    | -1                  | 4-5 = false, 8-9 = false, 10-11 = false |
| true, true, ""           | 2                   | 4-5 = true, 8-9 = true, 10-11 = true    |

**e)**
| Test Case magic(a, b, c) | Erwartetes Eregbnis | Zeile                     |
| ------------------------ | ------------------- | ------------------------- |
| false, false, "blub"     | -1                  | 4-5 = false, 8-11 = false |
| true, true, ""           | 2                   | 4-5 = true, 8-11 = true   |

**f)**
Modified Condition Decision Coverage (Lösung genau angucken)
| Test Case magic(a, b, c) | Erwartetes Ergebnis |
| ------------------------ | ------------------- |
| false, false, "full"     | -1                  |
| true, false, "full"      | -2                  |
|                          |                     |
| false, false, ""         |                     |

**g)**
| Test Case magic(a, b, c) | Erwartetes Ergebnis |
| ------------------------ | ------------------- |
| false, false, "full"     | -1                  |
| false, false, ""         | -1                  |
| false, true, "full"      | -2                  |
| false, true, ""          | -2                  |
| true, false, "full"      | -2                  |
| true, false, ""          | 2                   |
| true, true, "full"       | 2                   |
| true, true, ""           | 2                   | 

**h)**
Nein, neben den Coverages kann es auch noch andere Fehler geben, wie zum Beispiel mit der Speichernutzung

### Aufgabe 3
| Nr. | Beschreibung | Wertebelegung von a | Erwartetes Ergebnis / Exception |
| --- | ------------ | ------------------- | ------------------------------- |
| 1   | Array = null | null                | IllegalArgumentsException       |
| 2   | Array leer   |                     |Illegal                               |
| 3   | Array leer   | [1, 2, 3, 4, 5]     |                                 |
| 4   |              |                     |                                 |
| 5   |              |                     |                                 |
