---
title: 03 Tuples og lister
aliases: [Tuples og lister,]
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - Python
created: 2022-04-09 02:00:00
updated: 2022-08-13 20:25:56
---
# Tuples og lister
En Tuple er en verdi som inneholder FLERE verdier, de refereres ofte som lister. Du lager en Tuple ved å ramme verdien inn i en ``[]`` blokk, verdier adskilles ved komma. Her er foreløpig en uoversiktlig oversikt over hva det er for noe.

```python
MinForsteTuple = [0, "Ole", 25]
# Inneholder verdiene: 0, "Ole", 25
```

For å behandle dataen som ligger i Tuple, så har man mange muligheter. Den 'manuelle' metoden er å referere til verdien vi ønsker ved å sette inn et `[VERDI-Indeks]` etter variabelnavnet:
```python
MinForsteTuple = [0, "Ole", 25]

print(MinForsteTuple[0]) # Printer 0
print(MinForsteTuple[1]) # Printer Ole
print(MinForsteTuple[2]) # Printer 25
```

Man kan også behandle ALL dataen som om det var samme kategori, for eksempel en liste med navn. Dette kalles på fagspråk å [[Enumerate|enumerere]] data til en stor liste, for å så [[Iterate|iterere]] seg gjennom den. I Python så har vi iterereingsfunksjonen `in` som kan brukes på flere måter, det vil bety at den sjekker alle enumererte data (Dvs. den går gjennom listen):
```python
NavnBegynnerPaaJ = ["Jens", "Julia", "Jonas", "Jan", "Jason"]

NavnetDitt = input()
if NavnetDitt in NavnBegynnerPaaJ:
	print("Ditt navn begynner på J!")
	
if NavnetDitt not in NavnBegynnerPaaJ:
	print("Ditt navn begynner IKKE på J, eller så er det skrevet feil")
```

Man kan også bryte ned dataen dersom man ønsker å finne en spesifikk verdi, ved å gi en definisjon til `in`, lettere gjort enn forklart:
```python
NavnBegynnerPaaJ = ["Jens", "Julia", "Jonas", "Jan", "Jason"]

for NAVN in NavnBegynnerPaaJ:
	print(NAVN)
	
# Printer Jens
# Printer Julia
# Printer Jonas
# Printer Jan
# Printer Jason

# Eksempel der du ser etter spesifikt navn

NavnetDitt = input("Hva er ditt navn")
for NAVN in NavnBegynnerPaaJ:
	if NavnetDitt = NAVN:
		print(f"Du har samme navn som {NAVN}!")
```

De kan også brukes litt på lik linje som [[CSV]] - som er et dataspråk som bl.a. Excel bruker til å ha en sekvens av verdier som representerer ulike "nøkler". For eksempel en CSV kan ha format: "Fornavn, Etternavn, Alder" og man plotter inn data i den strukturen; "Jens, Stoltenberg, 45, Jonas, Gahr-Støre, 55".

```python
CPU_options = [["Billigste", 	 2000, "prisjakt.no/billigste"], 		# Verdi 0
			   ["Nest billigst", 4000, "prisjakt.no/nestbilligste"], 	# Verdi 1
			   ["Nest dyrest",	 5000, "prisjakt.no/nestdyrest"], 		# Verdi 2
			   ["Dyreste",		 6000, "prisjakt.no/dyreste"]]			# Verdi 3
			   
CPU = CPU_options[1] # Velg ut Verdi 1
print(f"Du bør gå for {CPU[0]} - den koster bare {CPU[1]}kr, du finner den på {CPU[2]}")
# Du bør gå for Nest billigst - den koster bare 4000kr, du finner den på prisjakt.no/nestbilligste
```

Du kan også splitte opp verdiene i flere variabler om du ønsker å ha bedre oversikt
```python
CPU_options = [["Billigste", 	 2000, "prisjakt.no/billigste"], 		# Verdi 0
			   ["Nest billigst", 4000, "prisjakt.no/nestbilligste"], 	# Verdi 1
			   ["Nest dyrest",	 5000, "prisjakt.no/nestdyrest"], 		# Verdi 2
			   ["Dyreste",		 6000, "prisjakt.no/dyreste"]]			# Verdi 3
			   
CPU = CPU_options[1] # Velg ut Verdi 1
CPU_Navn = CPU[0]
CPU_Pris = CPU[1]
CPU_Link = CPU[2]
print(f"Du bør gå for {CPU_Navn} - den koster bare {CPU_pris}kr, du finner den på {CPU_Link}")
# Du bør gå for Nest billigst - den koster bare 4000kr, du finner den på prisjakt.no/nestbilligste
```

Dersom du ønsker bedre kontroll, så må man se på alterntivet som i Python heter [[02 Dictionaries|Dictionaries]]! Her er det samme prinsipp, men med ulike nøkler for data; altså navn. Se eget skriv.