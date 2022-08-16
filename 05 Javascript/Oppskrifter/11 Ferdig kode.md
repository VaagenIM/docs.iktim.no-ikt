---
title: 11 Ferdig kode
aliases: [11 Ferdig kode,]
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - missing
created: 2022-04-26 02:00:00
updated: 2022-08-13 20:26:20
---
# Ferdig kode
Den ferdige koden til prosjektet kan lastes ned her: https://github.com/VaagenIM/JS-UserLogin-Demo

Fullstendig `app.js`:
```js
const express = require('express')
const fs = require('fs')
const session = require('express-session')
const { sha512, } = require('./crypto')

const port = 3000
const app = express()

app.set('view engine', 'pug')

// Håndter POST forespørsel
app.use(express.json())
app.use(express.urlencoded({ extended: true }))

// Konfigurer cookie
const crypto_salt = "MittCookiePassord, holdes hemmelig!"
app.use(session({
  secret: crypto_salt,
  resave: true,
  saveUninitialized: true
}))

// Legges nede
app.post('/signup', (request, response) => {
  var db = {}
  try   { db = require('./database.json') }
  catch { db = {"users":{}} }

  var brukernavn = request.body.username
  var brukernavn_lower = brukernavn.toLowerCase()
  var passord = sha512(request.body.password)

  // Sjekk at bruker ikke eksisterer
  if (!db["users"][brukernavn_lower]) {
    // Legg til nøkkel [brukernavn] i databasen, som inneholder følgende nøkler/verdier
    db["users"][brukernavn_lower] = {
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

app.post('/auth', (request, response) => {
  var brukernavn = request.body.username.toLowerCase()
  var passord = sha512(request.body.password)

  var database = require('./database.json')

  // Sjekk om data stemmer
  if (database["users"][brukernavn] && passord == database["users"][brukernavn]["password"]) {
    // Hvis login info er korrekt, legg til i cookie:
    request.session.loggedin = true
    request.session.name = database["users"][brukernavn]["username"]
    //
    response.redirect('/')
  } else {
    response.send("Feil brukernavn eller passord")
  }
})

app.get('/login', (request, response) => {
  response.render('login')
})

app.get('/signup', (request, response) => {
  response.render('signup')
})

// Logg ut funksjon fungerer av å slette cookie
app.get('/logout', (req, res) => {
  req.session.destroy()
  res.redirect('/')
})

app.get('/', (request, response) => {
  // Send Cookie i tillegg når vi rendrer index.pug (request.session)
  response.render('index', request.session)
})

app.listen(port, () => { console.log(`Listening on port: ${port}`) })
```