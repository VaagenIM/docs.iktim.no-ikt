---
title: 01 Oppsett av filserver SAMBA CIFS
aliases: [Oppsett av filserver SAMBA CIFS,]
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - Linux
  - NAS
created: 2022-04-09 02:00:00
updated: 2022-08-13 20:25:20
---
# Oppsett av filserver (SAMBA CIFS)
Her er en steg for steg oppskrift på hvordan man setter opp en delt mappe over nettverk på en Linux maskin. Mappen lar deg overføre filer til og fra din maskin, og fungerer i prinsipp på samme måte med delte mapper i en [[NAS]]. Videre kan du koble opp [[samba]] med [[apache2]] og hoste en mappe (med f.eks. HTML) på nettet. For å konfigurere med apache2 se [[02 Oppsett av Apache2 i delt mappe]]

Funksjoner vi trenger: `apt-get`, `mkdir`, `nano`, `smbpasswd`, `systemctl`. Vi skal også leke litt i mappen `/etc/` der vi endrer de fleste instillinger.

## Steg 1: Installasjon
Veldig enkelt i Linux, man installerer programvare ved å bruke `apt-get` funksjonen. Last ned samba med følgende instrukser:
```shell
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install samba samba-common-bin
```

Vi setter opp en delt mappe i vår brukers hjemmemappe (samme som skrivebord). Fullstendig filbane for dette er `/home/NAVNETDITT/`, og er stedet du havner når du først logger på din Linux maskin. Sett opp en mappe med navn `smb` via `mkdir` funksjonen:
```shell
mkdir smb
# Eller: mkdir /home/NAVNETDITT/smb
```

## Steg 2: Sette opp Samba.conf
For å kunne koble opp vår mappe `smb` til Samba/CIFS, må vi bygge en bro mellom dem. I Samba må vi legge til en formel av tekst i bunnen av et konfigurasjonsdokument; `smb.conf`. Denne finner vi i filbanen `/etc/samba/smb.conf`.

Teksten vi må legge til er for eksempel:
```comment
[sondre]
path = /home/sondre/smb
writeable=Yes
create mask=0777
directory mask=0777
public=no
```
Merk at teksten inne i boksen `[sondre]` definerer navnet på den delte mappen, i dette tilfellet vil den delte mappen befinne seg i `<ip-adresse>/sondre` og peke mot path: `/home/sondre/smb`.

Resten av parametrene (writeable, mask og public) handler om tillatelse, ikke bry deg om disse :)

Kopier teksten og rediger navnet til ditt eget, og lim det til slutt inn i .conf filen via kommandoen:
```shell
sudo nano /etc/samba/smb.conf
```
Naviger deg til nederst i dokumentet (CTRL+V hopper nedover raskere) og lim inn tekstbolken. Lagre med `CTRL+S` og avslutt med `CTRL+X`.

## Steg 3: Sette opp Samba bruker
For å kunne koble seg til mappen, må man benytte oss av en bruker som har tilgang. Som standard er det ingen brukere som har tilgang. Den enkleste (men minst sikre måten, ikke så farlig her) er å gi brukeren `root` tilgang, som er adminstratorbrukeren i Linux. For å gi brukeren tilgang brukes kommando:
```shell
sudo smbpasswd -a root
```
Gi brukeren `root` passordet `root` for simpelhetens skyld.

## Steg 4: Restart Samba, og koble til
Nå er du i teorien ferdig! Alt som gjenstår er å bruke endringene. Dette gjør du ved å restarte samba daemonen, som er en tjeneste som kjører i bakgrunnen:
```shell
sudo systemctl restart smbd
```

For å koble til kan du følge oppskriftene basert på hvilken enhet du har:

**Windows**
Oppskrift: [support.microsoft.com](https://support.microsoft.com/en-us/windows/map-a-network-drive-in-windows-29ce55d1-34e3-a7e2-4801-131475f9557d)
URL til nettverksdisken er f.eks. `\\192.168.100.100\sondre` - bruk annen innloggingsinformasjon: `root`, passord `root`.

**MacOS**
Oppskrift: [montana.edu](https://ag.montana.edu/it/support/smb-macs.html)
Erstatt `data$` med din sambafilnavn, f.eks. `smb://192.168.100.100/sondre` - logg inn med registrert bruker `root` passord `root`