---
title: 05 Enum, Identifisering
aliases: [Enum, Identifisering,]
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - Python
  - OOP
created: 2022-07-08 02:00:00
updated: 2022-08-13 20:26:07
---
# 05 Enum, Identifisering
En enum, eller enumerated type, er en verdi som identifiserer [[Constant|konstante]] verdier. I programmering møter man ofte situasjoner der man må behandle ulike egenskaper individuelt.

Et eksempel er ulike typer betalingsordninger; Visa, American Express, Mastercard, Discover. osv. har alle egne protokoller for å behandle betaling som må behandles ulikt.

## Eksempel, uten Enum
I Python bruker man ofte store bokstaver for å definere konstanter. Hvordan man velger å definere ulike verdier er opp til en selv, men konvensjonen anbefaler å bruke en [[04 Classes|klasse]] med enumererte verdier.

Her er likevel noen eksempler på hvordan man kan skille av betalingstypene:

```python
TYPE_VISA = 1
TYPE_AMEX = 2
TYPE_MASTERCARD = 3
TYPE_DISCOVER = 4

def Pay(Card):
	if Card == TYPE_VISA:
		raise NotImplementedError
	if Card == TYPE_AMEX:
		raise NotImplementedError
	if Card == TYPE_MASTERCARD:
		raise NotImplementedError
	if Card == TYPE_DISCOVER:
		raise NotImplementedError

MittKort = TYPE_VISA
Pay(MittKort)
```

Eller via tekst;
```python
def Pay(Card):
	if Card == "VISA":
		raise NotImplementedError
	if Card == "AMEX":
		raise NotImplementedError
	if Card == "MASTERCARD":
		raise NotImplementedError
	if Card == "DISCOVER":
		raise NotImplementedError

MittKort = "VISA"
Pay(MittKort)
```

> [!info] Obs
> Dette er per definisjon ikke feil, og får jobben gjort.
> Det betyr likevel at det ikke finnes en bedre måte å gjøre det på, som både er mer lesbar og mer skalerbar.


## Enum og Auto
I forrige kapittel lærte vi om [[04 Classes|Classes]]. Den største fordelen med Classes er at de kan brukes om igjen i flere deler av et prosjekt, mens konstante verdier må ofte defineres på ny avhengig av hvilken modul man arbeider med. Det kan bety at man må endre kode flere steder dersom man må endre på konstante verdier.

Ved å heller opprette en Class som inneholder våre konstanter via `Enum` modulen, kan vi definere en modulær klasse som inneholder konstantene. Denne kan deles via flere moduler og skaleres enklere og er ofte lettere å forstå enn løse konstante verdier i et dokument.

Her er et eksempel som forvandler en konstant verdi, `TYPE_VISA`, til en egen klasse; `CARD_TYPE.Visa`, som er mer selvforklarende og modulær:
```python
from enum import Enum, auto  
  
class CARD_TYPE(Enum):  
   Visa = auto()  
   American_Express = auto()  
   Mastercard = auto()  
   Discover = auto()  
  
def Pay(Card):  
   if Card == CARD_TYPE.Visa:  
      raise NotImplementedError  
   if Card == CARD_TYPE.American_Express:  
      raise NotImplementedError  
   if Card == CARD_TYPE.Mastercard:  
      raise NotImplementedError  
   if Card == CARD_TYPE.Discover:  
      raise NotImplementedError  
  
MittKort = CARD_TYPE.Visa
Pay(MittKort)
```

> [!note] `auto()` funksjonen
> `auto()` funksjonen i `enum` modulen er også med på å automatisk angi en verdi til konstantene for simpelhetens skyld.
>
> Vi kan likevel definere konstanten selv med egne verdier, dersom man behøver det som her:
> ```python
> class CARD_TYPE(Enum):  
>	   Visa = 1
>	   American_Express = 2
>	   Mastercard = "Mastercard"
>	   Discover = "Discover"
> ```
> Resultatet blir det samme, men muligheten er der.

