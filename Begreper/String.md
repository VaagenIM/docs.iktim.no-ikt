---
title: String
aliases: [String,Streng]
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - Definisjon
created: 2022-08-16 11:01:11
updated: 2022-08-16 11:01:11
---
# String
Betegnelse for tekst.

## String literaler
Symboler som definerer start eller slutt på en streng
```python
`String`
"String"
"""String"""
```

### Escaped characters
Noen bokstaver har flere betydninger, eller flere funksjoner. `\` tegnet sin funksjon er å forlate funksjonen til tegnet foran, for å få tekstverdien til symbolet. Lettere å forstå med et eksempel:

```python
print('I can't type the ' character')
print('I Couldn\'t type the \' character')
```

Siden `\` tegnet har en slik funksjon må man derfor escape selve `\` symbolet for å bruke den.

```python
print('\\')  # \
print('\\\\')  # \\
```

Alternativt så kan `raw strings` benyttes. I Python setter man en `r` foran tekstliteralen:

```python
print(r'\\\\') # \\\\
```

## Template literaler
Strenger som kan innhente flere verdier, for eksempel variabler. I Python begynner man en template literal på samme måte som en streng, men med en `f` karakter foran:

```python
navn = 'Bob'
template = f'Hei {navn}'
print(template)
#  Hei Bob
```

## Unicode / ASCII
En annen funksjon til `\` karakteren er Unicode karakterer eller ulike escape sekvenser. Et eksempel på en escape sekvens er tegnet som definerer starten av en ny linje; `\n`. Denne er som regel usynlig i programvare, men når man programmerer så må denne spseifiseres manuelt.

```python
print('Hello\nWorld!\n\nHow are you?')
# Hello
# World
#
# How are you?
```

Emojier er også en unicode. `\U0001f600` er for eksempel koden til 😁 symbolet.

```python
print('\U0001f600')
# 😁
```

## Les mer
- 
- https://en.wikipedia.org/wiki/ASCII