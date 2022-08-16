---
title: 02. IPv4-adresser
aliases: [IPv4-adresser, IPv4, IP-adresser]
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - Nettverk
  - Cybersikkerhet
  - IP
created: 2022-04-09 02:00:00
updated: 2022-08-13 20:25:32
---
# IP-adresser (IPv4)
IP adresser er en adresse tildelt alle enheter som kobler seg til internett. Vi skiller IP-adresser i to kategorier, offentlig og privat. Eksempel på en privat ip-adresse er $192.168.1.55$.

En IP-adresse består av 4 [[Oktett|oktetter]], som er det samme som 4 bytes som representerer ulike tall fra $0-255$. Det vil si at ip-adresser starter fra $0.0.0.0$ og slutter på $255.255.255.255$.

En del av ip-adressene er reserverte og kan ikke brukes enn annet de er reservert til, for eksempel er $0.0.0.0$ reservert til å være en ukjent adresse, ofte brukt til å definere "all ukjent trafikk". Regler som `Tillat host 0.0.0.0` betyr egentlig åpent for alle.

Den fjerde oktetten har også noen vanlige reserverte verdier, der den første verdien, f.eks. $X.X.X.1$ betyr [[Gateway]], eller ruter. Den siste verdien, f.eks. $X.X.X.255$ brukes som en felles "radiokanal" hvor alle enheter kan snakke sammen. Eksempelvis brukes den til å fortelle alle PC'er i et nettverk om hvor printeren ligger.


## Privat IP-adresse
Private IP-adresser tildeles av en ruter som er [[NAT|NATet]] fra en offentlig IP-adresse (om den er koblet til internett). Forskjellen mellom private og offentlige IP-adresser er at private IP-adresser aldri kan eksponeres til resten av internett, uten å gå gjennom en ruter som er tildelt en offentlig adresse.

Private IP-adresser finnes i 3 ulike klasser, A, B og C:

| Klasse | IP-start      | IP-stopp          | [[03 Subnetting|Subnet mask]] | Antall Adresser |
| ------ | ------------- | ----------------- | ------------------------------- | --------------- |
| A      | $10.0.0.0$    | $10.255.255.255$  | $/8$                            | $16.777.216$    |
| B      | $172.16.0.0$  | $172.31.0.0$      | $/12$                           | $1.048.576$     |
| C      | $192.168.0.0$ | $192.168.255.255$ | $/16$                           | $65.536$        |


## Offentlig IP-adresse
Offentlige IP-adresser er IP-adresser som gis ut av en internett distributør, eller en [[ISP]]. Adressen er knyttet til den boenheten som eier den og sier noe om fysisk lokasjon. IP-adresser kan også spores når en besøker nettsider. For å finne ut hvilken IP-adresse en har så kan en besøke [WhatIsMyIP.com](https://www.whatismyip.com/)


## Les mer
[TCP/IP addressing and subnetting - Windows Client | Microsoft Docs](https://docs.microsoft.com/en-us/troubleshoot/windows-client/networking/tcpip-addressing-and-subnetting)