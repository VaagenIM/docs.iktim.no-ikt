---
title: CPU
aliases: 
  - Sentral Prosesseringsenhet
  - Prosessor
  - CPU
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - Data
created: 2022-09-06 10:17:53
updated: 2023-05-09 09:11:06
---
# Sentral Prosesseringsenhet
Hjernen til maskinen.

Utfører enkel logikk (sammenligne verdier), enkel matematikk (+ og - regnestykker) og kan kommunisere med [[Minnebrikke|minnet]]. Kan også delegere arbeid til andre komponenter, for eksempel kan grafiske applikasjoner avlastes til et [[Grafikkort]].

Måles i antall operasjoner per sekund (Hz). Dagens prosessorer måles ofte i GHz, som tilsvarerer $1.000.000.000$Hz.

## Inndeling av CPU
En CPU består av flere prosessorkjerner som igjen består av tråder, som er individuelle prosessorer som kan fordele arbeidsmengden. Programvaren må være programmert på forhånd for å kunne utnytte flere prosessortråder på samme tid. I videoredigering kan arbeidsoppgavene fordeles ved å gi en kjerne et bilde å prosessere hver når en video skal eksporteres.

Noen programmer eller operativsystemer ([[Hypervisor|Hypervisorer]]), for eksempel [VirtualBox](https://www.virtualbox.org/), lar deg til og med fordele en prosessor til virtuelle maskiner, slik at man kan kjøre flere operativsystem på èn og samme maskin.