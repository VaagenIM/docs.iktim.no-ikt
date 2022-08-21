---
title: 03 Hvordan skrive HTML
aliases: 
  - Hvordan skrive HTML
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - HTML
  - Web
created: 2022-08-21 13:41:53
updated: 2022-08-21 13:41:57
---
# 03 Hvordan skrive HTML
Innhold i HTML plasseres mellom tagger som har en start og en slutt, disse kalles for tagger.

## Åpning av tag: `<tag>`
Starten, eller åpningen på en tag defineres av mindre-enn og mer-enn symbolene; `<` og `>`, med taggen mellom tegnene. Et eksempel kan være taggen `html`, hvor innholdet etter åpningen blir definert som HTML tekst. For å starte HTML taggen skriver man da `<html>`.

## Lukking av tag: `</tag>`
For å lukke en tag følger man nesten samme syntaks som når man åpnet den, men etterfulgt av `/` symbolet i starten. Symbolene for å avslutte en tag blir derfor `</` og `>`. For å lukke `<html>` taggen må vi derfor plassere en `</html>` tag etter innholdet: `<html>Innhold her</html>`.

## html, head og body.
I HTML bruker man 3 tagger for å definere hvert nettsted vi lager; `<html>`, `<head>` og `<body>`.

`<html>` definerer hva som er hypertekst, som regel er all tekst i et `.html` dokument hypertekst. Man velger likevel å lage taggen ettersom enkelte nettlesere eller programvare behøver taggen for å kunne tolke siden på riktig måte.

Et standard oppsett pleier å ha følgende struktur:

```html title="index.html"
<html>
  <head>
  </head>
  <body>
  </body>
</html>
```

### head
Man kan tenke på innholdet i `<head>` som hjernen til siden, det som skjer bak kulissene. Her plasserer man tagger og innhold som ikke nødvendigvis er synlig på nettsiden, men som gjerne spiller en rolle for å definere utseendet til nettsiden.

`<head>` er også stedet hvor man kan definere tittelen til et nettsted ved hjelp av en `<title>` tag. Man kan ikke se det i innholdet på siden, men i fanen til nettleseren:

```html
<head>
	<title>Min nettside</title>
</head>
```

### body
Kroppen er det vi ser, bokstavelig talt. Man kan ikke direkte se hva som foregår inne i hodet på noen, men vi kan se kroppen. Her plasseres innhold som vi vil at besøkende skal se.

```html
<body>
	Hello World!
</body>
```

## Hello World
Ved å kombinere det du nå har lest kan du lage ditt aller første nettsted:

```html title="index.html"
<html>
  <head>
	<title>Min nettside</title>
  </head>
  <body>
	Hello World!
  </body>
</html>
```