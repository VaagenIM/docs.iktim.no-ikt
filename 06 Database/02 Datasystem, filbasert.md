---
title: 02. Datasystem, filbasert
aliases: [Filbasert Database,]
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - Database
  - JSON
  - CSV
created: 2022-04-09 02:00:00
updated: 2022-08-13 20:25:31
---
# Datasystem, filbasert
En måte vi kan lagre data på i system, er å bruke tradisjonelle mappesystemer. Dataen vi lagrer og behandler bruker datamaskinens filsystem, som betyr at vi kan finne frem og endre på informasjonen ved å bruke vanlig filutforsker.

Det finnes mange fordeler ved å bruke filbaserte datasystemer - men avhengig av prosjektets størrelse så finnes det flere ulemper. Den største fordelen til filbasert database er at det er raskt å jobbe med og teste, men kan fort bli uoversiktlig dersom det er behov for å behandle store mengder data. I ytelse vil en [[03 Datasystem, SQL|SQL-basert]] database være betydelig raskere enn en filbasert, ettersom en database kan ligge lagret ferskt i [[RAM|minnet]], mens en filbasert database må leses hver gang.

## Fordeler
- Enkelt å programmere
- Kan stå selvstendig, er ikke avhengig av en database som kjører
- Lett å slette ting og teste ting
- Oversiktlig om man har lite data
- Enkelt for mennesker å forstå

## Ulemper
- Tregt. Må lese/skrive til disk, kan ikke bruke RAM på samme måte som en SQL database. Disker er IKKE laget for mange, små filer
- Ikke-skalerbart, blir fort rotete når man lagrer data for 50+ brukere
- Kan ikke passordbeskyttes på samme måte som en database
- Vanskelig å oppdatere all lagret data på samme tid