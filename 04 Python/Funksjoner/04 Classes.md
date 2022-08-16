---
title: 04 Classes
aliases: [Class,Classes]
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - Python
  - OOP
created: 2022-07-06 02:00:00
updated: 2022-08-13 20:25:59
---
# Classes
Class er en standardfunksjon i [[OOP|Objekt-orientert programmering]] (OOP)

**Hvorfor classes?**
- Det gjør kode mer lesbart
- Det samler relevant data i ett objekt
- Det er lett å utvide i eksisterende kode

## Hva er en class?
En class er et python objekt som inneholder et sett av egenskaper og metoder som kan forenkle deler av en kode ved å redefinere verdier i en slags blåkopi.

## Eksempel, uten class
Et eksempel kan være konseptet biler: vi vet de har hjul, dører, ratt, seter. I [[Funksjonell Programmering]] så kan man for eksempel definere en bil slik:

```python
car_doors = 4
car_wheels = 4
car_seats = 5
car_steering_wheels = 1
car_name = "Civic"
car_manufacturer = "Honda" 
car_year = 2022

print(f'{car_manufacturer} {car_name} from {car_year}')
# Honda Civic from 2022
```

Her vil vi sitte igjen med mange [[Variabel|variabler]] (individuelle objekter) som kan brukes i et program som omhandler biler, men verdiene brukes individuelt.

## Eksempel, med class
Bruker vi en class kan vi heller definere hva en bil er, og derav definere hva verdiene skal kunne brukes til. I eksempelet vil det brukes en `@dataclass` [[Python Decorator|dekoratør]], som forenkler syntaksen til å generere en class.

```python
from dataclasses import dataclass  
  
@dataclass
class Car:
	name: str
	manufacturer: str
	year: int = 2022 # standardverdi
	wheels: int = 4 
	doors: int = 4
	seats: int = 5

honda = Car('Civic', 'Honda', year=2021)
print(f'{honda.manufacturer} {honda.name} from {honda.year}')
# Honda Civic from 2021

tesla = Car('Model 3', 'Tesla')
print(f'{tesla.manufacturer} {tesla.name} from {tesla.year}')
# Tesla Model 3 from 2022
```

Funksjonellt sett er koden helt lik, men likevel forskjellig med tanke på lesbarhet.

## Funksjoner i klasser
En ting som gjør klasser mer unik er evnen til å definere [[Getters og Setters]]; en metode å hente (eller lagre) informasjon på. Et eksempel på en innebygd getters er `__str__(self)` funksjonen. `__str__(self)` definerer hvordan objektet vil se ut i tekst.

Dersom vi tar eksempelet over og prøver å printe objektet, vil vi få følgende resultat:
```python
tesla = Car('Model 3', 'Tesla')
print(tesla)
# Car(name='Model 3', manufacturer='Tesla', year=2022, wheels=4, doors=4, seats=5)
```

Dersom vi overstyrer `__str__(self)` i klassen, kan vi omdefinere hvordan objektet konverteres til tekst:
```python
from dataclasses import dataclass  
  
@dataclass  
class Car:  
   name: str  
   manufacturer: str  
   year: int = 2022 # standardverdi  
   wheels: int = 4  
   doors: int = 4  
   seats: int = 5  
  
   def __str__(self):  
      return f'{self.manufacturer} {self.name} from {self.year}'  
  
tesla = Car('Model 3', 'Tesla')  
print(tesla)
# Tesla Model 3 from 2022
```


Vi kan også bruke noe som heter `@property` dekoratører, som definerer en metode å hente informasjon på, for eksempel en kode for å hente hele navnet til bilen:
```python
@dataclass
class Car:
	...

	@property
	def fullname(self):
		return f'{self.manufacturer} {self.name}'

tesla = Car('Model 3', 'Tesla')  
print(tesla.fullname)
# Tesla Model 3
```

Eller finne ut hvor mange år gammel bilen er:
```python
from datetime import date

@dataclass
class Car:
	...

	@property
	def age(self):
		return date.today().year - self.year

tesla = Car('Model 3', 'Tesla', year=2020)  
print(tesla.age)
# 2
```


Eller til og med legge til egne funksjoner:
```python
import random

@dataclass
class Car:
	...

	def honk(self):
		honks = ['Tut tut!', 'HONK!', 'BEEP BEEP!']
		print(random.choice(honks))

tesla = Car('Model 3', 'Tesla')
tesla.honk()
tesla.honk()
tesla.honk()
tesla.honk()
# HONK!
# Tut tut!
# BEEP BEEP!
# BEEP BEEP!
```

## Komplett eksempel
```python
from dataclasses import dataclass  
from datetime import date  
import random  
  
@dataclass  
class Car:  
    name: str  
    manufacturer: str  
    year: int = 2022  # standardverdi  
    wheels: int = 4  
    doors: int = 4  
    seats: int = 5  
  
    def __str__(self):  
        return f'{self.manufacturer} {self.name} from {self.year}'  
  
    @property  
    def fullname(self):  
        return f'{self.manufacturer} {self.name}'  

    @property  
    def age(self):  
        return date.today().year - self.year
  
    def honk(self):  
        honks = ['Tut tut!', 'HONK!', 'BEEP BEEP!']  
        print(random.choice(honks))
```

## Eksempel, kredittkort:
```python
from dataclasses import dataclass
from datetime import datetime, date

@dataclass
class CreditCard:
	number: int
	exp_month: int
	exp_year: int
	card_holder: str

	@property
	def exp_date(self):
		exp = f'{self.exp_year}-{self.exp_month}'
		return datetime.strptime(exp,"%Y-%m").date()

	@property
	def isValid(self) -> bool:
		return self.exp_date > date.today()


def Pay(Price: float, Card: CreditCard):
	if Card.isValid:
		print(f'Payment of {Price},- was succesful')
	else:
		print(f'Sorry {Card.card_holder}, could not complete the transaction. Reason: Expired Card')

cc1 = CreditCard(123456789, 12, 2048, 'Jens')
cc2 = CreditCard(123456789, 12, 1948, 'Bob')

Pay(1500, cc1)
Pay(1500, cc2)
# Payment of 1500,- was succesful
# Sorry Bob, could not complete the transaction. Reason: Expired Card
```

## Les mer
[Python Classes](https://www.w3schools.com/python/python_classes.asp)
[Python @property: How to Use it and Why? - Programiz](https://www.programiz.com/python-programming/property)