---
title: Standardkommandoer i Linux
aliases: [Standardkommandoer i Linux,]
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - Linux
created: 2022-04-09 02:00:00
updated: 2022-08-13 20:30:43
---
# Standardkommandoer i Linux
Kan du disse standardkommandoene i Linux, så kan du få til det meste.

Dog er det en stor tilvending å komme fra andre operativsystemer, ettersom det er utrolig mange måter å gjøre samme ting på, og hjelpen du finner på internett er full av elitistiske nerder som gjør ting på sin unike måte - eller rett og slett overkompliserte løsninger.

Et eksempel på en overkomplisert måte å gjøre noe på kan være å skrive "Hei" i en tekstfil, på nett pleier nerdene å skrive 
```shell
touch file.txt
echo "Hei" > file.txt
```
eller
```shell
cat << EOF > file1.txt
Hei
EOF
```
eller
```shell
touch file.txt
printf "Hei\n" > file.txt
```
For å ikke nevne `joe -help file.txt` eller `vi file.txt`.

Men slik trenger det ikke være; KEEP IT SIMPLE, STUPID.

# Copy/paste
Greit å vite, i konsollvinduet er HØYREKLIKK på musen tilsvarende "Lim Inn", mens kopier skjer automatisk når du markerer tekst. (Gjelder hvertfall dersom du bruker [PuTTY](https://www.putty.org/))

# Autocomplete (TAB knappen)
Tab knappen er din BESTE venn. Trykk på den en gang, så vil den velge et passende alternativ til det du prøver å gjøre. Hvis den ikke gjør noe, trykker du en gang til for å få opp alternativ.

Har vi filen "hei.txt", så trenger man bare skrive "h" + TAB, så vil den fylle ut resten.

# `ls` funksjonen
Gjør: List opp mappeinnhold, enten i mappen du er i, eller en angitt bane.
`ls -a <filbane>` viser alle filer
`ls -lh <filbane>` viser synlige filer som en liste
`ls -lah <filbane>` - viser alle filer som en liste

F.eks. `ls /home/brukernavn/` viser innholdet på skrivebordet hos "brukernavn".
`ls` viser din nåværende mappe.

# `cd` funksjonen
cd står for Change Directory - bytt mappe.
Linux har et unikt mappesystem. `~/` er startmappen til aktiv bruker, `/` er systemet sin rotmappe. Dette kan fort bli komplisert, men fortvil ikke. `/` er på en måte det samme som `C:/` i WIndows.

`cd <mappenavn>` -> beveger terminalen inn i en mappe
`cd ..` -> beveger terminalen opp en mappe
`cd` -> beveger terminalen til startmappen (Der du havner når du logger inn)

# `cat` funksjonen
Står ikke for dyret, men concatenate; prosedyren av å sette sammen bokstaver/tegn til å danne ord/setninger.
`cat <fil>` - leser av filen.

# `rm` funksjonen
rm står for remove - denne sletter en fil.
`rm <filnavn>` - sletter filen.

# `cp` funksjonen
cp står for copy-paste. Kopierer en fil til en annen plass
`cp <filnavn> <destinasjon/filnavn>` -> lager kopi av en fil
`cp <filnavn> <mappe>` -> legger en kopi i en mappe, med samme navn
`cp <filnavn> <nyttnavn>` -> lager en kopi, med et nytt navn

# `mv` funksjonen
mv står for move. Flytter en fil til en annen plass, men kan og gi nytt navn.
`mv <filnavn> <nyttnavn>` -> gir filen nytt navn
`mv <filnavn> <destinasjon>` -> flytter filen

# `nano` programmet
nano er en tekst-editor i konsollen som er den letteste å bruke.
Minner om Notepad på Windows, eller TextEdit på Mac.
`nano <fil>` åpner filen til redigering, hvis filen ikke eksisterer, lager den en ny.
`CTRL+S` lagrer dokumentet
`CTRL+X` avslutter nano
Hvis du har gjort endringer uten å lagre, får du spørsmål om du vil lagre dem. Her må du trykke `N` for nei, `Y` for ja. Velger du ja så må du og bekrefte filnavn (trykk `Enter`

# `apt` - Last ned programmer / utvidelser
APT, eller Advanced Packaging Tool er Linux sin måte å oppdatere, eller installere programvare på. Minner litt om `pip` med Python - som du også kan bruke direkte i Linux.

Noen Linux distroer har ofte og en innebygd App store til å laste ned kommersielle programmer som Steam, Spotify, Teams eller lignende. Dette kan man ikke gjøre med `apt`, men via f.eks. [Snap Store](https://snapcraft.io/store). Ikke tenk på dette :)

For å oppdatere til siste programvare:
```shell
sudo apt-get update
sudo apt-get upgrade -y
```

For å laste ned programmer:
```shell
sudo apt-get install <program>
```

Kan bytte ut `install` med `remove` for å avinstallere.

For å sette opp en nettside/webserver, trenger man ikke gjøre mer enn å laste ned en webserver:
```shell
sudo apt-get install apache2
```
Etter å ha kjørt kommandoen kan du med en gang besøke ip-adressen til enheten i en nettleser og se standardnettsiden.