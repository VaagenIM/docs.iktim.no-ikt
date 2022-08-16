---
title: 06. Docker og Wordpress
aliases: [Docker og Wordpress,]
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - Azure
  - Docker
  - Wordpress
  - Webdesign
created: 2022-05-03 02:00:00
updated: 2022-08-13 20:26:12
---
# 06. Docker og Wordpress
For å sette opp en enkel webserver i Azure må man gjøre følgende steg:
- [[03 Koble til Virtuell Maskin|Koble seg til via SSH]]
- Laste ned Docker
- Kjør en Docker Container (`sondregronas/wordpress-container`)
- Åpne tilgang i brannmuren (For mer utfyllende, se [[08 Azure Brannmur|Azure Brannmur]])

## Koble til via SSH
For å koble til, følg stegene i [[03 Koble til Virtuell Maskin|03. Koble til Virtuell Maskin]].

## Last ned Docker
Vi bruker [[apt]] til å laste ned [[Docker]], bruk følgende kommandoer i terminalen:
```sh
sudo apt-get update
sudo apt-get install docker.io -y
```

## Kjør en Docker container
Hvordan man kjører, eller installerer en [[Docker Container]] avhenger litt av hvordan [[Docker Image]] (bilde) er satt opp, noen trenger konfigurasjon, andre ikke.

Her har jeg utviklet en container for dere som gjør konfigurasjonen automagisk som ligger her, hvor dere eventuelt kan finne kildekoden: https://hub.docker.com/r/sondregronas/wordpress-container

For å kunne kjøre bildet må man kun definere hvilke nettverksporter den skal lytte på, som skal sendes til port `80` i bildet. Dette gjøres ved å bruke flagget `-p <port>:80` hvor `<port>` er porten du vil maskinen skal åpne opp til internett. Det er derfor viktig at vi ikke bruker en port som allerede er åpen. Hvis du har laget en [[04 Hello World webserver|Hello World webserver]] må du eventuelt avinstallere eller stoppe `apache2` for å kunne bruke port `80`. (`service apache2 stop`)

Vi setter opp Wordpress på port 8080, det gjør vi ved å kjøre følgende kommando:

```sh
docker run -d -p 8080:80 sondregronas/wordpress-container
```

Verre er det faktisk ikke! Alternativt kan den kjøres med andre kontainere eller konfigurasjoner ved å bruke en [[docker-compose]] fil.

Docker containeren lager automatisk en administratorbruker og en gjestebruker. `admin/admin` er innlogging for admin, `guest/guest` er innlogging for gjestebruker. Passord bør byttes ved første anledning.

## Åpne webserver i brannmuren
I Azure må du gå til `Networking` fanen, her skal du komme til en fane som heter `Inbound port rules`.

![[Azure Brannmur tab.png]]

Her må du legge til en ny regel, velg `Custom` port og skriv inn port `8080`.

![[Pasted image 20220503170335.png]]

Du skal nå kunne besøke http://din_azure_ip_adresse:8080 og se ditt nye Wordpress nettsted. Logg inn med `admin/admin` og skift passord.

Se hvordan du kan knytte nettsiden opp til et domene, for å slippe å bruke port :8080 i neste kapittel: [[07 HTTPS og NGINX Proxy Manager]]