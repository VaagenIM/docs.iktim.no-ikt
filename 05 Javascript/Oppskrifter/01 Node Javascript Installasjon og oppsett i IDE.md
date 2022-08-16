---
title: 01 Node Javascript - Installasjon og oppsett i IDE
aliases: [NodeJS - Installasjon og oppsett i IDE,]
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - IDE
  - Editor
  - Javascript
created: 2022-04-09 02:00:00
updated: 2022-08-13 20:25:18
---
# Installasjon og oppsett av IDE
Her er noen gode tips for å komme i gang med JavaScript programmering.

## Installasjon
Installasjon til Javascript utvikling (NodeJS) finner du her: [Node.js](https://nodejs.org/en/)
Anbefalt versjon er LTS, som betyr long-term support.

## Oppsett i [[01 Atom IDE|Atom]]
Her er noen anbefalinger til packages som kan installeres i Atom, for en innføring i hvordan man laster ned packages, se [[01 Atom IDE#Installer Packages|Atom - Installer Packages]]

> [!INFO] Installer anbefalte pakker i terminalen
> For å installere alle pakkene i terminalen så kan du lime inn følgende kommando i en terminal:
> ```sh
> apm install atom-ternjs platformio-ide-terminal linter-js-standard atom-pug
> ```

### `atom-ternjs` (Autocomplete)
`atom-ternjs` er en Atom package som foreslår alternativer og viser våre mulige valg automagisk. Denne er nesten et must når man programmerer Javascript.

### `platformio-ide-terminal` (Terminal)
I NodeJS bruker man noe som heter [[NPM]] til å installere pakker og kjøre vår kode. Dette gjøres i terminalen, men istedet for å bruke operativsystemet sin terminal så kan dette gjøres direkte i Atom.

### `linter-js-standard` ([[Linter]])
`linter-js-standard` er en linter som hjelper oss å holde orden på koden og gjøre den ryddig. Denne kan være litt masete, men den er som oftest til god hjelp.

### `atom-pug` (Fargelegg .pug filer)
Vi kommer i "HTML" et nytt filformat, `.pug`. Med denne pakken så blir det enklere å lese filene. ([https://pugjs.org](https://pugjs.org/))

