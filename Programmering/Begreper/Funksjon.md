---
title: Funksjon
aliases: [Funksjon,]
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - Definisjon
created: 2022-04-09 02:00:00
updated: 2022-08-21 15:20:11
---
# Funksjon
En funksjon er i sin enkleste forklaring det samme som en tradisjonell kokebok oppskrift, som i seg selv ikke er så komplisert - men dersom en funksjon kombineres med andre funksjoner blir det fort komplekst. 
Til forskjell fra en kokebok for mennesker, utføres oppskriften av [[01 Hva er en datamaskin|datamaskinen]] da den blir bedt om å 'følge oppskriften'.

I Python defineres en funksjon via `def` syntaksen, etterfulgt av `navn`, avsluttet av en parameter-parantes`():`.
Eksempel: `def MinFunksjon():`, `def JegErEnFunksjon():`
Alternativt kan funksjonen inneholde argumenter `(navn1, navn2):`: `def SummereTall(tall1, tall2):`
Eller hvis du vil gjøre det avansert: (`(*args, **kwargs):`).

Funksjonen i seg selv er innholdet som kommer etterpå - helt til man stopper med å ha [[Innrykk]].

Eksempel:
```python
# Oppskrift_Brod() tar ingen argumenter, printer en oppskrift på Brød
def Oppskrift_Brod():
	print("2 liter hvetemel")
	print("50g sukker")
	print("1 liter rugmel")
	print("1 pakke gjær")
	print("0.5 liter varm melk")
	print("Rør godt")
	
# Oppskrift_Kake() tar ingen argumenter, printer en oppskrift på Kake
def Oppskrift_Kake():
	print("1 liter hvetemel")
	print("400g sukker")
	print("100g 70% kakao")
	print("Rør godt, 200C i ovnen i 15 min")
	

# Gi maskinen en 'oppskrift'!
print("Her er oppskriften til BRØD!")
Oppskrift_Brod()

print("Her er oppskrift på kake heller, men jeg skriver den TO ganger!!")
Oppskrift_Kake()
Oppskrift_Kake()
```

## Funksjoner med verdier
Dette er en generelt dum funksjon - den tar et sett instrukser og gjennomfører den. Fordelen med programmering, er at vi kan håndtere data i våre funksjoner. Det gjør man ved å gi et parameter i funksjonen, i Python kan vi legge til hva som helst, vi bare gir det et navn! Her har jeg lagt inn navnet "porsjoner", men du kan skrive HVA du vil (så lenge det ikke allerede er definert av noe annet).

```python
def Oppskrift_Brod(porsjoner):
	liter_hvetemel 	= str(porsjoner * 2)
	liter_rugmel 	= str(porsjoner * 1)
	liter_varmmelk  = str(porsjoner * 0.5)
	gram_sukker 	= str(porsjoner * 50)
	pakke_gjaer		= str(porsjoner * 1)
	
	print(liter_hvetemel + " liter hvetemel")
	print(gram_sukker 	 + "g sukker")
	print(liter_rugmel 	 + " liter rugmel")
	print(pakke_gjaer 	 + " pakke gjær")
	print(liter_varmmelk + " liter varm melk")
	print("Rør godt!")
	
print("Her er oppskrift for 8 porsjoner av BRØD!!")
# Vi skriver inn 8 - funksjonen kaller verdien "8" for "porsjoner"
Oppskrift_Brod(8)

print("Eller bare 0.5 porsjon BRØD")
Oppskrift_Brod(0.5)
```

Slike funksjoner kan også ha standardverdier ved å legge et = etter en parameter:
```python
def Oppskrift_Brod(porsjoner=1):
	liter_hvetemel 	= str(porsjoner * 2)
	liter_rugmel 	= str(porsjoner * 1)
	liter_varmmelk  = str(porsjoner * 0.5)
	gram_sukker 	= str(porsjoner * 50)
	pakke_gjaer		= str(porsjoner * 1)
	
	print(liter_hvetemel + " liter hvetemel")
	print(gram_sukker 	 + "g sukker")
	print(liter_rugmel 	 + " liter rugmel")
	print(pakke_gjaer 	 + " pakke gjær")
	print(liter_varmmelk + " liter varm melk")
	print("Rør godt!")

print("Her er oppskriften for BRØD!")
# Ingen verdi i parantes betyr at porsjoner forblir 1
Oppskrift_Brod()

print("Her er oppskriften for 2")
# Her overstyrer vi porsjoner til å være 2
Oppskrift_Brod(porsjoner=2)
```

## return funksjonen
Det kraftigste verktøyet vi har er return, på godt norsk returnerer det en verdi som maskinen kan ta videre, dersom den vil. Lettest forklart så kan vi forvente å få lagret summen av tall, dersom vi har en funksjon som legger sammen to tall:
```python
def summer(tall1, tall2):
	verdi = tall1 + tall2
	return verdi

summer(5, 12) # Summerer tallene 5 + 12 - men ingenting skjer!
print(summer(5, 12)) # Summerer tallene 5 + 12, resultatet blir printet (17)
x = summer(5, 12) # Summerer tallene 5 + 12, resultatet blir lagret i variabel x
x = summer(x, 12) # Summerer tallene x + 12, x = 17, 17 + 12, resultatet blir lagret i variabel x
print(x) # Printer tallet 29
```

Det kan også brukes til andre praktiske ting, hvis vi ser på oppskrift eksempelet kan det for eksempel returnere hvor mange måltider du kan få:
```python
def Maaltider_Brod(porsjoner=1):
	# 1 Brød = dekker nok mat for 5 personer
	maaltider 		= porsjoner * 5
	
	return maaltider

def Maaltider_Kjott(porsjoner=1):
	# 0.4kg  kjøtdeig = dekker nok mat for 3 personer
	maaltider 		= porsjoner * 3
	
	return maaltider
	
print("Hvis vi baker 3 brød og steker 2 kjøttdeigspakker, hvor mange kan vi mate?")
maaltider_brod = Maaltider_Brod(porsjoner=3) # Returnerer 15 (5 måltider * 3 porsjoner)
maaltider_kjott = Maaltider_Kjott(porsjoner=2) # Returnerer 6 (3 måltider * 2 porsjoner)

antall = maaltider_brod + maaltider_kjott
print(f"Vi kan i verste fall mate {antall} personer!")

```

## Avansert bruk av return
Hva en funksjon kan returnere er HELT abstrakt, bare fantasien setter grenser! Det mest nyttige formatet er [[JSON]]. Som i tidligere eksempel, returnerer Oppskrift_Brod et datasett av `ingredienser` med `tekst` til hver ingrediens og en `verdi`. I tillegg er det et sett av `instrukser`:
```python
# Oppskrift_Brod(porsjoner=n):
# Generer en JSON i vårt Oppskrift format (Oppskrift['ingredienser'] og ['instrukser'])
def Oppskrift_Brod(porsjoner=1):
	JSON = { 
		'ingredienser':[
		{
			'tekst': "Liter hvetemel",
			'verdi': porsjoner * 2
		},
		{
			'tekst': "Liter rugmel",
			'verdi': porsjoner * 1
		},
		{
			'tekst': "Liter Varm melk",
			'verdi': porsjoner * 0.5
		},
		{
			'tekst': "Gram sukker",
			'verdi': porsjoner * 50
		},
		{
			'tekst': "Pakker med gjær",
			'verdi': porsjoner * 1
		}
		],
		'instrukser': [
			'Visp alt det flytende',
			'Rør inn det tørre',
			'Stapp det inn i ovnen!'
		]
   }
	return JSON

# PrintOppskrift(): 
# Tolker vårt JSON oppskriftformat og printer ut
def PrintOppskrift(oppskrift):
	for ingrediens in oppskrift['ingredienser']:
		# Eksempel: Du trenger 2500 Gram sukker
		print(f"Du trenger {ingrediens['verdi']} {ingrediens['tekst']}")
	print("Slik gjør du:")
	for instruks in oppskrift['instrukser']:
		print(instruks)

# Test koden:
print("Oppskriften for 1 porsjon brød:")
PrintOppskrift(Oppskrift_Brod())

print(" ") # Mellomrom

print("Her er samme oppskrift, men for 50 porsjoner!!!")
x = Oppskrift_Brod(porsjoner=50)
PrintOppskrift(x)
```

Dette blir da generert av maskinen når du kjører:
```sh
# Oppskriften for 1 porsjon brød:
# Du trenger 2 Liter hvetemel
# Du trenger 1 Liter rugmel
# Du trenger 0.5 Liter Varm melk
# Du trenger 50 Gram sukker
# Du trenger 1 Pakker med gjær
# Slik gjør du:
# Visp alt det flytende
# Rør inn det tørre
# Stapp det inn i ovnen!
# 
# Her er samme oppskrift, men for 50 porsjoner!!!
# Du trenger 100 Liter hvetemel
# Du trenger 50 Liter rugmel
# Du trenger 25.0 Liter Varm melk
# Du trenger 2500 Gram sukker
# Du trenger 50 Pakker med gjær
# Slik gjør du:
# Visp alt det flytende
# Rør inn det tørre
# Stapp det inn i ovnen!
```