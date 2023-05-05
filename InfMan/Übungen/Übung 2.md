#### Aufgabe 2.1
a) A(*K*, L), B(*M*, N, *K*)
b) A(*K*, L), B(*M*, N), C(*O*, P), R(Q, K, *M*, *O*)

#### Aufgabe 2.2
a) 
**Superschlüssel**: {T, S}, {T, P}
**Schlüsselkandidat**: {T, S}, {T, P}
b)
**Superschlüssel**:
{Pers.Nr, Name, Rang, Raum}, {Pers.Nr}
{Pers.Nr,...}

#### Aufgabe 2.3
Nein, sie sind keine Fremdschlüssel, da bei Einkauf Elemete enthalten sind, die bei Kund_in und Einkauf fehlen

#### Aufgabe 2.4
**WICHTIG: DATENTYPEN FEHLEN**
Schritte:
1. Abbildung der Entitätstypen auf Relationen
2. Abbildung der Beziehungtypen auf Entitäten
3. Zusammenfassen der Relationen
4. Behandlung von schwachen Entitätstypen

Siehe Musterlösung!

#### Aufgabe 2.5 Realationale Algebra

a)$S = \pi_{\text{ISBN}} (\sigma_{\text{Nachname = 'Kemper'} \land \text{Nachname = 'Alfons'}}(\text{AutorIn} \bowtie _{Nr = AutorNr} \text{Verfasst}))$b)
$S = \pi_{\text{Name}}(\sigma_{\text{Überkategorie = "Informatik"}}(Kategorie))$
c)$S = \pi _\text{Vorname, Nachname} (Benutzer) \cap \pi _\text{Vorname, Nachname}((AutorIn \bowtie _\text{Nr = AutorInNr} Verfasst)$d)