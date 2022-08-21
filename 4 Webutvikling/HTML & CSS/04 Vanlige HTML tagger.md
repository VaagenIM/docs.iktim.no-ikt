---
title: 04 Vanlige, basic HTML tagger
aliases: 
  - 04 Vanlige HTML tagger
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - HTML
  - Web
created: 2022-08-21 13:51:41
updated: 2022-08-21 13:51:47
---
# 04 Vanlige, basic HTML tagger
Her er bare et fåtall av de mest vanlige HTML taggene, Google er din beste venn.

## `<p>` - paragraf
En paragraf betyr blokk av tekst, og er det man lager når man blant annet trykker `Enter` tasten i programmet Word.

```html
<body>
	<p>
		Paragraf 1: Lorem ipsum dolor sit amet, 
		consectetur adipiscing elit, sed do eiusmod 
		tempor incididunt ut labore et dolore magna aliqua.
	</p>
	<p>
		Paragraf 2: Ut enim ad minim veniam, 
		quis nostrud exercitation ullamco laboris 
		nisi ut aliquip ex ea commodo consequat.
	</p>
</body>
```

## `<h1-6>` Overskrifter
Enkelt å greit, overskrifter i synkende størrelse.

```html
<h1>Overskrift 1</h1>
<h2>Overskrift 2</h2>
<h3>Overskrift 3</h3>
<h4>Overskrift 4</h4>
<h5>Overskrift 5</h5>
<h6>Overskrift 6</h6>
```

## `<b>` og `<i>` - **fet** og _kursiv_
```html
<b>Fet (Bold) tekst</b>
<i>Kursiv (Italic) tekst</i>
```

## `<br>` - break, eller "ny linje"
Når man skriver tekst i HTML over flere linjer, så betyr ikke det automatisk at nettleseren vil tolke linjeskiftene som nye linjer. Resultatene i dette eksempelet vil vises helt likt:
```html
<body>
	<p>Linje 1. Linje2. Linje3.</p>
	<p>
		Linje 1.
		Linje 2.
		Linje 3.
	</p>
</body>
```

For å få nytt linjeskift må man manuelt definere skiftet via `<br>` taggen, eller starte en ny paragraf:

```html
<body>
	<p>
		Linje 1.<br>
		Linje 2.<br>
		Linje 3.
	</p>
</body>
```

## `<a>` Attribute, aka lenker.
Attributes er spesielle tagger som inneholder utvidet funksjonalitet. Den vanligste funksjonen heter `href`, som betyr hypertekst referanse. En referanse blir en trykkbar lenke som tar nettleseren videre til en ny hypertekstfil. For å definere innholdet i funksjonen bruker man syntaksen `<a funksjon="funksjonens innhold>"`.

Litt tungt å huske, men `<a href="lenke">tekst</a>` er taggen for å lage lenker.

```html
<body>
	<a href="https://google.com">Google</a>
	<a href="side2.html">Side 2</a>
	<a href="/">Hjem</a> <!-- / = index.html -->
</body>
```

## `<img>` - bilder
På samme måte som `<a>` krever `<img>` en funksjon på hvordan taggen skal laste inn bilde, da et bilde kan være mer enn bare piksler. Vanligvis brukes `src` funksjonen for å definere kilden til bildet.

```html
<img src="https://example.com/example.jpg">
<img src="bilde1.jpg">
```

## Kombinere tagger
Alle tagger i HTML kan kombineres, men rekkefølgen kan være viktig!

Link, som er et bilde <mark style="background: #BBFABBA6;">(Riktig)</mark> :

```html
<a href="https://google.com"><img src="bilde.jpg"></a>
```

Bilde, som inneholder en link, som ikke er synlig <mark style="background: #FF5582A6;">(Feil)</mark> :
```html
<img src="bilde.jpg"><a href="https://google.com"></a></img>
```