---
title: 05. Last ned mer RAM (SWAP)
aliases: [Last ned mer RAM (SWAP),]
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - Cloud
  - Azure
  - RAM
created: 2022-04-16 02:00:00
updated: 2022-08-13 20:26:06
---
# 05. Last ned mer RAM (SWAP)
I motsetning til maskinene vi er vandt med, kommer ikke Azure sine virtuelle maskiner med [[SWAP]] fil forhåndsdefinert. SWAP er et mellomlager for minnet som er allokert av lagringsdisken. Uten SWAP fil vil programmer krasje når maskinen går tom for RAM. 

Maskinen vi har satt opp hos Azure har kun 512MB med RAM, som begrenser hva vi kan gjøre betraktelig. Ved å allokere en 4GB SWAP-fil (4096MB), vil vi gi maskinen mer pusterom. Effektivt vil maskinen ha 4.5GB med RAM, der kun en liten del av det er 'rask og ekte RAM'.

## Endre `/etc/waagent.conf` (Microsoft Azure Linux Agent)
Vi må endre tektsfilen `/etc/waagent.conf`, dette gjøres ved å bruke en teksteditor, f.eks. [[Nano]]
```sh
nano /etc/waagent.conf
```

Vi må endre følgende linjer til å ha følgende verdier:
```sh
ResourceDisk.Format=y
ResourceDisk.EnableSwap=y
ResourceDisk.SwapSizeMB=4096
```

Trå endringene i effekt ved å kjøre en omstart:
```sh
reboot
```

## Bekreft
For å bekrefte at SWAP filen er generert, kjør kommando `swapon -s`. Denne skal vise til en `/mnt/swapfile` fil.

```sh
root@maskin:~$ swapon -s
Filename
/mnt/swapfile
```

## Les mer
[Add Swap Space to Azure Linux 3CX Instances and Avoid Memory Exhaustion - 3CX](https://www.3cx.com/blog/docs/swap-space-azure-linux/)