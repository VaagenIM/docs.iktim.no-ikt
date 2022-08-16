---
title: 08 Cookies
aliases: [Cookies,]
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - Javascript
  - Cookie
created: 2022-04-25 02:00:00
updated: 2022-08-13 20:26:32
---
# Cookies
Forklaring kommer snart. [[Cookie]]

`npm install express-session`

```javascript
// Legges øverst
const session = require('express-session')

// Konfigurer cookie
const crypto_salt = "MittCookiePassord, holdes hemmelig!"

// Sett opp cookie
app.use(session({
  secret: crypto_salt,
  resave: true,
  saveUninitialized: true
}))

app.post('/auth', (request, response) => {
	var brukernavn = request.body.username
	var passord = request.body.password

	var database = require('./database.json')

	// Sjekk om data stemmer
	if (brukernavn == database["users"][brukernavn] && passord == database["users"][brukernavn]["password"]){
		// Hvis login info er korrekt, legg til i cookie:
		request.session.loggedin = true
		request.session.name = brukernavn
		// Merk at du kan lagre hva som helst under request.session
		request.session.hvasomhelst = "Ja, hva som helst"
		//
		response.send(`Velkommen inn, ${brukernavn}!`)
	} else {
		response.send("Feil brukernavn eller passord")
	}
})

// Logg ut funksjon fungerer av å slette cookie
app.get('/logout', (req, res) => {
  req.session.destroy()
  res.redirect('/')
})

app.get('/', (request, response) => {
	// Sjekk om bruker er logget inn
	if (request.session.loggedin) {
		response.send(`Hei, ${request.session.name}!`)
	} else {
		response.send('Hei, du må <a href="/login">Logge deg inn</a>.')
	}
})
```