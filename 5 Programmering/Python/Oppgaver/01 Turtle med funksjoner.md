---
title: 01 Turtle med funksjoner
aliases: [Turtle med funksjoner,]
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - Python
created: 2022-04-09 02:00:00
updated: 2022-08-13 20:25:23
---
# Turtle med funksjoner
Vi har sett på Python pakken [[Turtle]], et forenklet underspråk laget i [[Python]]. En skilpadde som tar fysisk logiske kommandoer som forward, right, left, backward. Vi installerer Turtle ved å åpne [[Konsollvindu]], på mac heter dette [[Terminal]], Windows [[Kommandolinjeverktøy]] (CMD). Der skriver vi koden for "Python Install Package", som er `pip install turtle`. 
Et helt enkelt oppsett av Turtle skrives som følger:

```python
from turtle import *

speed(1)
shape("turtle")

forward(100)
right(90)
forward(100)
```

Her vil det tegnes en 90 graders vinkel på skjermen. Man kan endre parametrene til å tegne nesten det man vil, som om man brukte en gammeldags Etch-a-sketch. Men selv enkle programmer kan fort bli innviklete, med mindre man forenkler prosessene man ønsker å oppnå. Møt derfor funksjoner, der du kan forhåndsprogrammere sekvenser.

## Oppgave
Du skal bruke Turtle til å tegne ditt eget navn, eller noen andre sitt navn, ved hjelp av [[Funksjon|funksjoner]]. Du står fritt frem om du vil bruke tid på å få skilpadden til å ta tusjen opp eller ned, farger eller lignende, men så lenge det kan se ut som ditt navn så er det fint. 

Funksjoner er rett og slett oppskrifter på hvordan maskinen skal utføre kode, og kan derfor gjøre at vi kan forhåndsprogrammere et sett med kommandoer og få det ned til en enkel kommando, som kan være nyttig dersom man vil gjøre det enkelt å oppnå et spesifikt resultat, for eksempel hvordan tegne bokstaver. Jeg skal vise et eksempel over hvordan en funksjon kan se ut, men resten må dere lage selv.

## Eksempel på funksjon, tegn firkant
Dette eksempelet har en funksjon som tar imot en parameter, navn på parameter er helt frivillig, og du kan bruke navnet i koden, som om den har informasjonen som du vil at den skal ha. Fordel er det om du bruker navn som representerer hva funksjonen trenger av informasjon, for eksempel dersom funksjonen trenger et tall, at du kaller den for tall.

```python
from turtle import *

speed(1)
shape("turtle")

# Firkant tar inn verdi tall, som er hvor stor kuben skal være
def Firkant(tall):
	for i in range(0,4):
		forward(tall)
		right(90)
		
Firkant(10) # tegner en 10px stor kube
Firkant(100) # tegner en 100px stor kube
```

## Eksempel på funskjon, tegn bokstav A
Tenk deg koden for å tegne en tekst på skjermen, du går fra å kunne skrive `"Hei jeg heter Jens"` til at det kommer opp et tegn for bokstaven H, et tegn for bokstaven e, osv. Det er ikke av tilfeldigheter at det fungerer slik, det er fordi noen har manuelt sittet å programmert det inn i operativsystemet som funksjoner. På samme måte, må du selv skrive koden for hvordan bokstaver skal bli representert. Vi skal gjøre dette noe forenklet, men i teorien skal du kunne få skilpadden til å tegne, dersom du bruker litt god tid, ved å skrive `Skriv("Jeg er en Skilpadde")`. Men vi skal gjøre det på en litt mer hacky måte. I eksempelet under viser jeg hvordan du kan lage en funksjon til å tegne bokstaven A.

```python
from turtle import *

speed(1)
shape("turtle")

def bokstavA():
	# /
	left(80)
	forward(50)
	
	# \
	right(160)
	forward(50)
	
	# Beveg skilpadde ned mot midten av A'en
	right(180)
	forward(20)
	
	# - Tegn en stripe i midten av A'en og gå tilbake
	left(80)
	forward(8)
	left(180)
	forward(8)
	
	# Gå ned til ytre høyre av bokstaven for å avslutte den
	right(80)
	forward(20)
	
	# Gå 10px fram for å gi plass til neste bokstav
	left(80)
	forward(10)
	

# Skriv AAA
bokstavA()
bokstavA()
bokstavA()
```

For å forstå hva jeg mente med å konvertere til at man kan skrive `Skriv("AAA")`, så skriver jeg eksempelet her. Det er egentlig en dårlig måte å gjøre det på, do as I say, not as I do:
```python
from turtle import *

speed(1)
shape("turtle")

def bokstavA():
	# /
	left(80)
	forward(50)
	
	# \
	right(160)
	forward(50)
	
	# Beveg skilpadde ned mot midten av A'en
	right(180)
	forward(20)
	
	# - Tegn en stripe i midten av A'en og gå tilbake
	left(80)
	forward(8)
	left(180)
	forward(8)
	
	# Gå ned til ytre høyre av bokstaven for å avslutte den
	right(80)
	forward(20)
	
	# Gå 10px fram for å gi plass til neste bokstav
	left(80)
	forward(10)
	
def Skriv(tekst):
	# Sjekk en og en bokstav
	for bokstav in tekst:
		if bokstav == "A":
			bokstavA()
			continue
		if bokstav == "a":
			bokstava()
			continue
		# Osv..
		
Skriv("AAA") # Gjør det samme som koden over, gitt at bokstavA() funksjonen finnes.
```