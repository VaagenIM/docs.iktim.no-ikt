---
title: 03. Subnetting
aliases: [Subnetting,Subnet Mask]
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - Nettverk
  - VLAN
created: 2022-04-09 02:00:00
updated: 2022-08-13 20:25:38
---
# Subnetting
Subnet definerer et område hvor det kan eksistere IP-adresser. Jo større subnet, jo flere enheter kan koble til nettverket. Den første verdien og siste verdien i et subnet forteller enhetene som er koblet til hvor de kan hente informasjon om andre enheter i nettverket automatisk, via for eksempel tjenester som [Apple sin Bonjour](https://developer.apple.com/bonjour/). 

Det betyr ikke at et nettverk med flere subnet er adskilt, men dersom de kombineres med [[04 VLAN|VLAN]] så kan det legges [[05 Brannmur|Brannmur]] mellom som gjør at subnettene oppfører seg som om de var isolerte nettverk.

Subnett blir brukt til å definere områder for enheter slik at man kan reservere IP-adresser ut ifra hvilket behov en har. Forventer en $500$ besøkende til et hotell for eksempel, så kan det være lurt å reservere nok plass slik at alle kan få en IP-adresse.

Før var det viktig for ytelsen sin del å ikke ha større subnet enn nødvendig, ettersom større subnet førte til verre ytelse i nettverket.


## Eksempel
Hvis vi tar utgangspunkt i at IP-adresser har 4 [[Oktett|Oktetter]], så er Subnet et sett av nye 4 oktetter som definerer hvor mange bits en ip-adresse kan ta av. Totalt kan et subnet bestå av 32 bits, ($4*8$).

En subnet maske av 255.255.255.0 vil ha 24 bits, og se slik ut:
$$
1111 1111 .1111 1111 .1111 1111 .0000 0000
$$

*Subnet masker tar utgangspunkt i en IP-adresse den blir gitt.*
For eksempel ip-adressen $192.168.1.1$ som har et $/24$ bits subnet kunne ha hvilket som helst tall i den fjerde oktetten. $192.168.1.0-192.168.1.255$.

Hvis vi tar en tilfeldig ip-adresse, $192.168.5.88$ og gir den en subnet maske på $/32$, vil det bety at alle 32 bits er reserverte, og derfor kan det kun eksistere **1 IP-adresse** i hele subnettet. $/31$ bits subnet betyr at det kan eksistere 2 ip-adresser, som brukes til isolerte [[Point to Point|PTP]] nettverk.


## Liste av Subnet masker
Her er en illustrasjon av de ulike subnet maskene og hvor mange IP-adressen den tillater.

![[subnet_table.png]]
(Tabell fra [Subnet Masks Table - Connected Dots Online](https://www.connecteddots.online/resources/blog/subnet-masks-table))


## Edge-cases
Som nevnt i forrige artikkel, [[02 IPv4-adresser|IPv4-adresser]], så reserveres den første og siste ip-adressen i et subnet. Merk at $/30$ bits subnet har og bare **2 tillate enheter** på lik linje med $/31$ bit subnet. Dette er fordi et $/30$ bits subnet tillater standard kommunikasjon mellom enhetene og behandler det som et vanlig nettverk (F.eks. Printer og PC). $/31$ bits nettverk fungerer bare til applikasjoner som [[Point to Point|PTP]].


## Oppgave
Se for deg at du skal sette opp et nettverk for en mellomstor bedrift med 200 brukere.

Lag en liste over de ulike enhetene som skal koble seg til, er det fornuftig å ha noen enheter på et eget subnett? F.eks. Printere, servere, ansattmaskiner, gjestenett, osv. Gjerne legg til et fiktivt antall enheter.

Hvor mange IP-adresser bør de ulike subnettene ha? Tenk at bedriften kan vokse og få mer ansatte over tid!

For ekstra utfordring så kan du legge inn en [[02 IPv4-adresser|IP-adresse]] subnettet bør starte fra. Dette har ingen betydning for ytelse, men det kan fungere som en indikator. $10.13.37.X$ (L33T, Elite) er bra for å indikere et gaming-nett og $192.168.107.X$ brukes ofte som et [[IoT]] nett, ettersom 107 er IOT i [[L33T Speak]].

Lag en tabell slik som denne:

| Subnet | Antall enheter | Antall adresser | Start IP |
| -- | -- | -- | -- |
| Printer | 55 | 255 | 192.168.10.1 |
| Gjestenett | 100 | 3000 | 192.168.50.1 |


## Les mer / Kilder
Mangler