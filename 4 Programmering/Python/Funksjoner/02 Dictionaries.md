---
title: 02 Dictionaries
aliases: [Dictionaries,]
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - Python
created: 2022-04-09 02:00:00
updated: 2022-08-13 20:26:50
---
# Dictionaries
Kommer fra det flotte engelske ordet for ordbok. Det er på mange måter likt som [[03 Tuples og lister]] - men det skiller seg ut ved at det bruker nøkler. Det er et veldig universelt format på lik linje som [[JSON]] - et skriftlig dataformat typ-excel fil, men for datamaskiner.

For å lage en dictionary så bruker man ikke `[]` men `{}`, der vi definerer alt med en nøkkel. Merk at man kan likevel bruke tuples eller flere dictionaries inne i en dictionary dersom man ønsker mange lag.

Slik lager man en dictionary:
```python
format = {'key':'verdi',
		  'key2':'verdi2'
		  }
		 
print(format['key']) # Printer 'verdi'
		 
# For eksempel:
Ole = { 'fornavn': "Ole",
		'etternavn': "Gregor",
		'alder': 28,
		'adresse': "Berggata 22"
		}
		
print(Ole['fornavn'] + " " + Ole['Etternavn']) # Printer 'Ole Gregor'
```

Fordelen med dette er at vi får struktur, og det blir mer lesbart - men det kan og bli litt mye!

Her er et uoversiktelig eksempel på bruksområde i slike datasett:
```python
folk = {'menn':[
				{'fornavn': 'Ole',
				 'etternavn': 'Gregor'
				},
				{'fornavn': 'Jens',
				 'etternavn': 'Stoltenberg'
				}],
		 'kvinner':[
				{'fornavn': 'Kari',
				 'etternavn': 'Traa'},
				{'fornavn': 'Julie',
				 'etternavn': 'Lise'
				 }]
		}
		
for menn in folk['menn']:
	print(f"{menn['fornavn']} {menn['etternavn']} er med i løpet.")
	print(menn['fornavn'])
	
for verdi in folk['kvinner']:
	print(f"{verdi['fornavn']} {verdi['etternavn']} er med i løpet.")
	print(verdi['fornavn'])
```

Strukturen her er at vi har en dictionary, som består av 2 nøkler; menn og kvinner. Verdiene til nøklene er en liste. Listen inneholder en dictionary som har nøkler for de ulike mennene / kvinnene. Her er det igjen, bare brutt ned i ulike komponenter. Resultatet er HELT likt:

```python
ole = {'fornavn': 'Ole',
	   'etternavn': 'Gregor'}
	   
jens = {'fornavn': 'Jens',
	    'etternavn': 'Stoltenberg'}
	   
kari = {'fornavn': 'Kari',
	    'etternavn': 'Traa'}
	   
julie = {'fornavn': 'Julie',
	     'etternavn': 'Lise'}
	   
menn = [ole, jens]
kvinner = [kari, julie]

folk = {'menn': menn
		'kvinner': kvinner}
		
for menn in folk['menn']:
	print(f"{menn['fornavn']} {menn['etternavn']} er med i løpet.")
	print(menn['fornavn'])
	
for verdi in folk['kvinner']:
	print(f"{verdi['fornavn']} {verdi['etternavn']} er med i løpet.")
	print(verdi['fornavn'])
```

Man kan også legge til ting i en dictionary, eller endre dem ved å bare late som om de er variabler:
```python
Ole = { 'fornavn': "Ole",
		'etternavn': "Gregor",
		'alder': 28,
		'adresse': "Berggata 22"
		}

Ole['postnummer'] = 45 # Legger til 'postnummer':45 i dictionarien
Ole['alder'] = 29 # Endrer verdien til nøkkel 'alder'
```