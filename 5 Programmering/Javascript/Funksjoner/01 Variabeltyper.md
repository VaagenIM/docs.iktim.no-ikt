---
title: Variabler - let, var, const
aliases: [Javascript variabler,]
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - Javascript
created: 2022-04-09 02:00:00
updated: 2022-08-13 20:25:29
---
# Variabler - let, var, const
I Javascript er det tre forskjellige måter å opprette variabler på.

De har samme funksjon, men ulike egenskaper.

## var
`var` definerer en variabel som kan endres på. Når en variabel lages med `var`, må den ikke nødvendigvis inneholde en verdi.
```js
var Tall = 1
var Tall2
Tall2 = 2

console.log(Tall) // 1
console.log(Tall2) // 2
```

## let
`let` er nesten helt lik `var`, men fungerer bare i samme "blokk".
```js
let Tall = 1

if (Tall) { // Hvis tall eksisterer, som det gjør.
	let Tall = 2
	console.log(Tall) // 2
}

console.log(Tall) // 1
```

## const
`const` er en konstant variabel, som betyr at den kan ikke endre seg etter den først er erklært.

```js
const Tall = 1

try { // Prøv å endre tall
	Tall = 2
} catch (err) { // Hvis det er feil, fang den som <err>
	console.log(err) // TypeError: Assignment to Constant Variable
}

console.log(Tall) // 1
```

## Les mer:
[Var, Let, and Const – What's the Difference?](https://www.freecodecamp.org/news/var-let-and-const-whats-the-difference/)