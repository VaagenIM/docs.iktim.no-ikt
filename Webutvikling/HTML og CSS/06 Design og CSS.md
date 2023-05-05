---
title: 6. Design og CSS
aliases: 
  - 06 Design og CSS
  - CSS
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - HTMl
  - CSS
  - Web
created: 2022-08-21 14:43:47
updated: 2023-05-05 12:40:06
---
# 06 Design og CSS
CSS (Cascading Style Sheets) er et stilsett-språk som brukes til å definere utseendet og oppførselen til HTML-elementer på en nettside. CSS skiller seg fra HTML ved at det fokuserer på presentasjonen av nettsiden, mens HTML fokuserer på innholdet.

CSS brukes til å definere stil- og layout-egenskaper for HTML-elementer, som farger, skriftstørrelser, marginer, padding og posisjonering. CSS kan enten inkluderes direkte i HTML-dokumentet ved hjelp av `<style>`-taggen, eller i en separat CSS-fil som refereres til fra HTML-dokumentet.

CSS bruker en rekke regler for å definere stiler for forskjellige HTML-elementer. Hver regel består av en selektor, som bestemmer hvilke HTML-elementer regelen skal påvirke, og en deklarasjonsblokk, som inneholder stil-egenskapene som skal påføres på elementene.

Her er en enkel forklaring på CSS-regler i markdown-format:
-  En CSS-regel består av en selektor og en deklarasjonsblokk, som er adskilt av krøllparenteser `{}`.
-  Selektoren bestemmer hvilke HTML-elementer som regelen skal påvirke, og kan være en enkel elementselektor, en klasse-selektor, en ID-selektor eller en kombinasjon av disse.
-  Egenskaper og verdier defineres innenfor deklarasjonsblokken ved å bruke syntaksen `egenskap: verdi;`, for eksempel `color: blue;` for å definere fargen på teksten.

## Eksempel
I dette eksempelet er CSS bakt inn i HTML dokumentet. Merk at man vanligvis ville brukt en egen `.css` fil som ville vært lenket opp i `<head>` taggen, slik at de definerte stilene kan gjenbrukes av flere dokumenter.

```html
<head>
	<style>
		h1 {
			color: blue;
		}
	</style>
</head>
<body>
	<h1>Denne teksten er blå!</h1>
	<h2 style="color: red;">Denne teksten er rød.</h2>
</body>
```