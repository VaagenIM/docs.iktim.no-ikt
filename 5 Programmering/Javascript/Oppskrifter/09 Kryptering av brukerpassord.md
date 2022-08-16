---
title: 09 Kryptering av brukerpassord
aliases: [Kryptering av brukerpassord,]
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - Javascript
created: 2022-04-09 02:00:00
updated: 2022-08-13 20:26:21
---
# Kryptering av brukerpassord
Dette er UTROLIG viktig, og er et lovbrudd dersom man lar være å kryptere data i ekte bruksområder. Det er heller ikke så vanskelig.

Dokumentet er ikke ferdig.


## Lag et krypteringsbibliotek
Vi må først lage et nytt bibliotek over funksjoner, dette er ikke et must - men det gjør at vi kan holde koden mer ryddig. Vi lager derfor et ny `.js` dokument og kaller denne for `crypto.js`. Denne skal inneholde funksjoner som gjør det enklere for oss å kryptere innhold.

`crypto.js`
```javascript
const crypto = require('crypto')

const sha512 = x => crypto.createHash('sha512').update(x, 'utf8').digest('hex')

module.exports = {sha512}
```

Denne koden lager en ny funksjon, `sha512(tekst)`, som returnerer samme teksten i [[Hashing|Hashet]] format.

# Legg til sha512 i vår Express app
For å legge til vårt nye bibliotek må vi legge til følgende variabel øverst på vår app, slik med våre andre biblioteker.
`app.js`
```javascript
const { sha512, } = require('./crypto')
```

Denne importerer sha512 funksjonen fra `crypto.js` i samme mappe som `app.js`.

For å ta i bruk algoritmen trenger vi kun å endre alle referanser til `req.body.password` til å være `sha512(req.body.password)`, som i f.eks. `app.post('/auth')` funksjonen:

`app.js`
```javascript
app.post('/auth', (request, response) => {
	var database = require('./database.json')

	var brukernavn = request.body.username

	// Her er endringen
	var passord = sha512(request.body.password)
	////////////////////////////////////////////

	var db_brukernavn = database["users"][brukernavn]["username"]
	var db_passord = database["users"][brukernavn]["password"]

	// Sjekk om data stemmer
	if (brukernavn == db_brukernavn && passord == db_passord){
		response.send(`Velkommen inn, ${brukernavn}!`)
	} else {
		response.send("Feil brukernavn eller passord")
	}
})
```

Det samme gjelder når vi lager vår bruker i `app.post('/signup')`

`app.js`
```javascript
// Legges øverst
const fs = require('fs')

// Legges nede
app.post('/signup', (request, response) => {
	var db = require('./database.json')

	var brukernavn = request.body.username
	// Her er endringen
	var passord = sha512(request.body.password)
	///////////////////////////

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

Nå vil passordene som blir laget av bruker, og det som blir lagret i databasen, bli omgjort til en annen variant ved hjelp av `sha512` sin hashingsalgoritme. `passord` i `sha512` er eksempelvis `a9d50700baec3d1e40c238bcb37847d3a9633e174dfabeeddcac68d661d02937f71c0edba8b41602e8993015c465ec330f40843849c163d9235d00542a96e3a1` - Dette er ikke reverserbart, og er derfor mye tryggere å lagre.

Merk at brukeren trenger **ikke** skrive mer enn `passord` når han logger inn og trenger derfor ikke tenke på algoritmen.

## Pepper
[[Salt og Pepper]] er mye brukt i kryptografi, vi har sett på hvordan man salter en cookie i [[08 Cookies|Cookies]], som gjør det vanskelig å lese data i cookie filen dersom den skulle på en eller annen måte lekke ut. Pepper er en annen måte å [obfuskere](https://naob.no/ordbok/obfuskere) data på er gjennom peppring, som er en ekstra streng av tekst som legges til før dataen blir hashet.

Eksempel kan være at dersom en bruker `Passord123` som passord, kan det bli pepret med `dZ0lyQg90NuDfmp2U6FJDmBUE6xMme`. Passordet vil da bli for eksempel `Passord123dZ0lyQg90NuDfmp2U6FJDmBUE6xMme`, hvis vi legger pepperet på slutten av teksten.

Vi kan fint legge til pepperet i vår funksjon slik:

`crypto.js`
```javascript
const crypto = require('crypto')
const pepper = "dZ0lyQg90NuDfmp2U6FJDmBUE6xMme"

const sha512 = x => crypto.createHash('sha512').update(x + pepper, 'utf8').digest('hex')

module.exports = {sha512}
```