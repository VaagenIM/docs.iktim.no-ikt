---
title: 05 Enkel Innloggingsdemo
aliases: [NodeJS - Enkel Innloggingsdemo,]
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - Javascript
created: 2022-04-09 02:00:00
updated: 2022-08-13 20:26:09
---
# Enkel Innloggingsdemo
Ut ifra det vi nå har lært om [[04 Express HTML Pug Templating|Pug Templating]] og Express, skal vi lage en enkel demo for innlogging. Vi kommer til å se på hvordan vi sender data mellom [[Frontend]] og [[Backend]] med ulike [[HTTP Metoder]]. Merk at alt som skjer på Frontend er synlig for endebruker, det er ikke Backend. Man kan altså behandle data som passord på Frontend, men det er ikke så lurt!

Verdt å merke så er dette IKKE en sikker måte å gjøre ting på, men det synliggjør mer avanserte problemstillinger vi må ta henhold til senere.

## Sett opp en Login side (GET-metode)
I vår `app.js` må vi legge inn en ny side hvor vår app lytter på [[GET]] forespørsler til en ny side, `/login`, som viser innholdet i en ny Pug vi lager, `views/login.pug`. Innholdet må være et skjema som sender vår innloggingsinformasjon tilbake til vår Express [[Backend]]. Dette gjøres i form av et HTML `<form>` ([W3schools - HTML Forms](https://www.w3schools.com/html/html_forms.asp)).

`app.js`
```js
app.get('/login', (request, response) => {
	response.render('login')
})
```

Merk at `render('login')` refererer til `views/login.pug`.

`login.pug`
```pug
html
	head
		title Logg inn
		style
			include style.css
	body
		h1 Logg inn med ditt brukernavn og passord!
		form(action="/auth" method="get")
			input(type="text" placeholder="Brukernavn" name="username")
			br
			input(type="password" placeholder="Passord" name="password")
			br
			input(type="submit" value="Logg inn")
		h1 Ikke registrert? <a href="/signup">Registrer deg da vel</a>.
```

Dette vil generere en HTML side med 2 tekstfelt og en "Logg inn" knapp. Skjemaet bruker parametrene `(action="/auth" method="get")`, som sier noe om hvordan skjema-dataen vil bli behandlet. I dette tilfelle vil den generere og gå til en lenke: `/auth?name=value&name2=value2`. Vi bruker 2 ulike `name` verdier, `username` og `password`. `value` kommer av hva bruker har skrevet inn.

Skriver vi derfor inn 123 som brukernavn, 456 som passord, vil den sende oss til: `/auth?username=123&password=456`

For å håndtere dataen videre, må vi validere at det er brukt riktig brukernavn og passord. Dette gjør vi ved å sette opp en til GET funksjon som lytter på `/auth` i `app.js`, siden vårt skjema bruker `method="get"`.

Verdiene vi får legger seg automatisk inn i `request` objektet som tas inn i funksjonen, under et underobjekt som heter [[Query]] (forespørsel). For testen sin skyld bruker vi brukernavnet: `Ole` og passord: `123`

`app.js`
```js
app.get('/auth', (request, response) => {
	console.log(request.query)
	// Printer {username:"verdi", password:"verdi"}
	var brukernavn = request.query.username
	var passord = request.query.password

	// Sjekk om data stemmer
	if (brukernavn == "Ole" && passord == "123"){
		response.send("Velkommen inn, Ole!")
	} else {
		response.send("Feil brukernavn eller passord")
	}
})
```

## POST metode
Nå har vi sett på GET metoden for å sende data, som legger inn dataen direkte i URL'en, `?nøkkel=verdi&nøkkel2=verdi2&nøkkel3=verdi3`. Nå skal vi se på POST metoden, som sender dataen "bak kulissene".

For å benytte oss av [[POST]], bytter vi bare ut `form(method="get")` med `form(method="post")`:

`login.pug`
```pug
html
	head
		title Logg inn
		style
			include style.css
	body
		h1 Logg inn med ditt brukernavn og passord!
		form(action="/auth" method="post")
			input(type="text" placeholder="Brukernavn" name="username")
			br
			input(type="password" placeholder="Passord" name="password")
			br
			input(type="submit" value="Logg inn")
		h1 Ikke registrert? <a href="/signup">Registrer deg da vel</a>.
```

For å kunne lese `post` forespørsler er vi nødt til å definere at vi leser `post`forespørsler i [[JSON]] format - dette gjør vi ved å legge inn følgende kommando, der hvor vi definerer `'view engine', 'pug'`:

```javascript
app.use(express.json())
app.use(express.urlencoded({ extended: true }))
```

I `app.js` må vi også endre fra `get` til `post` forespørsler. Det er heller ikke verre enn å bytte ut `.get()` med `.post()` - forskjellen her blir bare hvor vi henter verdiene fra. Nå kommer de ikke fra forespørselen ([[Query]]), men fra en annen usynlig forespørsel med innhold. Nettleseren sender altså et brev (post) av innhold bak kulissene, og det som blir lest av er `body` delen av brevet, som på norsk kan oversettes til innhold. `request.query` (URL, GET) blir derfor byttet ut med `request.body` (POST)

`app.js`
```js
app.use(express.json())
app.use(express.urlencoded({ extended: true }))

app.post('/auth', (request, response) => {
	var brukernavn = request.body.username
	var passord = request.body.password

	// Sjekk om data stemmer
	if (brukernavn == "Ole" && passord == "123"){
		response.send("Velkommen inn, Ole!")
	} else {
		response.send("Feil brukernavn eller passord")
	}
})
```

## Tips
Hvis man vil unngå å måtte skille mellom små og store bokstaver, så kan man bruke `.toLowerCase()` funksjonen. Merk at brukernavnet må da også lagres med små bokstaver.
```javascript
var brukernavn = request.body.username.toLowerCase()
```