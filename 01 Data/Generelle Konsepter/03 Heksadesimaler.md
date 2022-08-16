---
title: 03. Heksadesimaler
aliases: [Heksadesimaler,]
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - Tallsystem
created: 2022-04-09 02:00:00
updated: 2022-08-13 20:23:47
---
# Heksadesimaler
Heksadesimaler er et 16-tallsystem hvor laveste tall er 0, og høyeste tall er F (15). Også kjent som Hex.

1 siffer i det heksadesimale systemet er det samme som 4 siffer i [[02 Binærtall|binærtall]], en [[Byte]] kan derfor representeres med 2 siffer i hex.

De fleste PC-skjermer bruker 8bit farge (også referert til som 24bit), med 8 bits i de ulike fargekanalene, [[RGB|Rød, grønn og blå]]. For å representere 8 bits med heksadesimaler trenger vi kun 2 siffer for å gjengi alle verdiene mellom 0-255.

Mange redigeringsprogram bruker som standard hex fargekoder når man velger ut farger. Hex farger går fra verdien #000000 til \#FFFFFF. De to første sifrene representerer rød, de 2 to neste representerer grønn, og de to siste representerer blå. 

| Hex      | Farge |
| -------- | ----- |
| \#FF0000 | Rød   |
| \#00FF00 | Grønn |
| \#0000FF | Blå   |
| \#FFFF00 | Gul   |
| \#FF00FF | Lilla |
| \#00FFFF | Cyan  |
| \#FFFFFF | Hvit  |
| \#000000 | Svart |

## Å regne med Hex
Vi regner med heksadesimaltall på samme måte som med [[02 Binærtall|Binærtall]], hvor vi ganger verdien av posisjonen med verdien av $n$, opphøyd i posisjon, som blir summert med resten av tallene i sekvensen.[@CitationNeeded]

Formelen for hex, hvor $n$ er et tall mellom 0-15: $(n * 16^1) + (n * 16^0)$
Obs. Tall som er opphøyd i 0 vil alltid bli tallet 1 ($∞^0$ = 1)

Merk at vi bruker samme formel i [[10-Tallsystemet|10-tallsystemet]], bare der bruker vi runde tall som er lettere å forstå.

10-tallsystemet: $(n * 10^1) + (n * 10^0)$. 
Tallet 25 blir da $(2 * 10^1) + (5 * 10^0)$, bedre kjent som $(20 + 5)$


| Hex   | Steg 1                         | Steg 2                   | Steg 3        | Desimal |
| ----- | ------------------------------ | ------------------------ | ------------- | ------- |
| 0xFF  | $(15*16^1)+(15*16^0)$          | $(15*16)+(15*1)$         | $240+15$      | 255     |
| 0x4F  | $(4*16^1)+(15*16^0)$           | $(4*16)+(15*1)$          | $64+15$       | 79      |
| 0x22  | $(2*16^1)+(2*16^0)$            | $(2*16)+(2*1)$           | $32+2$        | 34      |
| 0x8DF | $(8*16^2)+(13*16^1)+(15*16^0)$ | $(8*256)+(13*16)+(15*1)$ | $2048+208+15$ | 2271    |


Fordi heksadesimaler bråker både tall og bokstaver er det vanskelig å avgjøre automatisk om heksadesimale tall bare er en [[String|streng]] av bokstaver og tall, eller om den skal tolkes som et heksadesimalt tall. Derfor er det satt i bruk en konvensjon om å skrive inn `0x` foran alle heksadesimale tall slik at maskinen ikke tolker feil.

Eksempelvis betyr FF forte fortissimo, som betyr "veldig høyt". For at maskinen skal tolke det som tall, må vi skrive `0xFF`, som blir representerer tallet 255 (eller 256, hvis vi teller med tallet 0).

## Les mer
[Hexadecimal to Decimal Converter](https://www.rapidtables.com/convert/number/hex-to-decimal.html)
[HTML Color Picker](https://www.w3schools.com/colors/colors_picker.asp)
[heksadesimalt tallsystem – Store norske leksikon](https://snl.no/heksadesimalt_tallsystem)