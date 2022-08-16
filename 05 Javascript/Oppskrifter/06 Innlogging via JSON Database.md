---
title: 06 Innlogging via JSON Database
aliases: [Innlogging via JSON Database,]
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - Javascript
created: 2022-04-09 02:00:00
updated: 2022-08-13 20:26:17
---
# Innlogging via JSON Database
Når vi skal behandle større mengder data lagres disse ofte i [[03 Datasystem, SQL|Databaser]], et format som er vanlig å bruke i programmering er [[JSON|JSON]] formatet. Det er en tekstfil med data hvor verdier får en nøkkel som inneholder eventuelt flere verdier, dette kalles for [[Nesting]].

## Opprett en databasefil
Lag en ny fil i prosjektmappen og kall denne for `database.json`. Her må vi tenke oss frem til et design av vår database. I tilfellet med innlogging så kan vet vi at vi trenger følgende verdier:
- Liste over `users`
- Hver `user` må ha en unik ID (brukernavn) og som regel minst ha følgende verdier:
	- `password`
	- `username`

Vår `.json` fil kan derfor bruke følgende tekst som mal:
```json
{
  "users": {
    "test": {
      "username": "test",
      "password": "123456",
    },
  },
}
```

Merk at man kan legge til flere verdier, separert med komma:
```json
{
  "users": {
    "test": {
      "username": "test",
      "password": "123456",
    },
    "test2": {
      "username": "test2",
      "password": "123456",
    },
  },
}
```

## Importer i Javascript
For å importere filen er det mange måter å gjøre det på, den enkleste er å bruke `require('./filnavn')` funksjonen, som vil returnere filens innhold. Merk at vi må bruke `./` for å definere at filen ligger i vår rotmappe. Vi kan navigere oss inn i databasen ved å spesifisere hvilken nøkkel vi vil ha:

```javascript
const database = require('./database.json')
console.log(database["users"]["test"]["password"])

// Output: password
```

Vi tar utgangspunkt i vår `app.post('/auth')` funksjon vi lagde i forrige kapittel, men med noen endringer:

`app.js`
```javascript
app.post('/auth', (request, response) => {
	var database = require('./database.json')

	var brukernavn = request.body.username
	var passord = request.body.password

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

Koden vil nå:
- Laste inn databasefilen (Lese den)
- Definere brukernavnet utifra innloggingsforespørselen, lagres til `brukernavn`
- Definere passordet utifra innloggingsforespørselen, lagres til `passord`
- Forsøke å hente verdien til nøkkelen `"username"`, inne i nøkkelen: `"users"` inne i brukernavnet - lagres til `db_brukernavn`
- Forsøke å verdien til nøkkelen `"password"` inne i nøkkelen: `"users"` inne i brukernavnet - lagres til `db_passord`
- Sjekk om `brukernavn == db_brukernavn` og `passord == db_passord`
- Hvis ja, gjør X, hvis ikke, gjør Y

## Tips
For å gjøre koden litt mindre, kan vi definere hvilken del av databasen vi vil ønsker. Denne koden vil gjøre det samme som den over, men med mindre kompleksitet ettersom vi starter fra en definert nøkkel:
```javascript
const database = require('./database.json')["users"]
console.log(database["test"]["password"])
```

Vår innlogging kan og gjøres enklere med samme metodikk:
`app.js`
```javascript
app.post('/auth', (request, response) => {
	var brukernavn = request.body.username
	var passord = request.body.password

	var database = require('./database.json')["users"][brukernavn]

	// Sjekk om data stemmer
	if (brukernavn == database["username"] && passord == database["password"]){
		response.send(`Velkommen inn, ${brukernavn}!`)
	} else {
		response.send("Feil brukernavn eller passord")
	}
}
```

Bruk funksjonen `.toLowerCase()` bak sammenligningen av brukernavn for å unngå å måtte skille mellom store og små bokstaver.