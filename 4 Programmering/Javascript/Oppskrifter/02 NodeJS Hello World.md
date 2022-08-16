---
title: 02 NodeJS - Hello World
aliases: [NodeJS - Hello World,]
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - Javascript
created: 2022-04-09 02:00:00
updated: 2022-08-13 20:25:34
---
# NodeJS: Hello World
I motsetning til Python, har NodeJS litt mer avanserte syntakser som kan være litt frustrerende å jobbe med, men fortvil ikke! Med pakkene vi installerte i forrige artikkel, [[01 Node Javascript Installasjon og oppsett i IDE]], så får vi god hjelp!

I denne oppskriften skal vi lage et Express prosjekt som viser teksten "Hello Node!"

## Steg 1: Hello World, konsoll
Opprett en ny mappe på maskinen din og kall denne for HelloNode

I din [[IDE]] åpner du prosjektmappen (i [[01 Atom IDE|Atom]] er det `Add Folders` eller `Open Folder`.

Lag en fil i prosjektet og kall denne for `app.js`

La oss verifisere at [[Javascript]] er installert ved å skrive inn koden:
```javascript
console.log("Hello Node!")
```

For å kjøre vår kode, åpner vi en terminal i prosjektet vårt 

Dersom du følgte anbefalingene på [[01 Atom IDE|Installasjon av Atom]], med `platformio-ide-terminal` installert så er snarveien `ALT+SHIFT+T`.
Her skriver vi `node app.js`.

Hvis alt har gått etter planen, vil du nå få opp teksten "Hello Node!"
Dette er et godt tegn på at alt er installert, bra jobba!

## Steg 2: Opprett et Node prosjekt
Nå som vi har et prosjekt gående i vår [[IDE]], er det på tide å erklære prosjektet som et node prosjekt. Dette gjøres i terminalen i samme mappe (samme sted hvor man kjørte `node app.js`).

For å erklære prosjektet skriver man: `npm init`

Her vil man få opp mange valg, men med standardvalg satt i parantes. Her trenger du ikke konfigurere noen ting, bare trykk enter til den spør om du er fornøyd og skriv `yes`!

Du skal nå kunne se en ny fil i mappen; `package.json`. Dette er filen som inneholder all relevant prosjektdata.

## Steg 3: Installer `express` npm modul
[Express](https://expressjs.com/) er et rammeverk for web- og mobilapplikasjoner som brukes til å "servere" filer i nettleseren. Express benytter seg av [[HTTP Metoder]] som [[GET]] og [[POST]] til å formidle data.

For å installere modulen, må man kjøre en enkel kommando i terminalen. Vi bruker [[NPM]] (Node Package Manager) på lik måte som vi gjør med PIP i Python og skriver inn: `npm install express`.

Mappen `node_modules` og filen `package-lock.json` skal nå dukke opp i prosjektmappa.

## Steg 4: Hello Node, fra Express
Vi skal nå endre `app.js` til å sende "Hello Node!" fra Express i en nettleser, istedetfor konsollen.

For å gjøre dette må vi først si til Javascript at vi skal bruke `express`. 
Vi må først importere modulen, det gjøres ved funksjonen `require(<modul>)`. 
Så må vi definere en app som bruker express, det gjøres ved å lage en [[01 Variabeltyper|javascript variabel]] som bruker express: `const app = express()`

Legg derfor inn denne linjen øverst i dokumentet:
```js
const express = require('express')
const app = express()
```

For å starte serveren må vi definere hvilken [[Nettverksport]] den skal kjøre fra. Standard-konvensjon (uskreven regel) for Express er å bruke port 3000. I fagspråk så definerer vi at express skal lytte på port 3000, og kommandoen for det er:

```js
app.listen(3000)
```

Denne skal ligge **nederst** i dokumentet.

### Legg inn HTTP metode
Nå har vi satt opp en express server, men innholdet er likevel tomt. For å legge til innhold, er vi først nødt til å definere en HTTP metode som express skal lytte på.

I nettlesere vil det sendes en [[GET]] forespørsel hver gang vi besøker en nettside som serveren prosesserer. Hvis serveren er satt opp riktig, så vil den også kunne sende data tilbake. 

For å definere dette, bruker vi funksjonen `app.<http-metode>(<sted>, function(forespørsel, svar){<kommandoer>}`. Vi kan bruke `forespørsel` eller `svar` til å enten lese forespørselsdataen, eller sende svar tilbake til den som sendte forespørselen. For å sende tilbake for eksempel ren tekst, bruker man funksjonen `.send(<tekst>)`

Det virker komplisert, men her er et eksempel i praksis:
```js
app.get('/', function(request, response){
	response.send('Hello Express!')
})
```
Alternativt kan man bruke en [[02 Arrow Functions|Arrow Functions]] for å forkorte koden:
```js
app.get('/', (request, response) => {
	response.send('Hello Express!')
})
```

Her er en forklaring på hva de ulike delene gjør:

- `app.get('/', ` - definerer at express skal høre etter forespørsler på `/`, som er det samme som hjemmeside (`example.com`). Eksempelvis hadde `app.get('/side2', ` lyttet etter `example.com/side2`
- `(request, response) => {...})` Er en funksjon med variablene `request` og `response`. Inne i `request` ligger det mye data som for eksempel hvilken nettleser som er brukt, hvilken enhet og hvilket nettsted som er forsøkt å besøke. `response` brukes til å sende data tilbake.
- `{ response.send('Hello Express!') })` er funksjonen som utføres når noen besøker `/`, som er hjemmesiden. Her vil serveren sende tilbake "Hello Express!" hver gang noen besøker hjemmesiden.

### Sett det sammen
Nå har vi sett på de ulike komponente vi trenger for å opprette en express-app. Til slutt skal vi sitte igjen med følgende kode:

```js
const express = require('express')
const app = express()

app.get('/', (request, response) => {
  response.send('Hello Express')
})

app.listen(3000)
```

Hvis vi nå kjører koden ved å bruke kommando `node app.js` i terminalen, kan vi besøke nettsiden på http://localhost:3000 og se vår Hello Express!

## Utfordring / Oppgave
Se nå om du klarer, utifra teksten over, å vise teksten "Du fant meg!" når vi besøker nettadressen http://localhost:3000/paaske-egg
