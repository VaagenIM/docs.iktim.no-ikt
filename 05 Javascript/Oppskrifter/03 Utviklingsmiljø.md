---
title: 03 Utviklingsmiljø
aliases: [NodeJS - Utviklingsmiljø,]
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - IDE
  - Javascript
created: 2022-04-09 02:00:00
updated: 2022-08-13 20:26:01
---
# Utviklingsmiljø i Javascript
Her er en oppskrift på hvordan du kan sette opp et enkelt utviklingsmiljø i [[Javascript]]. Oppsettet setter opp et prosjekt i en mappe via [[NPM]] (Node Package Manager) og tar i bruk en modul som heter [npm-watch](https://www.npmjs.com/package/npm-watch). 

npm-watch sin oppgave er å restarte ditt prosjekt hver gang den merker endringer, slik at alt du trenger å gjøre er å refreshe nettsiden.

Når du er ferdig, vil du kunne bruke `npm run watch` til å kjøre koden din, istedetfor å bruke `node app.js`. Fordelen med å bruke `npm run watch` er at `npm-watch` oppdaterer og kjører koden din automagisk hver gang etter du har gjort endringer, slik at du sparer mye tid.

## Oppsett av `npm-watch`:
For å installere npm-watch kjører vi følgende kommando i prosjektet vårt sin terminal: `npm install npm-watch`

Vi er nå nødt til å gjøre noen endringer i vår fil som heter `package.json`, den vil se noe slik ut:
```json
{
  "name": "hellonode",
  "version": "1.0.0",
  "description": "",
  "main": "app.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
    "express": "^4.17.3",
    "npm-watch": "^0.11.0"
  }
}

```
Om du har flere dependencies her, eller ulike verdier, så gjør det ingenting. Bare bekreft at `npm-watch` ligger under `"dependencies"`.

Her må vi endre på `"scripts"`, og legge til et nytt felt: `"watch":`

Dette er det som må inn:
```json
  "scripts": {
    "watch": "start http://localhost:3000 & npm-watch",
    "test": "node app.js"
  },
  "watch": {
    "test": "*.js"
  },
```

Hele `package.json` vil da se slik ut:
```json
{
  "name": "hellonode",
  "version": "1.0.0",
  "description": "",
  "main": "app.js",
  "scripts": {
    "watch": "start http://localhost:3000 & npm-watch",
    "test": "node app.js"
  },
  "watch": {
    "test": "*.js"
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
    "express": "^4.17.3",
    "npm-watch": "^0.11.0"
  }
}

```

Ved å nå kjøre `npm run watch` i terminalen, vil en tjeneste, [nodemon](https://www.npmjs.com/package/nodemon) åpne nettleseren din, starte `app.js` og overvåke endringer i alle `.js` filer.

Dersom du har et express dokument aktivt, vil du nå kunne endre på funksjonene uten å måtte kjøre koden manuelt ved å bruke `node app.js`, istedet er det kun nødvendig å refreshe nettleseren din.

## Les mer:
[npm-watch - npm](https://www.npmjs.com/package/npm-watch)