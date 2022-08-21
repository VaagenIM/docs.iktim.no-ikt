---
title: 5. Mappestruktur og relative stier
aliases: 
  - 05 Mappestruktur og relative stier
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - HTML
  - Web
created: 2022-08-21 13:58:23
updated: 2022-08-21 13:58:27
---
# 05 Mappestruktur og relative stier
Det viktigste når man lager en HTML nettside er en god mappestruktur og forståelse for relative filstier.

En relativ filsti vil være plasseringen av et dokument relativt til dokumentet den lenkes fra. 

## Rotmappe (`/`)
Rotmappe, eller root, er den øverste mappen i prosjektet. For å linke til root kan man bruke `/` som filsti. Bruk av rotmappe er den letteste måten å håndtere relative lenker på, ettersom stiene er relative til rotmappen og ikke de individuelle dokumentene.

> [!warning] Obs:
> Rotmappen vil ikke fungere for nettsider som ikke er tilgjengelig via internett, ettersom rotmappen defineres av tjeneren som holder nettsiden oppe.
> 
> I noen [[Integrated Development Environment|IDE]] programmer vil forhåndsvisningen av nettsiden holdes oppe av en midlertidig tjener som tillatter bruk av rotmappe.

## Opp èn mappe `../`
For å gå opp en mappe bruker man `../` symbolene, gjerne flere ganger: `../../min-side.html`.

## Eksempel
Hvis vi har følgende mappestruktur:

```
Min-Nettside/
	index.html
	side2.html
	img/
		bilde.jpg
	ekstra/
		side3.html
```

Så kan man bruke ressursene ved å linke til dem i forhold til dokumentet de lenkes fra:

```html title="index.html"
<a href="index.html">Hjem</a>
<a href="side2.html">Side 2</a>
<a href="ekstra/side3.html">Side 3</a>
<img src="img/bilde.jpg">
```

Men for `side3.html` er ikke ressursene på samme sted relativt til `index.html` eller `side2.html`. Da må vi bruke enten `/` eller `../`

```html title="ekstra/side3.html"
<a href="/index.html">Hjem</a> <!-- Root -->
<a href="../side2.html">Side 2</a> <!-- Relativ -->
<a href="/ekstra/side3.html">Side 3</a> <!-- Root -->
<img src="../img/bilde.jpg"> <!-- Relativ -->
```

## Absolutte filstier
Man kan også lenke til filer gjennom absolutte verdier, det vil si verdier som ikke endrer seg dersom prosjektet endrer seg. <mark style="background: #FFB86CA6;">Dette er sett på som dårlig praksis og bør unngås.</mark> 

```html
<img src="C:\Users\user\Desktop\Min-Nettside\img\bilde.jpg">
```

Man kan også lenke til absolutte eksterne verdier, som for eksempel andre nettsteder, dette er mer vanlig.

```html
<a href="https://google.com">Google</a>
<img src="https://example.com/example.jpg">
```