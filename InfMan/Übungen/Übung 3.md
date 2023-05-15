#### Aufgabe 3.1 a)
```sql
DROP TABLE IF EXISTS Buch;  
DROP TABLE IF EXISTS BuchAutor;  
DROP TABLE IF EXISTS Autor;  
DROP TABLE IF EXISTS Bibliothek;  
DROP TABLE IF EXISTS Leser;  
DROP TABLE IF EXISTS Exemplar;  
  
CREATE TABLE Buch  
(  
ISBN CHAR PRIMARY KEY,  
Titel VARCHAR(255) NOT NULL,  
Preis DECIMAL(10,2)  
);  
  
CREATE TABLE Autor  
(  
ID INT,  
Vorname VARCHAR(40),  
Nachname VARCHAR(80)  
  
);  
  
CREATE TABLE BuchAutor  
(  
ISBN CHAR(13) PRIMARY KEY ,  
ID INT,  
FOREIGN KEY (ISBN) REFERENCES Buch (ISBN),  
FOREIGN KEY (ID) REFERENCES Autor (ID)  
);  
  
CREATE TABLE Bibliothek  
(  
Name VARCHAR(40),  
Ort VARCHAR(80),  
Telefon VARCHAR(80)  
  
);  
  
CREATE TABLE Leser  
(  
ID INT,  
Vorname VARCHAR(80),  
Nachname VARCHAR(80)  
  
);  
  
CREATE TABLE Exemplar  
(  
ExemplarNr INT,  
ISBN CHAR(13),  
Bibliothek VARCHAR(40),  
LESER INT,  
FOREIGN KEY (ISBN) REFERENCES Buch (ISBN),  
FOREIGN KEY (Bibliothek) REFERENCES Bibliothek (Name),  
FOREIGN KEY (LESER) REFERENCES Leser (ID)  
  
);
```

#### Aufgabe 3.1 b)
