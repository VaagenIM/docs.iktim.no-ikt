---
title: 04. Hello World webserver
aliases: [Hello World webserver,]
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - Azure
  - Cloud
  - Webserver
created: 2022-04-16 02:00:00
updated: 2022-08-13 20:27:08
---
# 04. Hello World webserver
For å sette opp en enkel webserver i Azure må man gjøre følgende steg:
- [[03 Koble til Virtuell Maskin|Koble seg til via SSH]]
- Laste ned Webserver
- Åpne tilgang i brannmuren (For mer utfyllende, se [[08 Azure Brannmur|Azure Brannmur]])

## Koble til via SSH
For å koble til, følg stegene i [[03 Koble til Virtuell Maskin|03. Koble til Virtuell Maskin]].

## Laste ned Webserver
Inne i terminalen kan vi laste ned en webserver, for eksempel `apache2`. Før vi kan laste ned en pakke, må vi oppdatere listen over pakker. Dette gjør vi via `sudo apt-get update`.

For å laste ned `apache2` webserveren gjør vi dermed følgende:
```sh
sudo apt-get update
sudo apt-get upgrade -y

sudo apt-get install apache2
```

Nå skal maskinen servere en nettside fra mappen `/var/www/html/` helt automagisk. Fra før vil det ligge en `index.html`, eller tilsvarende fil fra `apache2` installasjonen.

Det betyr likevel ikke at nettsiden er tilgjengelig, for å gjøre det tilgjengelig må vi åpne opp i brannmuren.

## Åpne webserver i brannmuren
I Azure må du gå til `Networking` fanen, her skal du komme til en fane som heter `Inbound port rules`. 

![[Azure Brannmur tab.png]]

Dette er brannmursregler om hva som har lov til å koble seg til vår enhet i skyen. Legg til en ny regel og velg service `HTTP` for å åpne port `80`, som er standardport for nettsider.

![[HTTP Service brannmur.png]]

Merk at du trenger ikke spesifisere en `Destination`, med mindre du har mer enn 1 virtuell maskin på ditt Azure nettverk.

Du skal nå kunne gå til http://din_azure_ip_adresse og se nettsiden din.

## Endre innhold
For å endre innholdet på nettsiden til å vise en Hello World, kan man endre `/var/www/html/index.html`

```sh
nano /var/www/html/index.html
```

Endre innholdet til å være:
```html
<h1>Hello Azure!</h1>
<p>Min egen nettside, i SKYA!</p>
```

Lagre med `CTRL+S` og avslutt med `CTRL+X`.

Gratulerer, du har nå satt opp en enkel webserver i himmelen!