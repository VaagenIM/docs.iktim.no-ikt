---
title: DNS
aliases: [DNS,Domain Name System,Navnetjener]
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - Definisjon
  - Nettverk
created: 2022-08-13 20:26:41
updated: 2023-05-04 12:01:14
---
# Domain Name System
Også kalt navnetjener på norsk, eller DNS, er et system som oversetter navn til adresser.

## Funksjonen til en DNS
En DNS har ansvar om å oversette navn til [[02 IPv4 adresser|IP-adresser]]. Et eksempel er addressen til "https://google.com". Dersom noen prøver å besøke nettsiden, vil DNS i bakgrunnen oversette forespørselen til google's adresse som er 142.250.74.46. IP-adressen kan endre seg over tid, og kan til og med endres basert på geolokasjon. En webserver i Norge vil ta kortere tid å svare enn en server i USA.

![[techtarget-dnsworks.png]]
(https://www.techtarget.com/searchnetworking/definition/domain-name-system)

## Hvem bestemmer?
Alle domener på internett styres av en høyere makt, for eksempel `.no` TLD'et (Top Level Domain) er eid av Norge og kan distribueres ut til nordmenn mot betaling. Dersom man kjøper et domene fra for eksempel https://domene.shop, vil man også kunne styre hvilke registreringsverdier domenet skal ha. Det vanligste er et A-register som er hvilken IP-adresse domenet knyttes opp til.

Hvilken navnetjener du benytter velger du selv i ruteren din under [[06 DHCP|DHCP]] instillingene, hvor standard er å få tildelt en navetjener fra tjenesteleverandøren din ([[ISP]]). Det kan likevel være gode grunner til å skifte ut denne, som stabilitet eller hastighet.

Oppdaterer du et A-register vil leverandører automatisk gi beskjed til alle navnetjenere om oppdateringen, og endringen vil trå i effekt i løpet av 48 timer.

Det er likevel mulig for hvem som helst å opprette sin egen navnetjener, for både godt og vondt. [dnsmasq](https://thekelleys.org.uk/dnsmasq/doc.html) er et program som lar deg tilby egen DNS server. Ved å styre din egen navnetjener, styrer du også reglene. Her kan du for eksempel endre registerne for https://facebook.com til å peke mot din egen nettside, eller opprette egne domener. Likevel vil ikke endringene være tilgjengelig for alle, men dersom du administrer et offentlig nett så kan du påvirke nettets brukere til å bruke din navnetjener. Dette kalles for DNS-spoofing og er en av grunnende til at mange er kritiske til åpne nettverk.

Man kan også basere seg på populære navnetjenere, som Google's `8.8.8.8` eller Cloudflare's `1.1.1.1`, og legge inn enkelte endringer, for eksempel å blokkere alle nettadresser som inneholder ordene `ad` eller lignende, ved å bruke tjenester som [Pi-hole](https://pi-hole.net/).

## Feilsøking
DNS har ofte skylden for mange nettverksproblemer, og bør være det første stedet man sjekker dersom man har problemer med internett-koblingen. Fungerer ikke DNS'en, fungerer ikke internettet - selv om man er koblet til internett. Dette er fordi både mennesker, men også en del systemer som printere eller lignende, forholder seg gjerne mer til navn som sjeldent endrer seg enn det de gjør ip-adresser som er i stadig endring.

### Eksempler på feil:
- DNS caches (mellomlagres) for hver nettside du besøker, dersom det er feil i mellomlageret, vil nettsiden muligens ikke lastes riktig.
- Navnetjener er ikke helt oppdatert (inntil 48 timer ved endringer)
- Navnetjener er nede (skjer nesten aldri, har store konsekvenser - det BLIR lagt merke til, store tjenester vil "forsvinne" mens navnetjener er nede.)

![[itsalwaysdns.png]]
