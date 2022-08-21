---
title: Markup Language
aliases: 
  - Markup Language
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - Definisjon
created: 2022-08-21 12:51:33
updated: 2022-08-21 12:51:33
---
# Markup Language
Markup er kjennetegn på språk hvor innholdet må tydelig markeres (noteres) for å bli behandlet og strukturert på riktig måte. Ofte har notasjonen både en start og en slutt, som man kan se i blant annet webutviklingsspråket [[01 Hva er HTML|HTML]].

Et eksempel kan være å gjøre deler av teksten **fet** eller *kursiv*. I de fleste programvarene som behandler tekst blir notasjonen usynlig for brukere. I HTML bruker man ulike tagger med en definert start og slutt for å notere endringen;

```html
Eksempel på <b>fet</b>, <i>kursiv</i> og <b><i>fet og kursiv tekst</i></b>.
```
Resultat: Eksempel på **fet**, *kursiv* og **_fet og kursiv tekst_**.

Et alternativ til Markup er [[Markdown Language]], som bruker en mer minimalistisk syntaks:

```md
Eksempel på **fet**, _kursiv_ og **_fet og kursiv tekst_**.
```