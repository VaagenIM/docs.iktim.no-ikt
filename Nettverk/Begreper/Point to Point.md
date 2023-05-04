---
title: Point to Point
aliases: [Point to Point,PTP]
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - Nettverk
created: 2022-04-09 02:00:00
updated: 2023-05-04 11:04:15
---
# Point to Point
Se også [[Point to Multipoint]]

Merk at PTP er ikke det samme som P2P ([[Peer to Peer]]), som er en protokoll for fillagring.

## Hva er Point to Point?
Point to Point, eller PTP, er en trådløs nettverkskobling som overfører data mellom to punkter, gjerne fra lengre avstander. Som regel benyttes PTP seg av to parabolantenner montert på et høyt punkt som peker mot hverandre ved høy nøyaktighet.

Når to paraboler peker nøyaktig mot hverandre uten hindringer i mellom (inkludert dårlig vær) kan man oppnå over 1Gbit/s hastighet opp til avstander på omtrent 50km. PTP kan bruke vanlig 2.4GHz eller 5GHz WiFi, men for lengre avstander eller høyere hastighet kan 60GHz eller millimeter-wave benyttes.

> [!TECH]+ Typiske bruksområder
> PTP er ikke kun for fancy bedrifter, men også vanlige folk! Her er noen eksempler til bruksområder:
> - Som alternativ til kablet nett, hvor det er uegnet å legge kabel. For eksempel fra et gårdshus til et annet.
> - Koble sammen flere bygninger til samme nett, for eksempel ved Universiteter eller høyskoler.
> - Flere PTP kan skjøtes med kabler og solcellepanel i mellom til å få internett i steder hvor det hverken er 4G dekning eller mulighet for fiber.
> - Få nettverkskobling over hav eller andre hindringer.

## Ressurser
Unifi ISP Design Center er et verktøy fra Ubiquiti som kan brukes til å planlegge PTP/PTMP løsninger ved hjelp av topologi (kartdata). Prøv det ut!

Link: https://ispdesign.ui.com/

## Se det i aksjon
Her er en demonstrasjon og installasjonsvideo fra LinusTechTips hvor PTP brukes til å oppnå stabilt internett til en hytte på en isolert øy.

<iframe width="560" height="315" src="https://www.youtube.com/embed/9T98VsMe3oo" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

