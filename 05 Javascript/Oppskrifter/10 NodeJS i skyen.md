---
title: 10 Publiser i skya
aliases: [Publiser i skya]
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - Cloud
  - Nettverk
  - Javascript
created: 2022-04-09 02:00:00
updated: 2022-08-13 20:26:18
---
# Publiser i skya
Godt jobba! Nå skal vi migrere vårt prosjekt til [[Cloud|skyen]]. Vi bruker [Microsoft Azure](https://azure.microsoft.com/en-us/) - du logger inn med din skolekonto

## Steg 1: Opprett en maskin i skya
Inne på [https://portal.azure.com/](https://portal.azure.com/) skal vi opprette en virtuellmaskin. Vi må definere et navn, brukerkonto, tillate SSH (port 22) og generere en SSH nøkkel (Valgfritt, kanskje denne skal velges bort).

## Steg 2: Publiser prosjektet ditt på GitHub
Det VIKTIGSTE her er å ikke overføre sensitive filer og data. Kun det som er nødvendig må opp til GitHub. Vanligvis bruker man en [[gitignore]] fil når man laster opp et Git prosjekt.

## Steg 3: Installer NodeJS på den virtuelle maskinen
Vi trenger NodeJS installert for å kunne kjøre vårt prosjekt

## Steg 4: Last ned GitHub prosjektet ditt
Når vi har kjørt prosjektet under testing, så har vi brukt `npm run watch`. Det fungerer bra for testing, men ikke over lengre tid.

Vi må like vel installere prosjektet:
```sh
git clone <lenke>
cd <prosjekt-navn>
npm install
```

## Steg 5: Last ned en webserver, som hoster Node
Forklaring kommer.

