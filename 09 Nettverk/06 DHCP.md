---
title: 06. DHCP
aliases: [DHCP,Dynamic Host Configuration Protocol]
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - Nettverk
  - DHCP
created: 2022-04-27 02:00:00
updated: 2022-08-13 20:26:34
---
# DHCP
## Dynamic Host Configuration Protocol
DHCP står for Dynamic Host Configuration Protocol, som brukes til å gjøre nettverket mer Plug'n'Play.

DHCP er en funksjon i et nettverk. Vanligvis er DHCP forhåndskonfigurert i de fleste rutere, men det kan og installeres på andre maskiner.

En DHCP server sin funksjon er å *hilse* til nye enheter som kobler seg til et nettverk og deler automatisk ut en [[02 IPv4-adresser|IP-adresse]], hvilke [[DNS|Navnetjener(e)]], informasjon om [[03 Subnetting|Subnet Mask]] og en [[Gateway]]. Dersom enheten ikke har disse definert, kan ikke enheten kommunisere på internett. 

Merk at disse kan likevel defineres manuelt på de fleste enheter ved å huke bort "Obtain * automatically", på Mac: "Use DHCP / Manual".

![[tcp-ip-properties.png]]
(Bilde fra: https://www.howtogeek.com/howto/19249/how-to-assign-a-static-ip-address-in-xp-vista-or-windows-7/)

![[mac-manual-dhcp.png]]
(Bilde fra: https://osxdaily.com/2010/12/17/set-static-ip-address-mac/)

## IP-Ranges
DHCP serveren tar utgangspunkt i en IP-range, og begrensningene til en IP-range er definert av subnettet. Det betyr at dersom en IP-range er mellom $192.168.1.6-192.168.1.255$ så vil DHCP serveren kunne automatisk dele ut en ledig ip-adresse mellom de ip-adressene som er spesifisert. Enheter utenfor IP-rangen kan likevel defineres manuelt og brukes blant annet til [[Statisk IP|Statiske IP-adresser]], gitt at det er innforbi nettverkets subnet.

![[dhcp-basics.png]]
(Illustrasjon fra: https://www.cables-solutions.com/pppoe-vs-dhcp-difference.html)