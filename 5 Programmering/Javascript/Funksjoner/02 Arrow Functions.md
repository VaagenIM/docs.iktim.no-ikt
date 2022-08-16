---
title: Arrow Functions
aliases: [Arrow Functions,]
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - Javascript
created: 2022-04-09 02:00:00
updated: 2022-08-13 20:25:53
---
# Arrow Functions
Arrow Functions er rett og slett en annen konvensjon (uskreven regel) på hvordan man skriver funksjoner i Javascript uten navn. Forskjellen er at man ikke skriver hele syntaksen, men heller bruker `=>` symbolet.

Arrow functions brukes mye til "anonyme funksjoner", som er funksjoner uten navn.

Eksempel med `Express`	
```js
app.get('/', (request, response) => {
	response.send("Hello World")
})

app.get('/', function(request, response) {
	response.send("Hello World")
})
```

Arrow functions brukes og mye i diverse funksjoner med bare 1 callback, hvor paranteser ikke er nødvendige. Callback vil si en funksjon som kjører som følge av funksjonen som blir forespurt. For eksempel når man leser en fil, vil man gi innholdet i filen et navn.

Eksempel, denne vil printe ut innholdet i `minfil.txt`:
```javascript
const fs = require("fs")

fs.readFile('minfil.txt', variabelnavn => {
	console.log(variabelnavn)
})

fs.readFile('minfil.txt', (variabelnavn) => {
	console.log(variabelnavn)
})

fs.readFile('minfil.txt', function(variabelnavn) => {
	console.log(variabelnavn)
})
```

## Les mer
[Arrow function expressions - JavaScript | MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)