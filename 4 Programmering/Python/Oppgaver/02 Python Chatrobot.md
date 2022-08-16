---
title: 02 Python Chatrobot
aliases: [Python Chatrobot,]
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - Python
  - Oppgave
created: 2022-04-09 02:00:00
updated: 2022-08-13 20:25:55
---
# Python Chatrobot
Ved hjelp av noen få enkle [[Funksjon|funksjoner]], så skal du lage din egen chatrobot. Omfanget velger du selv, men det er en del minimumskrav du må følge. Programmering er et språk man lærer av å utforske ting i, for å få høy måloppnåelse i denne oppgaven, må du derfor eksperimentere med funksjonene du velger å gi din chatrobot.

## Syntaxer og funksjoner
Her er en oversikt over de ulike funksjonene du trenger for å løse oppgaven:
- `print(string)` - printer ut tekst, se eget skriv på [[01 Print og Input funksjonene]]
- `input(valgfri string)` - lar bruker skrive inn tekst, se eget skriv.
- `while True:` - kjører koden uendelig mange ganger, gitt at det står på et innrykk etter funksjonen.
- `if x == y:` - tester om x er helt lik y, Eksempel: `if input() == "test":` - dersom bruker skriver "test" så vil koden kjøre videre (gitt at det står på et innrykk etter funksjonen)
- `navn = verdi` - variabler, erstatt navn med hva som helst, verdi kan også erstattes med hva som helst. Se skriv om print og input for hvordan du lagrer tekst i variabler.
- `def Funksjon(valgfri argumenter):` - Lager en funksjon (Funksjon()) som lar deg skrive navnet på funksjonen, istedenfor å skrive koden funksjonen inneholder. Se eksempel for bedre forklaring.
- `# Kommentar` - Kode som ikke kjører, kun som en kommentar til den som koder for å lettere huske hva koden gjør, eller tankene bak.
- `continue` - Brukes i en `while True:` loop til å hoppe tilbake til start, for å effektivisere koden sin ytelse på maskinen.

## Minimumskrav
Kravene er veiledende, dersom du føler du har en løsning som er bedre enn hva som er nevnt, så kjører du heller på med det. Eksempel kan være å ikke bruke konsollvindu, men heller et grafisk grensesnitt.
- Chatroboten må ha kommandoer i en `while True:` loop, 
- Chatroboten skal hjelpe bruker med å fortelle hvilke kommandoer som kan brukes, enten i start av program eller ved en "hjelp" kommando.
- Minst en av kommandoene skal kjøre en egenlagt funksjon
- Du skal bruke variabler i minst en av funksjonene
- Bruk kommentar funksjonen til å forklare hva koden gjør, i Python er kommentarer gitt etter et # symbol.

## Eksempel chatrobot
Husk at Python kode kjøres fra linje 1 og nedover, men dersom kode er i innrykk, så vil det bare kjøre under gitte omstendigheter. `def` funksjoner vil kun kjøre når de blir referert til senere (funksjoner), `while STATEMENT:` vil bare kjøre dersom "STATEMENT" returnerer sant (kan være `while True:`).

Litt vanskelig å forklare, men det er ofte lettere gjort enn sagt.
```python
# Personalisering av roboten
print("Hei, jeg er en Chatrobot!")
print("Hva heter du?")

# Spør om navn og lagre den i variabel: navn
navn = input("Navnet ditt: ")
print(f"Hyggelig å treffe deg {navn}")

# Start Chatrobot med å introdusere kommandoene
print("Mine funksjoner er ?navn ?hjelp")

# while True: loop sørger for at koden kjører uendelig lenge, helt til vi trykker X 
# eller bruker en "break" funksjon, men det er ikke nødvendig her.
while True:
	x = input()	# Vent til bruker skriver inn en kommando, lagre det i "x" midlertidig
	if x == "?navn": # Hvis bruker skriver "?navn", kjør koden
		print(f"Ja jeg husker navnet ditt, {navn}")
		
		# Hvis bruker skrev inn ?navn, så er det ikke vits å sjekke om bruker skrev ?hjelp
		# fordi vi vet at det er umulig. Hopp heller tilbake til start.
		continue 
		
	if x == "hallo":
		print("hei")
		
	if x == "?hjelp": # Hvis bruker skriver inn "?hjelp", kjør koden
		print("Mine funksjoner er ?navn, ?hjelp")
		continue
```

## Eksempel, med funksjon
For mer info om hvordan funksjoner virker, se [[Funksjon]]
```python
def matte_pluss():
	# Be bruker skrive inn to tall som skal plusses
	print("Skriv inn dine 2 tall!")
	tall1 = input("Tall 1: ")
	tall2 = input("Tall 2: ")
	
	# Konverter tallene som er skrevet i tekst, til tall som er tall.
	svar = int(tall1) + int(tall2)
	
	# Konverter svar tilbake til tekst
	svar_tekst = str(svar) 
	
	# Print ut svaret
	print(f"{tall1} + {tall2} ble {svar_tekst}")
	
	# Returner svar - dette gjør at man kan bruke matte_pluss() som et tall, se neste eksempel
	return svar
	
print("Prøv min nye funksjon, ?pluss")
while True:
	x = input()
	if x == "?pluss":
		print(matte_pluss())
```

## Return funksjonen
`return` er et veldig kraftig verktøy, og det er det som gjør funksjoner nyttige. Det er ikke noe dere trenger å fokusere på i oppgaven, men det er uansett greit å vite hva den gjør. Den tar egentlig å avslutter funksjonen, og sender tilbake informasjon, hva den sender tilbake er helt valgfritt, men som regel er det noe du ønsker å få utav funksjonen. I eksempelet over, så er det summen av 2 tall vi er interessert i.

Eksempel:
```python
# UTEN return
matte = 15 + 5
print(matte) # Returnerer 20
```

```python
# MED return
def matte(tall1, tall2):
	svar = tall1 + tall2
	return svar # Returnerer summen av tall1 og tall2
# Merk at det bare er tekst i innrykk som er en del av funksjonen
print(matte(15, 5)) 
# Printer 20


# Eksempel 2

# mattetekst(tall1, tall2) tar to tall, plusser dem sammen, og returnerer en forklaring på formelen
def mattetekst(tall1, tall2):
	svar = tall1 + tall2
	
	# Konverter til tekst
	tall1_tekst = str(tall1)
	tall2_tekst = str(tall2)
	svar_tekst = str(svar)
	
	tekst = f"Jeg tar {tall1_tekst}, adderer den sammen med {tall2_tekst}, og da får vi {svar_tekst}!"
	return tekst
	
print(mattetekst(15, 5))
# Printer Jeg tar tall 15, adderer den sammen med 5, og da får vi 20!
```