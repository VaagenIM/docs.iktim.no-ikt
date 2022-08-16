---
title: Atom IDE (GAMMEL)
aliases: [Atom IDE,]
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - IDE
  - Editor
created: 2022-04-09 02:00:00
updated: 2022-08-13 20:23:58
---
# Atom IDE (Utgått)
Atom IDE er GitHub sin egen kode-editor, også kalt en [[IDE]] (Integrated development environment). Denne kan lastes ned på [atom.io](https://atom.io/)

## Installer Packages
I Atom så er det god fordel å installere noen packages ([[Plug-in|plug-ins]]) før man setter igang å kode. 

For å installere packages går man til `File -> Settings -> Install`, eventuelt `CTRL+,` -> `Install`.

> [!NOTE] Installer packages via terminalen
> Alternativt så kan packages installeres i terminalen med syntaks `apm install <packages>`

## Anbefalter packages
### `platformio-ide-terminal` (Terminal)
Med `platformio-ide-terminal` kan man åpne et konsollvindu for vårt prosjekt inne i Atom, uten å måtte lete frem til mappen i vår egen terminal. Standard snarvei er `ALT+SHIFT+T`.

### `atom-live-server` (Live-Webutvikling)
Denne åpner vårt prosjekt i en nettleser, som oppdateres automagisk hver gang vi lagrer dokumentet. Et must for når en jobber med blant annet [[HTML]]. Snarvei for å starte er `CTRL+ALT+L` / `CMD+ALT-L`

Her er en større liste av anbefale Atom pakker, som ikke er helt ryddig enda: [[Anbefalte Atom Packages]].

## Innebygd pakke: line-ending-selector
Et frustrasjonsmoment i noen språk kan være måten datamaskinen lagrer dokumentene på. I Linux/MacOS representerer et linjeskift tegnene `\n` (LF), men i Windows er det representert via `\r\n` (CRLF). En del programmer kan derfor få feilmelding om linjer som slutter med `\r`.

Inne i pakken `line-ending-selector` (Core Packages), kan man overstyre til å kun lagre filer i LF formatering som er å foretrekke for en del språk, for eksempel [[Bash]] programmering som er mye brukt i [[Linux]] og f.eks. [[Docker]].
