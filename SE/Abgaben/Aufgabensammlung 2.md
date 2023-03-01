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
| Nr. | Beschreibung                              | Wertebelegung von a  | Erwartetes Ergebnis / Exception |
| --- | ----------------------------------------- | -------------------- | ------------------------------- |
| 1   | Array = null                              | null                 | IllegalArgumentsException       |
| 2   | Array leer                                | []                   | IllegalArgumentsException       |
| 3   | Array normal                              | [1, 2, 3, 4, 5]      | 5                               |
| 4   | Array besteht aus nur einem Element       | [1]                  | 1                               |
| 5   | Array besteht nur aus negativen Elementen | [-1, -2, -3, -4, -5] | -5                                |

### Aufgabe 4
**a)**
$5 + 2 + 3 + 2 + 8 = 20$

**b)**
Prio: 1, 2, 4, 6
US: 17, 20, 13, 21
SP: 5, 8, 3, 3 = 19
Die User Stories sind so eingeteilt, dass sie in der Gewünschten Reihenfolge der Kunden implementiert werden, aber auch so, dass wir die Velocity der letzten Iteration nicht übersteigen. Deshalb werden die Prioritäten 3 und 5 auf eine Zukünftige Iteration verschoben, idealerweise so schnell wie möglich

### Aufgabe 5
**a)**
$A \land B \land C \land D \land \lnot C$

b)
a: Funktioniert nicht, weil es B D benötigt aber mit E D ausgeschlossen wird
b: Funktioniert nicht, weil entweder E oder D 

### Aufgabe 6
![[IMG_8211DC708935-1.jpeg]]

### Aufgabe 7
##### Modularität
- Modularität führt zu vier wichtigen Vorteilen:
	- Die Möglichkeit, das System in einfacherere Teile zu zerlegen
	- Die Möglichkeit, das System aus einfacheren Teilen zusammenzubauen
	- Die Möglichkeit, das System nicht als ganzes, sondern als Blöcke verstehen zu können
	- Die Möglichkeit, ein System zu verändern, indem nur ein Kleiner Teil verändert wird
- Modularität heißt schwache Kopplung aber hohe Kohäsion
##### Verständlichkeit
- Je größer der Code und das Team wird, desto komplexer wird der Code und komplexibilität hindert Entwickler daran den Code zu verstehen und effektiv zu verändern
##### Kohäsion
- Kohäsion ist ein Maß dafür, wie stark die einzelnen Elemente innerhalb einer Klasse, bzw eines bestimmten Softwareteils, miteinander verbunden sind
- Eine hohe kohäsion bedeutet, dass die Elemente untereinander Stark verbunden sind, heißt die Arbeiten zusammen um eine einzelne Funktionalität zu erfüllen. Eine niedrige Funktionalität hingegen weißt auf eine sehr schwache Verbindung der Elemente hin, was im extremfall bedeutet, dass die einzelnen Elemente nichts miteinander zu tun haben
- Eine niedrige kohäsion sorgt beispielsweise für eine höhere komplexität des Systems und somit zu einer schlechteren verständlichkeit was wiederum zu einer schlechten wiederverwendbarkeit, erweiterbarkeit, usw. führt.
##### Conzision
- Klarer Code und wenig Dopplungen

- Modularität
	- --> Portabilität
		- Durch die Modularität kann man das System als einzelne Blöcke betrachten, die unabhängig voneinander Funktionieren, was es super einfach macht, Plattformabhängige Funktionen durch andere Blöcke auszutauschen
	- --> Erweiterbarkeit
		- Dadurch, dass zwischen den eben beschriebenen Blöcken keine bzw nur leichte Abhängigkeiten bestehen, kann man das System sehr gut mit neuen Funktionen erweitern.
	- --> Wiederverwendbarkeit
		- Module können in anderen Systemen wiederverwendet werden
- Verständlichkeit
	- --> Erweiterbarkeit
		- Ist der Code sehr komplex und schwer zu verstehen, hindert es Entwickler daran, den Code effektiv zu verändern
	- --> Portabilität
		- Ist der Code schwer zu verstehen, könnte es für Entwickler schwer sein, die Software so anzupassen, dass sie auf einem anderen System läuft
	- --> Effizienz
		- Nur wer den Code versteht, kann ihn Optimieren
- Kohäsion
	- --> Effizienz
		- Klassen mit zu schwacher Kohäsion neigen dazu, Verantwortlichkeiten zu übernehmen, welche sie eigentlich deligieren sollten was die Klasse weniger effizient macht
	- --> Wiederverwendbarkeit:
		- Eine niedrige Kohäsion steigert die komlpexität der Klasse, was sie somit schwer verstehbar macht, was die wiederverwendbarkeit beeinträchtigt
- Conzision
	- --> Effizienz 
		- Ist der Code sehr unkonzise, verbaucht man beispielsweise unnötig Speicherplatz oder Systemressourcen 

### Aufgabe 8
**a)**
| Test Case magic(array, i, b) | Erwartetets Ergebnis/Exception | Zeile          |
| ---------------------------- | ------------------------------ | -------------- |
| [1, 2, 3], 5, true           | 6                              | 3, 7, 9-10, 13 | 

**b)**
| Test Case magic(array, i, b) | erwartet         | Edge                         |
| ---------------------------- | ---------------- | ---------------------------- |
| null, 1, true                | nullPointer...   | E1, E2                       |
| [1], 1, false                | 0                | E1, E3                       |
| [1, 2, 3], 0, true           | 0                | E1, E4, E5, E6               |
| [1, 2, 3], 3, true           | 6                | E1, E4, E5, E7, E10, E11, E6 |
| [1, 2, 3], 5, true           | ArrayIndexOut... | E1, E4, E5, E7, E10, E11, E8 |
| [null, null, null], 3, true  | NullPointer...   | E1, E4, E5, E7, E9           |

**c)**
| Test Case Magic(array, i, b) | erwartet |     |
| ---------------------------- | -------- | --- |
|                              |          |     |
