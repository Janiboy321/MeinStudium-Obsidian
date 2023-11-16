### Ausführen eines Programms
```
python3 hello.py
```

### Print
```python
print('show this in the console')
```

### Datentypen
| type            | Beschreibung                      | Beispiele                     |
| --------------- | --------------------------------- | ----------------------------- |
| Numerischer Typ | Zahl mit oder ohne Dezimalstellen | `int, float, complex, no = 3` |
| Texttyp         | Zeichenfolge                      | `str = "a literal String"`    |
| Boolescher Typ  | Boolean                           | `continue = true`             |

### Wie finde ich heraus, welchen Typ etwas hat?
```python
type(distance_to_alpha_centauri)
```

### Operatoren
```python
left_side = 10
right_side = 5
left_side/right_side # 2
```

### Importieren von Modulen
```python
from ... import ...
```

### Datumsangaben
> Um mit einem Datum zu arbeiten, muss man das Modul date importieren:
```python
from datetime import date
```

```python
date.today() #yyyy-mm-dd
```

### Konvertieren von Datentypen
```python
# Falsch, Ungültige Typen kann man nicht kombinieren:
print("Today's date is: " + date.today())

# Richtig, Daten konvertieren:
print("Today's date is: " + str(date.today()))
```

### Erfassen von Eingaben
#### Befehlszeilenargumente
> Startet man ein Programm mit `python3`, übergibt man den Namen der Datei, welche gestartet werden soll. Zusätzlich kann man auch Argumente übergeben - also Daten, auf welche das Programm bei der Ausführung zugreifen kann.
```python
# bspw. ein Datum, an welchem ein Backup ausgeführt werden soll
python3 backup.py 2023-01-01
```
So sieht das dann aus der sich des Programmierers  aus:
```python
import sys

# sys.argv ist ein Array, beginnend mit dem Namen des Programmes 
# gefolgt von den beim Aufrug angegebenen Argumenten
print(sys.argv)
print(sys.argv[0]) # program name
print(sys.argv[1]) # first 
```

#### Benutzereingabe
> Zum erfassen von Informationen von BenutzerInnen, verwendet man die `input()`-Funktion.
```python
print("Welcome to the greeter program")
name = input("Enter your name: ")
print("Greetings " + name)
```

> Daten welche das Programm so übergeben bekommt, werden immer als Strings abgespeichert, müssen also gegebenenfalls umgewandelt werden:
```python
# addiere zwei Zahlen
print(int(input("first number: ")) + int(input("second number: "))
```

### Arbeiten mit virtuellen Umgebungen
> Wie versichert man, dass das Entwickelte Projekt auch an anderen Computer funktioniert, welche möglicherweise eine andere Python-Version oder andere Versionen von Bibliotheken nutzt, als die, welche das Programm benötigt?
> Lösung: Man arbeitet in virtuellen Umgebungen

Eine Virtuelle Umgebung ist eine eigenständige Kopie sämtlicher Informationen, die zum Ausführen des Programms erforderlich sind. Dies schließt den Python-Interpreter und alle Bibliotheken ein, welche das Programm benötigt.

Grundlegender Workflow:
1. Man erstellt eine virtuelle Umgebung, die sich nicht auf den übrigen Computer auswirkt
2. Man gibt innerhalb der virtuellen Umgebung die Python-Version und die Bibliotheken an, welche benötigt werden
3. Man entwickelt das Programm

##### Erstellen einer Virtuellen Umgebung
1.  In das Verzeichnis wechseln, in welchem das Projekt gespeichert werden soll
2. Das Modul `venv` aufrufen:
```python
python -m venv env
```
An diesem Punkt werden einige Verzeichnisse erstellt:
```
/env
  /bin
  /include
  /lib
```
In env sollten keine Programmdateien abgelegt werden, diese sollten in ein extra Verzeichnis namens `src` ausgelagert werden:
```
/env
/src
  program.py
```

##### Aktivieren der virtuellen Umgebung
```python
source env/bin/activate
```

##### Deaktivieren der virtuellen Umgebung
```python
deactivate
```

### Pakete
> Ein Vorteil der Verwendung externer Bibliotheken ist die kürzere Entwicklungszeit für die Programme. Bibliotheken können aus dem Internet abgerufen werden. Wenn man diese Bibliotheken jedoch über eine virtuelle Umgebung abruft und installiert, stellt man sicher, dass sie nur für die virtuelle Umgebung und nicht global für den ganzen Computer installiert werden

#### Installieren eines Pakets
```python
pip install python-dateutil
```

#### Deinstallieren von Paketen
```python
pip install python-dateutil
```

#### Verwenden installierter Pakete
```python 
from datetime import *
from dateutil.relativedelta import *
now = datetime.now()
print(now)

now = now + relativedelta(months=1, weeks=1, hour=10)

print(now)
```

### Arbeiten mit Projektdateien
#### Freigeben eines Projekts
Folgende Schritte ausführen, um das Projekt in GitHub so freizugeben, dass andere Benutzer daran mitarbeiten können:
1. `pip freeze > requirements.txt
2. Gitignore Datei erstellen und Anwendungscode und requirements.txt einchecken
3. In Github einchecken

#### Verwenden eines Projekts
1. Projekt von Github abrufen
2. Virtuelle Umgebung erstellen und rein wechseln (source ...)
3. Projekt mit `pip install -r requirements.txt` wieder herstellen
4. App ausführen

### Verwenden von booleschen Operatoren
#### If Bedingung:
```python 
a = 97
b = 55
if a < b:
	print b
```

#### Else-If Bedingung (`elif`)
```python 
if a < b:
	print b
elif a > b
	print a
```

#### Else Bedingung
```python 
if a < b
	print b
else 
	print a
```

### Strings

##### ', " or """
> Möchte man innerhalb eines Strings ein Apostroph verwenden kann man den String mit "..." schreiben. Möchte man in dem String Anführungsstriche verwenden, kann man den String mit '...' schreiben. Möchte man im String beides verwenden, kann man den String mit """...""" schreiben

##### Zeilenumbruch in Python
Möchte man in Python einen Zeilenumbruch verwenden, kann man es mit \n machen, oder mit """...""":
```python
bslashn = "Hier kommt ein Zeilenumbruch \n Das war der Zeilen umbruch"
drippleanf = """Hier kommt ein Zeilenumbruch
Das war der Zeilenumbruch"""
```

#### String Methoden
- `.title()`
	- returnt den String mit großen Anfangsbuchstaben (jedes einzelnen Wortes)
- `.lower()` / `.upper`
	- Wandelt den String in Klein-/Großbuchstaben um
- `.split(String s)`
	- Returnt eine Array mit dem String, aufgeteilt in Teile von einem s zum anderen s
- `in`
	- Bsp: 
	```python 
	print("Moon" in "This text will describe facts and challenges with space travel")
	```
	. In returnt true falls "Moon" im String enthalten ist, sonst false
- `.find(String s)`
	- Die Methode returnt die Anzahl der im String enthaltenen s, oder -1 wenn kein s enthalten ist
- `.startswith(s)` / `.endswith`
	- Returnt ob ein String mit s anfängt/endet
- `.replace(s, newS)
	- Tauscht alle s im string mit newS aus
- `.join(String[] s)`
	- Return ein String, welcher aus allen Elementen einer Array zusammengefügt wurde

#### Formatieren eines Strings
Man verwendet den Platzhalter %s und schreibt nach dem String % ("S1", "s2", ...)
```python
name = "Jan"
print("This is %s, his brother %s used all his shampoo" % (name, "Tim"))
```

Oder man verwendet `.format()`
```python
print(f"It's {} brothers".format("friday"))
print(f"This is {0}, his brother {1} used all his shampoo".format("Jan", Tim))
```
Mittlerweile kann die Funktion auch variablen oder funktionen nutzen:
```python
name = "Jan"
print(f"This is {name}")
print(f"One plus 6 is {add(1, 6)}")
```

### Mathematische Operationen
##### Dividieren (Abrunden)
```python
	a = 5 / 2 # = 2,5
	b = 5 // 2 # = 2
```

##### Konvertieren von Strings in Nummern
`demo_int = int('215')`

##### Absolute Werte (Betrag)
`abs(16-39)`

##### Auf-/Abrunden
`round(14.5)`

##### Math library
```python
from math import ceil, floor

round_up = ceil(12.5)
print(round_up)

round_down = floor(12.5)
print(round_down)
```

### Listen
##### Create a list
```python
planets = ["Mercury", "Venus", "Earth", "Mars", "Jupiter", "Saturn", "Uranus", "Neptune"]
```

##### Access list items by index
```python
print("The first planet is", planets[0])
```

##### Length of a list
```python
len(planets)
```

##### Add items to lists
```python
planets.append("Pluto")
```

##### Remove items from lists
```python
# remove the last item:
planets.pop()
```

##### Use negative indexes
```python
planets[-1] # returns the last item in the list
planets[-2] # returns the second last item in the list
```

##### Find a value in a list
```python
planets.index("Jupiter") # returns the index of jupiter
```

##### Sclice lists
```python
planets = ["Mercury", "Venus", "Earth", "Mars", "Jupiter", "Saturn", "Uranus", "Neptune"]
print(planets[0:2]) # Ergebnis: ['Mercury', 'Venus']
print(planets[3:8]) # Ergebnis: `['Mars', 'Jupiter', 'Saturn', 'Uranus', 'Neptune']`
```

##### Join lists
```python
joinedlist = list1 + list2
```

##### Sort lists
```python
list.sort() # Aufsteigend
list.sort(reverse=true) # Absteigend
```