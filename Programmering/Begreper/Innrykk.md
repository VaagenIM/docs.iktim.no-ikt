---
title: Innrykk
aliases: [Innrykk,]
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - Definisjon
created: 2022-04-09 02:00:00
updated: 2022-08-21 15:09:33
---
# Innrykk
Innrykk er mellomrommet fra helt til venstre til der teksten starter. Python er VELDIG strenge når det gjelder innrykk.

```python
def funksjon():
	print("Jeg er innrykket, og er del av funksjonen")
print("Jeg er ikke en del av funksjonen - fordi jeg mangler innrykk")

if x == 1:
	print("Jeg printer hvis x er 1")
print("Jeg printer uansett")
```

Du kombinere innrykk med `continue`, `break` eller `return` funksjonene til feilhåndtering, lettest å forstå i et eksempel:

```python
def Valg():
	print("Velg 1 for Høyre, 2 for Venstre, 3 for Midten")
	svar = input("[1/2/3]: ")
	
	if svar == "1":
		return "Høyre"
	if svar == "2":
		return "Venstre"
	if svar == "3":
		return "Midten"
	
	# Hvis ingen av if-statementsene er sanne, så har ikke funksjonen returnert noe enda
	# Da er mest sannsynlig svaret skrevet feil!
	print("Her har du valgt feil! Prøv igjen")
	Valg()
	
print(Valg)
```

Bruk av `break` eller `continue` er mest nyttig når vi jobber med store [[JSON]] datasett:
```python
struktur = {
	'salg':[{
				'id': 1,
				'verdi': 800,
				'kategori': 12
			},
			{
				'id': 2,
				'verdi': 1200,
				'kategori': 12
			},
			{
				'id': 3,
				'verdi': 200,
				'kategori': 17
			}]
}

def FinnForsteSalgVerdiIKategori(kategori):
	Resultat = "Ingen salg i kategori " + str(kategori)
	# Start av løkke (for x in y:)
	for verdi in struktur['salg']:
		if verdi['kategori'] == kategori:
			Resultat = verdi['verdi']
			# Bryter opp en løkke (for-løkken)
			break
	return Resultat

def SumSalgEksludertKategori(kategori):
	Sum = 0
	for verdi in struktur['salg']:
		if verdi['kategori'] == kategori:
			# Hvis kategori er lik, hopp over
			continue
		# Hvis den ikke var lik, så ble den ikke hoppet over
		# Legg derfor til verdien.
		Sum += verdi['verdi']
	return Sum

print(FinnForsteSalgVerdiIKategori(17)) # 200
print(FinnForsteSalgVerdiIKategori(12)) # 800
print(FinnForsteSalgVerdiIKategori(13)) # Ingen salg i kategori 13

print(SumSalgEksludertKategori(1)) # 2200
print(SumSalgEksludertKategori(12)) # 200
print(SumSalgEksludertKategori(17)) # 2000
```