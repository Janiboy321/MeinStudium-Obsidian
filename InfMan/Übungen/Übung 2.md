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

2. 3

#### Aufgabe 2.4
- Autor_in(**NR**, Vorname, Nachname)
- Buch(**ISBN**, Jahr, Titel, Seiten,Verlag_Name)
- Exemplar(**Nr**, Regal, Position, Buch_ISBN)
- leiht(Rückgabedatum, Exemplar_NR, Benutzer_in_NR)
- Verlag(**Name**, Ort)
- Benutzer_in(**Nr**, Vorname, Nachname)
- Kategorie(**Name**)
- beinhaltet(Unterkategorie, Überkategorie)
- verfasst(Autorin_Nr,Buch_ISBN)
- beschreibt(Verlag_Name, Buch_ISBN)


#### Aufgabe 2.5 Realationale Algebra

a) $S = \pi_{\text{ISBN}} (\sigma_{\text{Autor = "Alfons Kemper"}}(\text{Buch} \bowtie \text{AutorIN}))$
b) $S = \pi_{\text{Unterkategorie}}(\sigma_{\text{Überkategorie = "Informatik"}}(beinhaltet))$
c) $S = $
