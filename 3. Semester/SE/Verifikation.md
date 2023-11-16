## Einfühurung
Wie versichert man Softwarequalität?
Um Softwarequalität zu versichern, muss ein definierter Qualitätsversicherungsplan befolgt werden:
- Designprinzipien
	- Meistern und Anwenden von gut getesteten Design Prinzipien
	- Komstante überprüfung der Softwarequalität (Quantitativ und Qualitativ)
- Design Techniken
	- Werkzeuge und Techniken benutzen, welche dabei helfen eine gewisse Qualität zu erlangen
- Design Patterns
	- Lernen von und wiederverwenden von bewährten Lösungen zu wiederkehrenden Problemen
- Verifikation
	- Systematisch die Korrektheit und Performance des Designs prüfen
- Validation
	- Prüfen, ob das Design die Anforderungen erfüllt

**Validierung vs. Verifikation:**
- Validierung 
	- Versichert, dass die Erwartungen der Kunden erfüllt wurden
		- "Bauen wir das richtige System?"
	- Ist das implementierte Feature komplett und wie gewollt Eingerichtet?
	- Passt die Software in den Workflow der Organisation?
	- Mitarbeit der Kunden / User benötigt
- Verifikation
	- Versichert korrektheit gegenüber der Systemspezifikationen
		- "Bauen wir das System richtig?"
	- Arbeiten die implementierten Features wie spezifiziert?
	- Wie reagiert das System auf fehler?
	- Verifikation wird herstellerseitig durchgeführt

**Überblick über Verifikationstechniken:**
- Static - Ausführung des Codes nicht notwendig
	- Code Review
		- Kann zu jeder Zeit des Entwicklungsprozesses angewendet werden
	- Static Checking
		- Automatisierte Analyse: Typenchecks, Bug finder
	- Formal Verification
		- Versichert, dass das Program die Formalien erfüllt
- Dynamisch - Ausführung des Codes wird benötigt
	- Testing
		- Korrektes Verhalten des Programmes für bestimmten Input überprüfen
	- Runtime monitoring
		- Programm mit Sicherheits-Assertions spicken, deren violation während der Ausführung angezeigt werden


## Code Reviews
> Eine Code review ist ein strukturierter Inspektionsprozess für einen Teil einer Software, welche in einem Team, mit dem Ziel, mögliche Fehler zu finden, durchgeführt wird.

- Bedingung: Aktueller Code und die komplette Spezifikation ist verfügbar
- Jedes Mitglied des Teams nimmt eine der folgenden Rollen an (Minimalsetup):
	- Author/Besitzer
	- Inspektur/Leser
	- Schreiber
	- Vorsitzender/Moderator
- Ablauf:
	1. Planung
	2. Overview
	3. Individuelle Vorbereitungen
	4. Inspektionsmeeting
	5. Überarbeiten
	6. Folgetreffen

**Checklist:**
> Code reviews werden von einer Checklistste geführt
- Checklisten müssen auf das Projekt angepasst sein
	- z.B. Die Programmiersprache, nutzen von Staticanalyse usw.
- Ziel von Checklisten ist es spezielle Fault-Klassen zu finden
- Geschwindigkeit
	- ca. 500 Statements/h bei der Overview
	- ca. 100 Statement/h bei der Inspektion
	- Meetings sollten nicht länger als 2 Stunden dauern

**Vorteile und Hindernisse:**
- Vorteile
	- Es gibt starke, empirische Beweise dafür, das Code Reviews funktionieren und Kosten sparen
	- Sie helfen dabie Wissen über den Code im Team zu verbreiten
	- Man kann defekte aufspüren, bevor sie in Tests (oder sogar im Ausfelieferten Code) auffallen
	- Sie können die Qualität des Codes verbessern
	- Es wird kein ausführbares System benötigt
- Hindernisse:
	- Es werden reife Persönlichkeiten benötigt: Teammitglieder könnten sich diskriminiert fühlen
	- Unter Zeitdruck fühlen sich Code Reviews an wie Zeitverschwendung
	- Code Reviews funktionieren nur richtig, wenn sie richtig durchgeführt werden

## Software Testing
> Nicht triviale Tests haben unendlich viele oder unzählbar viele mögliche verschiedene Ausführungen, was es unmöglich macht sie alle zu testen

**Was ist ein Programmtest?**
- Inhalte
	- Das System bzw. die Implementierung welche getestet wird (SUT, IUT)
	- Die Testinputs
	- Das Runtime Environment, vorbereitung, durchlauf und clean-up (Testharness)
	- Ein Testurteil (Bestanden / Durchgefallen) durch ein Testorakel bestimmt

**Was ist ein Testplan?**
- Detaillierte Beschreibung des getesteten Prozesses
- Dokument beabsichtigt von Menschen gelesen zu werden
- Workplan: Phasen und Zeitplan
- Testprozeduren
- Erklärung des Testdesigns

**Test Design:**
1. Identifizierung und Analysieren der Verantwortungen der IUT
	- Pre- und Postbedingungen in Use Cases benutzen
	- Minimale und Erfolgs Garantien eines Fully Dressed Use Cases verwenden
	- Verteilung der Verantwortlichkeiten im Design analysieren
2. Testfälle basierend auf folgendem hinzufügen
	- Use Case, Design, Code analyse
	- Erahnungen, minimaler Erfolgsgarantie
	- Allgemeine Heuristiken (z.B. Domain / Expression beschränkungen)
3. Für jeden Test bestimmen, wie das Ergebnis erreicht wird:
	- Erwartete Ergebnisse und ein menschliches oder programmiertes Testorakel bereistellen

### Tests automatisieren
> Testen ist ein sehr teurer Schritt der Softwareentwicklung (ca. 15-25% der Summe der Kosten)

**Welche Aspekte des testens können automatisiert werden?**
1. Die Ausführung der Tests (Über Nacht, nach jeder Veränderung, etc.)
2. Testinputs generieren
	1. Codegeführt
	2. Modellgeführt
	3. Datengeführt
3. Testergebnisse generieren
	1. Testorakel ist ein kleines Programm, Teil des Testharnesses
	2. Orakel automatisch durch Spezifikationen generiert

**Aufgaben eines Systems welches Tests automatisiert:**
1. Testenvironment einrichten
	- Server starter, Netzwerk verbindung einrichten, Services registrieren, ...
2. IUT starten
3. IUT in die erforderlicher pretest Konfiguration bringen
	- Erforderliche Datentabellen laden und erforderliche Objekte erschaffen
4. Testinputs einstellen
5. Outputs evaluieren und Ergebnis aufnehmen
6. Testenvironment aufräumen
	1. Daten löschen, Services stoppen und Daten reseten

**Testgoal:**
- Was kann beim testen erreicht werden?
	- Man kann sicher gehen, dass das System die mindestvorraussetzungen erfüllt
- Umfassendes Testen beinhaltet folgende Schritte:
	- Ausführen der Testsuite und Verabschiedung des Urteils für jeden Testfall
	- Coveragetool verwenden, um die IUT zu bewerten
	- Testsuit wiederholen und die gegebene Coverage beurteilen
	- Wenn notwendig Testcases hinzufügen um Coverage zu steigern
	- Aufhören zu Testen, sobald das Coverageziel erreicht ist und alle Tests bestanden werden

**Test Input:**
- Ein Testpoint ist ein spezieller Wert für den Testcase Input oder eine Zustandsvariable
- Wird von der Domain ausgewählt
- Die Domain ist die Menge der Werte, welche input bzw. Zustandsvariablen annehmen können

Heuristik für die Wahl von Testpunkten:
- Äquivalenzklassen
- Schranken der Werte
- Spezielle Werte

**Test Case, Test Suit und Test Run:**
- Test case
	- Zustand der IUT vor dem Test
	- testpoints / Bedingungen
	- Erwartete Ergebnise
- Test Suit
	- Eine Menge von Testcases nennt sich Test Suit
- Test Run
	- Die Auführung einer Test Suit auf der IUT

**Test Driver und Test Harness:**
- Test driver
	- Klasse bzw. Dienstprogramm welche(s) Test Cases auf der IUP ausführt
- Test Harness
	- Ein System mit Test Drivers und anderen Werkzeugen um die Testausführung zu unterstüzen

**Fault und Failure:**
- Fault
	- Fehlender oder falscher Code
- Failure
	- Die Unfähigkeit eines Systems oder einer Komponente eine benötigte Funktion mit den gegebenen Limits durchzuführen

### Test Framework: JUnit
- @BeforeEach
	- Annotation für Methoden welche den für den Test benötigten Zustand einrichten
- @AfterEach
	- Annotation für Methoden welche nach dem Test wieder aufräumen
- @Test
	- Annotation für Methoden welche die Tests implementieren
- assertTrue, assertFalse,...
	- Evaluieren die Ergebnise und nehmen diese auf

## Test Coverage: Wann aufhören mit dem testen?

**Strukturelle Kriterien:**
- Statement Coverage - Alle Statements wurden mindestens einmal ausgeführt
- Basic Block Coverage - Alle Basic Blocks wurden mindestens einmal Ausgeführt
- Branch Coverage - Jede ausgehende Kante von einer Node im KFG wurde mindestens einmal ausgeführt
- Path Coverage - Jeder Pfad im KFG wurde mindestens einmal ausgeführt

**Logische Kriterien:**
- Condition Coverage - Jede Condition wurde in mindestens einem durchlauf als Wahr und als Falsch bewertet
- Decision Coverage - Jede Entscheidung (Guard) wurde in mindestens einem durchlauf als Wahr und als Falsch bewertet
- Modified Condition Decision Coverage (MCDC) - Kombiniert Aspekte von Condition Coverage, Decision Coverage und independence test
- Multiple-condition Coverage - Alle true-false Kombinationen wurden in mindestens einem durchlauf bewertet

**Condition vs. Decision:**
- Condition ist ein Teil einer Decision (a == b)
- Decision besteht aus Conditions (a == b || b < d)

**Modified Condition Decision Coverage:**
Eine Testsuit satisfies MCDC wenn:
- Eine Decision wird mindestens 2 mal ausgeführt
- Wobei die condition einmal mit false
- und einmal mit true bewertet wird
- Die Decision in beiden durchläufen unterschiedlich bewertet
- und die anderen Conditions in der Decision identisch in beiden oder garnicht in mindestens einem Testfall bewertet wird
> Jede Condition muss einfluss auf die Evaluation der Decision haben und muss unabhängig von den anderen Conditions sein

## Test Automatisierung und Tool Support

**Automatisierte Test Case Generation:**
Es gibt zwei fundamentale Ansätze:
- White Box
	- Code der IUT wird analysiert um Coverage zu erreichen
		- Syntaktische Ansätze:
			- Nach Conditions suchen
			- Evaluation reicht um logic based Kriterien zu erfüllen
			- Over-Approximation: unerreichbarer Code, undurchführbare Entscheidungen
		- Symbolische Execution
			- KFG abrollen mit symbolischen Werten 
			- Reicht um strukturelle Coverage Kriterien zu erfüllen
			- Under-approximation: Unerreichter Code
- Black Box
	- Analyse der Input Daten oder Model der IUT

**Test Coverage Recording:**
1. IUT vorbereiten
2. Test Suit laufen lassen und Informationen Sammeln
3. Analysieren und Anzeigen der erreichten test Coverage Statistiken

**Test Orakel Synthese:**
- Menschliches Orakel: Zeitfressend und Fehlerbehaftet
- Urteil als Code: Expertise benötigt, schwer zu Warten
$\Rightarrow$ Test Orakel in Formaler Spezifizierungs Sprache, davon Code ableiten

**Automatische Statische Verifikations Templates:**
- Statisches Checken
	- Normalerweise basiert auf KFG der IUT + lösen von Beschränkungen
	- Runtime exception, Lebendigkeit und Informationsfluss
	- Voll automatisiert
	- Over-approximating, möglicherweise zu viele falsch positive
	- Skaliert einigermaßen gut (Poly Time Algorithmen)
- Bug Finding
	- Basiert auf Pattern matching
	- Heuristiken:
		- Schnell, skaliert gut, handeln volles Java
		- Over- and Underapproximating (falsch-positiv und unvollständig)

**Statische Analysen mit KFG:**
- Kontroll Fluss Analyse:
	- Determiniert Kontroll Fluss im Programm
- Daten Fluss Analyse:
	- Ist eine Variable lebending, heißt: Wird der zugewiesene Wert irgendwo verwendet?
- Informationsfluss Analyse:
	- Von welchen Anfangswerten hängt das endergebniss ab?

**Typische Quellen für Bugs:**
- Komplexe Sprachfeatures
- Missverstandende API Methoden oder Invarianten
- Rechtschreibfehler, falsche Nutzung von Operatoren

**Formale Ansätze:**
- Streng Mathematische foundation
- Solide in Bezug auf das formale Modell
- Nicht notwendigerweie komplett

**Formale Verifikation:**
- Beweis, dass ein Programm den Formalen Spezifikationen entspricht
- Model Checking: CBMC, Java PathFinder, Spin, SDV/SLAM,...
- Deduktive Verifikation: KeY, KIV, VCC, VeriFast, jStar, VerCors, Viper...

**Design by Contract:**
- Formale Spezifikation:
	- Pre-, Postconditions, Nebeneffekte für jede Methode
	- Klassen und Schleifen Invarianten
- Verifikations Tools beweisen, dass jede Methode
	- ihren Vertrag in allen möglichen Läufen erfüllt
	- Loop und Objekt Invarianten beibehält

**Runtime Monitoring:**
- Preconditions, Postconditions, Invarianten als Assert Statements 
	- Vertrag auf Java Expressions limitieren
- Programmdurchläufe reporten verletzte Spezifikationen: Offensichtlich Unvollständig
