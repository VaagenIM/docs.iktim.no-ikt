---
title: 02. Sett opp en Virtuell Maskin
aliases: [Sett opp en Virtuell Maskin,]
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - Cloud
  - Azure
created: 2022-04-16 02:00:00
updated: 2022-08-13 20:25:35
---
# 02. Sett opp en Virtuell Maskin
Gå til https://portal.azure.com/#home - dette er dashboardet til Azure. Øverst i feltet kan du finne søkebaren, her kan du skrive inn tjenesten vi ønsker å sette opp som er en [[Virtual Machine|Virtuell Maskin]] (Virtual Machine):

![[virtual-machine-search.png]]

## Lag en Virtuell Maskin
Trykk på Create knappen øverst til venstre på siden, og velg *[[Azure Virtual Machine|Azure virtual machine]]*.

![[create-vm.png]]

Her får man utrolig mange valg, så her er det viktig å ikke miste motet!

**Subscription** og **[[Azure Resource Group|Resource group]]** kan du la stå for nå, disse oppdateres automatisk. Dette er verdier som brukes til å holde oversikt over hvilke tjenester som koster hva og brukes til bl.a. budsjettering og kostnadsfordeling - ikke noe vi trenger å tenke på.

Gi maskinen et navn som beskriver dens formål, *Testing* er et greit navn, *[[Wordpress]]* er et annet, *[[Minecraft Server|Minecraft-Server]]* er og et greit navn som beskriver hva maskinen er.

For **[[Azure Region|Region]]** er det greit å velge *Norway* mens man jobber for nordmenn. Får vår tjeneste mye trafikk fra USA, så kan vi opprette i USA.

**Availability options** kan være standard *No infrastructure redundancy required*.

**Security type** kan være *Standard*.

**[[OS Image|Image]]** er selve operativsystemet vår maskin skal ha, vi skal jobbe med *[[Ubuntu Server|Ubuntu Server 20.04 LTS]]*.

**Size** har en *stor* innvirkning på hvor mye maskinen vår skal koste, en maskin kan koste alt ifra 50kr i måneden til 500kr i minuttet. Her må du trykke **See All Sizes** og søke på den billigste (*[[Standard_B1ls]]*):

![[B1ls-search.png]]

## Dine innstillinger skal/bør nå se slik ut:
![[vm-settings-1.png]]

Merk at vi fremdeles har haugevis av valgmuligheter videre i forhold til størrelse på disker, RAM, plasseringer, IP-adresser og alt mulig rart, men vi trenger ikke forholde oss til dette når vi lærer. Teknisk sett så kan vi gå inn å justere for å kunne spare noe penger og konfigurere felles lagringsarenaer og lignende funksjoner, men det stadiet er vi ikke på nå.

## Administratorkonto og autentisering
Det er likevel noen valg som gjenstår, og det er vår administratorkonto. Her får vi valget mellom [[SSH Keys]] eller Passord. Foreløpig så kan du velge **Passord** da dette er lettere å sette opp, men SSH Keys er teknisk sett mye tryggere og lettere å jobbe med når de er satt opp riktig.

Et godt administratornavn er like viktig som et passord, skriv det gjerne ned. Merk at passordet må inneholde minst 12 bokstaver - skriv dette og gjerne ned en plass. Unngå tullepassord som 123456passord da det kan ha konsekvenser for deg dersom din virtuelle maskin blir kapret.

**Public inbound ports** kan du la stå med [[SSH]] (22) åpen, slik at vi kan [[03 Koble til Virtuell Maskin|koble oss til.]]

![[vm-settings-2.png]]

## Fullfør den virtuelle maskinen
Vi trenger *ikke* gå videre til å konfigurere mer, vi kan nå trykke på *Review + create* knappen for å starte vår maskin. Gratulerer, du har nå laget en server i skyen!

![[review+create.png]]