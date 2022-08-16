---
title: 04 Express HTML - Pug Templating
aliases: [Express HTML - Pug Templating,]
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - Javascript
  - HTML
  - Pug
created: 2022-04-09 04:00:00
updated: 2022-08-15 22:47:18
---
# Express HTML - Pug Templating
Nå skal vi se på en Templating Engine som heter [pug](https://pugjs.org/) - hva er en [[Templating Engine]] spør du? Jo - det er rett å slett noe som tar imot en form for innhold, og genererer en mer komplisert versjon. Den kan også ta imot verdier, som er grunnen til at en templating engine er nyttig.

Formålet med det er å konvertere noe vanskelig, tidkrevende, eller begge deler - til noe enklere og mer programmeringsvennlig.

## Installasjon av pugjs
For å installere pugjs, må vi gå inn i terminalen i vårt node prosjekt og skrive følgende kommando:
```bash
npm install pug
```

Verre er det faktisk ikke!

For å ta i bruk pug, må vi legge til en linje under vår "app" funksjon i node appen vår, hvor vi definerer hvilken `view engine` vi ønsker å bruke. Det gjør vi ved å legge inn følgende linje:
```js title="app.js"
const app = express()
app.set('view engine', 'pug')
```

## Eksempel med og uten pug
Til vanlig kan vi bruke `response.send(<innhold>)` for å sende tilbake innhold når en forsøker å nå en ressurs på vår Express app. Det vi legger i `<innhold>`, vil bli sendt til nettleseren. Ønsker vi derfor å sende ut en HTML side, må vi derfor sende hele HTML koden, slik som dette:

```js title="app.js"
app.get('/', function (request, response) {
  html = `
<html>
<head>
  <title>Min side</title>
</head>
<body>
  <h1>Velkommen!</h1>
</body>
</html>
`
  response.send(html)
})
```
Tungvint og rotete, ikke sant?

Med pug, kan vi heller bruke en `.pug` fil til å definere hvordan vår HTML side skal se ut, som gjør det mye lettere å håndtere hvordan man sender en fin side tilbake til leseren. Filene må ligge i en mappe som heter `views` i samme prosjektmappe.

Hvis vi lager en fil i `views` mappen som heter `index.pug`, (filbane: `views/index.pug`) - så kan vi skrive inn syntaksen pug tar. Merk at du KAN bruke vanlig HTML kode i en `.pug` fil.

```pug title="views/index.pug"
html
  head
    title Min Side
  body
    h1 Velkommen
```

For å tegne denne i Express, bruker vi `response.render('index.pug', {data})` istedet. `(, {data})` Er valgfritt å denne kommer vi tilbake til!
```js title="app.js"
app.get('/', function (request, response) {
  response.render('index')
})
```

Resultatet? Helt likt som det over!

## Legge til style.css
I tradisjonell HTML, så bruker vi en `<link>` tag til å importere CSS kode. Det gjør vi ikke i Pug. I stedet legger vi til hele `style.css` filen inn i en og en fil ved å bruke `include` funksjonen.

Hvis vi har en `views/style.css`, som bruker standard css kode, så kan vi importere denne i vår `index.pug` slik:
```pug title="views/index.pug"
html
  head
    title Min Side
    style
	    include style.css
  body
    h1 Velkommen
```

## Sende variabler til Pug
Nå kommer vi tilbake til `(, {data})` - det kule med pug er at vi kan sende data til våre `.pug` filer fra NodeJS, som for eksempel kan være hentet fra en [[Cookie]]. Vi skal komme tilbake til cookies senere. Pug tar imot vanlig Objekt, eller [[JSON]] data.

```js title="app.js"
app.get('/', function (request, response) {
  data = {
	"brukernavn": "Jens",
	"email": "Jens@jensen.no",
	"nymail": 22
  }
  response.render('index', data)
})
```

```pug title="views/index.pug"
html
  head
    title Min Side
    style
	    include style.css
  body
    h1 Velkommen, #{brukernavn}. Din e-post konto, #{email}, har #{nymail} nye beskjeder. 
```

## Class og ID
Til vanlig i HTML bruker vi `class=""` og `id=""` mye i våre tagger for å kunne selektere elementer i [[CSS]], f.eks. `<h1 class="tittel">Min Tittel</h1>` får CSS selektoren `.tittel {<css her>}`. I pug gjøres dette før du legger til innholdet:
```pug title="views/index.pug"
html
  head
    title Min Side
    style
	    include style.css
  body
    h1.tittel Min Tittel, med klasse "tittel"
    h2#tittel Min andre tittel, men med ID tittel
    div#innhold
	    p innhold i divven med ID innhold
	#div2
		p Innhold i divven med ID div2
```

## Attributter i Pug
Attributter, eller nøkler og verdier i elementer: `<a nøkkel="verdi" nøkkel2="verdi2">`, legges til i paranteser. For eksempel en lenke:
```pug title="views/index.pug"
body
	div#meny
		a(href="/") Hjem
		a(href="/login") Logg inn
```

Du kan også gjøre det som vanlig HTML, ofte er det enklere når vi skal ha ting på samme linje:
```pug title="views/index.pug"
body
	div#meny
		button <a href="/">Hjem</a>
		button <a href="/login">Logg inn</a>
```

## Layouts
En enda kulere ting, er at pug kan bygge på andre pugger. Det betyr at vi kan ha en pug som er mal for nettsiden, og en pug som er bare innholdet. Lettest å se med eksempel:

```pug title="views/layout.pug"
html
  head
    title Min side
    style
      include style.css
  body
    header
      block header
    section
      block content
    footer
      p Copyright Navn Navnesen
```

```pug title="views/index.pug"
extends layout.pug

block header
  h1 Min hjemmeside!

block content
  p Du er nå på min indeks side.
  p Trykk <a href="/login">her</a> for å logge deg inn.
```

I app.js er det fremdeles gode gamle:
```js title="app.js"
app.get('/', function (request, response) {
  response.render('index')
})
```

## Det finnes mye mer, Google er kongen!
Dette er bare et lite fnugg av hva som er mulig med Pug. Du kan gjøre loops (Vis alle søkeresultater for ...), gjøre IF statements (Hvis loggetinn = sant, hvis X).

Dette skal legges inn på siden senere, for nå må du google!

## Les mer
[Getting Started – Pug](https://pugjs.org/api/getting-started.html)
[Jinja — Jinja Documentation (3.1.x)](https://jinja.palletsprojects.com/en/3.1.x/)