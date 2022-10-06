---
title: Nedlastning av spill (Mac)
aliases: 
  - Nedlastning av spill (Mac)
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - Mac
created: 2022-10-06 08:32:38
updated: 2022-10-06 11:00:59
---
# Nedlastning av spill (Mac)
Dersom du laster ned spill fra vår egen kolleksjon, https://spill.iktim.no, kan det hende du blir møtt med følgende feilmelding når du prøver å åpne:

![[kan-ikke-apne-apple.png]]

Dette betyr ikke at filen er skadelig, men at programvaren ikke har gyldig sertifikat. Du bør fremdeles aldri laste ned og kjøre programvare fra nettsteder du ikke stoler på, men kopiene på denne siden er genuine.

## Fiks - prøv 1 steg om gangen
1. Plasser filen i Applications mappen
2. Du må muligens godta installasjon fra ukjente utviklere, dette gjør du i systemvalg.
3. Hvis du ikke får opp valget fra ukjente utviklere, kan du tvinge den frem ved å åpne appen `Terminal` og lime inn følgende kommando:
```sh
sudo spctl --master-disable
```

Nå skal du kunne åpne programmet / spillet.