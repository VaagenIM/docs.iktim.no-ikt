---
title: 07 Brukerregistrering
aliases: [Brukerregistrering,]
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - Javascript
created: 2022-04-09 02:00:00
updated: 2022-08-13 20:26:15
---
# Express - Brukerregistrering
Nå som vi har sett på hvordan man bruker en [[JSON]] database i Javascript, skal vi se på noe som tar det opp enda flere hakk - nemlig prosessen av å legge til innhold i en JSON database. Vi må dog og sette opp en side for å registrere vår bruker.

Heldigvis for oss, er det ikke noe verre enn når vi skrev inn vår `.json` fil manuelt, og skrive 2 linjer av kode som lagrer den. Vi trenger kun å importere `fs` modulen og bruke kommandoen `fs.writeFileSync(_filbane_, JSON.stringify(_database_))`

Her er et demoeksempel:
```javascript
const fs = require('fs')
// ^ Plasseres øverst i dokumentet

var db = {
	"users":{
		"test":{
			"username": "test",
			"password": "123456"
		}
	}
}

// Lagre db til database.json
fs.writeFileSync('./database.json', JSON.stringify(db))`
```

## Legge til en verdi på eksisterende database
Når vi skal for eksempel legge til en ny bruker i vår JSON database, må vi først importere vår database, bekrefte at brukeren ikke allerede eksisterer og så legge den til, så lagre.

For nå setter vi opp en `app.post('/signup')` funksjon - vi setter opp registreringssiden senere.

Det gjør vi ved å bruke `if(!db[nøkkel])` - denne sjekker om nøkkelen i vår database IKKE eksisterer, som betyr at den ikke er i bruk. Høres vanskelig ut? Kanskje, men se eksempel og prøv å forstå hva linjene gjør, linje for linje:

`app.js`
```javascript
// Legges øverst
const fs = require('fs')

// Legges nede
app.post('/signup', (request, response) => {
	var db = require('./database.json')

	var brukernavn = request.body.username
	var passord = request.body.password

	// Sjekk at bruker ikke eksisterer
	if (!db["users"][brukernavn]) {
		// Legg til nøkkel [brukernavn] i databasen, som inneholder følgende nøkler/verdier
		db["users"][brukernavn] = {
			"username": brukernavn,
			"password": passord
		}
		
		// Lagre databasen
		fs.writeFileSync('./database.json', JSON.stringify(db))
		
		// Send videre til innlogging
		response.redirect('/login')
		
	} else {
		response.send('En bruker med det navnet eksisterer allerede')
	}
})
```

Her gjør koden følgende:
- Importer databasen
- Hent ut verdiene brukernavn og passord fra en `form` forespørsel
- Sjekk at databasen ikke har verdien `brukernavn` i `"users"`, hvis den finnes, send beskjed om det.
- Legg til nøkkelen `brukernavn` med nøklene og verdiene til `username` og `password`
- Lagre filen med endringene
- Send bruker videre til `/login`

Merk at koden tar utgangspunkt i at `database.json` eksisterer og er satt opp med riktig struktur. Strukturen som er minimum er: `{"users":{}}`

Et alternativ er å generere strukturen dersom `database.json` ikke finnes:
```javascript
app.post('/signup', (request, response) => {
	  var db = {}
	  try   { db = require('./database.json') }
	  catch { db = {"users":{}} }
	  // catch kjører, HVIS try gir feilmelding
	  // Resten av koden her ...
}
```

## Tegn en registreringsside
Vi har allerede sett på hvordan vi lager en innloggingsside, en registreringsside er jo på mange måter ganske lik.

Vi kan derfor gjenbruke vår `login.pug` og lage en ny, med noen små endringer:

`views/signup.pug`
```pug
html
	head
		title Registrer din bruker
		style
			include style.css
	body
		h1 Lag din nye superkonto!
		form(action="/signup" method="post")
			input(type="text" placeholder="Brukernavn" name="username")
			br
			input(type="password" placeholder="Passord" name="password")
			br
			input(type="submit" value="Registrer konto")
```

Vi må og legge til funksjonen som tegner registreringssiden, slik som vi gjorde med `/login`:

`app.js`
```javascript
app.get('/signup', (request, response) => {
	response.render('signup')
})
```

## Tips
Som i tipset i [[05 Enkel Innloggingsdemo]] så kan det være lurt å bruke funksjonen `.toLowerCase()` når man skal lagre brukernavnet, for å ikke måtte skille mellom store og små bokstaver i brukernavnet:
```javascript
var brukernavn = request.body.username
var brukernavn_lower = brukernavn.toLowerCase()
// ...
if (!db["users"][brukernavn_lower])
	db["users"][brukernavn_lower] = {
		"username": brukernavn,
		"password": passord
	}
	// ...
```

## Utfordring
Utifra det du har lest om i dette kapittelet, klarer du å legge til mer informasjon som kan lagres i databasen? For eksempel brukerens e-post, eller telefonnummer?