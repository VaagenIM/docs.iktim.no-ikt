---
title: 01. Tallsystemer
aliases: [Tallsystemer,]
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - Tallsystem
created: 2022-04-09 02:00:00
updated: 2022-08-13 20:00:00
---
# Tallsystemer
Det vanligste tallsystemet som er brukt hos mennesker er [[10-Tallsystemet|10-tallsystemet]], som fungerer flott til de vanligste matematiske utfordringer hvor vi regner med tall. Dette er ikke tilfelle for datamaskiner, som representerer data i form av elektroniske signaler; av eller på.

Når en elektronisk krets bare har to utfall, som heter bits (1 eller 0), er det mer logisk å bruke to-tallsystemet [[02 Binærtall|Binærtall]]. Ofte er 8 bits satt sammen til 1 [[Byte]], eller delt inn i 4-bits ([[Nibble]])

Et kompakt tallsystem som fungerer bra og er mye brukt i kombinasjon med binærtall er [[03 Heksadesimaler|Heksadesimaler]], eller et 16-tallsystem, med tallene 0-F.

## Tabell av tall, fra 0-255
| 10-tallsystem | Heksadesimal | Binærtall |
| ------------- | ------------ | --------- |
| 0             | 0x0          | 0000      |
| 1             | 0x1          | 0001      |
| 2             | 0x2          | 0010      |
| 3             | 0x3          | 0011      |
| 4             | 0x4          | 0100      |
| 5             | 0x5          | 0101      |
| 6             | 0x6          | 0110      |
| 7             | 0x7          | 0111      |
| 8             | 0x8          | 1000      |
| 9             | 0x9          | 1001      |
| 10            | 0xA          | 1010      |
| 11            | 0xB          | 1011      |
| 12            | 0xC          | 1100      |
| 13            | 0xD          | 1101      |
| 14            | 0xE          | 1110      |
| 15            | 0xF          | 1111      |
| 16            | 0x10         | 0001 0000 |
| 17            | 0x11         | 0001 0001 |
| ...           | ...          | ...       |
| 31            | 0x1F         | 0001 1111 |
| 32            | 0x20         | 0010 0000 |
| 255           | 0xFF         | 1111 1111 |