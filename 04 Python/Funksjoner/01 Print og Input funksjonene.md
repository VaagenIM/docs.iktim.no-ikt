---
title: 01 Print og Input funksjonene
aliases: [Print og Input funksjonene,]
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - Python
created: 2022-04-09 02:00:00
updated: 2022-08-13 20:25:22
---
# Print og Input funksjonene
`print()` og `input()` er to [[Funksjon|basisfunksjoner]] som brukes mye i konsollen til å behandle tekst. Den ene, `print()` bruker tekst som [[Utdata|utdata]], mens `input()` bruker tekst som [[Inndata]].

## Funksjonen `print(string="")`
`print(string="")` - når parantesene har innhold i seg (i dette tilfelle en [[String|string]]), så kan man sende argumenter (ofte beskrevet som [[Argumenter|args*]]) til funksjonen som skal kjøre. Det finnes ingen begrensninger for hva vi kan sende til en funksjon, eller hva en funksjon kan ta imot, men `print()` tar bare imot en [[String|string]]; altså tekst. I de fleste programmeringsspråk krever man en form for hermetegn eller apostrof for å adskille tekst fra kode. Dette er fordi tegnet for mellomrom ( ) brukes av datamaskinen til å adskille [[Syntaks|syntakser]] eller annen kode. Når teksten er omringet av hermetegn/apostrofer, så vet maskinen at mellomrommene og spesialtegnene skal behandles som tekst.

##### Eksempel
```python
print("Hei Verden") 	# Vil sende teksten 'Hei Verden' til print
print('Hei Verden')		# Vil sende teksten 'Hei Verden' til print
print("""Hei Verden""") # Vil sende teksten 'Hei Verden' til print
print(Hei Verden) 		# Syntaksfeil, Hei Verden er ikke tekst, og er derfor ikke definert

tekst = "Hei Verden"	# Vi definerer navnet tekst til å inneholde teksten 'Hei Verden' og lagre i RAM.
print(tekst) 			# Vil sende innholdet til navnet tekst, som er 'Hei Verden', til print.
```

## Funksjonen `input(text="")`
`input(text="")` - argumentene som input funksjonen tar, er tekst som vil vises før inndata tar sted. Teksten er valgfri. Input funksjonen legger ett stopp i kjøringen av koden, helt til brukeren av koden trykker enter. Bruker får også tilgang til å skrive noe i konsollvinduet. Funksjonen returnerer en tekst, som inneholder tekstinformasjon om hva bruker taster inn. Denne informasjonen kan lagres i [[Variabel|variabler]] og brukes i andre funksjoner.

##### Eksempel
```python
input()						# Programmet venter til bruker skriver og trykker enter, før den går videre.
input("Hva heter du? ")		# Konsollen vil skrive Hva heter du? , deretter kan bruker taste inn et svar.

navn = input("Hva heter du? ")	# Her lagrer vi svaret som bruker skriver, i en variabel med navn 'navn'

# Man kan bruke input på mange måter, her er et eksempel!
sjekk = input("Er navnet ditt " + navn + "? (Svar j/n): ")
if sjekk == "j":
	print("Bra!")
else:
	print("Prøv igjen!")
	
# Chatrobot eksempel
print("Prøv å si 'hei' eller 'hade'")	# Instrukser til bruker er fint å ha!
while True:								# Denne koden kjører uendelig til man trykker X
	tekst = input()						# Sjekk hva bruker sier
	if tekst == "hei":
		print("Hei!")					# Hvis bruker sier "hei", si Hei! tilbake.
	if tekst == "hade":
		print("Hade!")					# Hvis bruker sier hade, si Hade! tilbake.
```

## Legge sammen tekst
Python har en matematisk tilnærming når det kommer til tekst, og vi kan derfor anvende basis matteformler til tekst, som betyr at dersom man vil legge noe ekstra til teksten, så kan vi plusse. Hvis vi ønsker å gjenta tekst et gitt antall ganger, så kan vi gange. 

Her blir det viktig å adskille hva som er tekst, og hva som er tall, når vi manipulerer tekst med matte. Python klarer ikke tolke forskjell mellom tekst og tall, noe som kan gjøre det enda mer forvirrende.

Vi kan også legge sammen innhold fra variabler, enten om det legges til med plussing, eller med en in-line variabel funksjon, se eksempel.

##### Eksempel
```python
print("Hei " + "Verden")	# Legg merke til mellomrommet i "Hei ". Her blir resultatet "Hei Verden"
print("Hei" * 5)			# Her vil vi få teksten "HeiHeiHeiHeiHei"	

print(15 + 5)				# Printer 20
print('15' + '5')			# Printer 155
print(int('15') + int('5'))	# Konverterer tekst til tall (integer) før den adderer, og printer derfor 20
print(str(15) + str(5))		# Konverterer hele tall til tekst før den adderer, printer derfor 155

print('15' + 5)				# Syntaksfeil, kan ikke blande tekst og tall.
print('15' + str(5))		# Konverterer tallet til tekst, nå vil den printe 155

navn = "Jens Stoltenberg"	# Definerer variabel navn med tekstinnhold, "Jens Stoltenberg"
print('Hei ' + navn)		# Vil legge sammen 'Hei ' og innhold til variabel navn, "Hei Jens Stoltenberg"

fornavn = "Jens"
etternavn = "Stoltenberg"
print("Hei " + fornavn + " " + etternavn + ".")	# Lite oversikt, men printer Hei Jens Stoltenberg.
print(f"Hei {fornavn} {etternavn}.")			# Legg merke til 'f' før teksten starter.
```

## Når man vil printe apostrof, hermetegn eller andre spesialtegn
Fordi noen tegn blir reservert av maskinen til å angi om et tegn er tekst eller tall, hex som alltid begynner med 0x00, eller om man rett og slett vil bruke " eller ' i en tekst, så må vi bruke et spesialtegn for å fortelle maskinen at vi vil sette inn et spesialtegn. Man kan også bruke apostrofer eller hermetegn om en annen.

Tegnet som brukes for å definere at neste tegn er et spesialtegn er backslashen `\`. Og ja - dersom du vil bruke en backslash i teksten din, så må du skrive `\\` , siden backslash selv er et spesialtegn. 

Dette er også grunnen til at vi ikke bruker mellomrom i filnavn eller mappenavn, da `/Skole Oppgaver/Min Oppgave Som Jeg Leverte!!!.docx` blir til `/Skole\ Oppgaver/Min\ Oppgave\ Som\ Jeg\ Leverte\!\!\!.docx` Noen ganger må vi også oppgi ASCII koden for mellomrom, som er 020: `/Skole$020Oppgaver/Min$020Oppgave$020Som$020Jeg$020Leverte!!!.docx` - dette kan føre til at programmet ikke kjører korrekt, ettersom vi behandler tolkning av mellomrom annerledes avhengig av operativsystem.

##### Eksempel
```python
print("Hei verden koden: print("Hei Verden")") 		# Syntaksfeil, teksten bare slutter midt i.
print("Hei verden koden: print(\"Hei Verden\")")	# Fungerer
print('Hei verden koden: print("Hei Verden")')		# Fungerer, siden teksten defineres av ', ikke "
print("""Her kan jeg skrive " ' i teksten""")		# Fungerer, siden teksten defineres av """

print("Adskill spesialtegn med \ symbolet!")		# Printer med en backslash " \ "
print("Adskill spesialtegn med \\ symbolet!")		# Printer, men kun med en backslash " \ "
print("Adskill spesialtegn med \\\ symbolet!")		# Printer, men kun med to backslash " \\ "
print("Adskill spesialtegn med \\\\ symbolet!")		# Printer, men kun med to backslash " \\ "
```