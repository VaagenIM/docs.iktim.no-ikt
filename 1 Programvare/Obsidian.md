---
title: Obsidian
aliases: [Obsidian,]
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - Programvare
created: 2022-08-16 21:49:58
updated: 2022-08-17 18:55:18
---
# Obsidian ✍
En moderne tekst editor i Markdown format med mange muligheter.

**Link**: https://obsidian.md/
**Guide**: https://help.obsidian.md/Start+here
**Relevant blogg**: https://theproductiveengineer.net/the-beginners-guide-to-obsidian-notes-step-by-step/

> [!EXAMPLE]- Last ned Sondres oppsett
> Hvis du bare ønsker å bruke samme oppsett som meg, så kan det lastes ned her: https://github.com/sondregronas/obsidian-config/releases/download/latest/sondregronas-obsidian.zip
> Merk at noen plug-ins kan kreve noen justeringer dersom du kopierer mitt oppsett.

## Anbefalt oppsett (Innstillinger)
Her er en kort oppskrift på noen innstillinger du kan justere for å få en smidigere opplevelse med Obsidian

## Bildemappe
Under innstillinger og `Files & Links` er det lurt å oppdatere verdien `Default location for new Attachments` til `In subfolder under current folder`, for å ikke oversvømme velvet med bilder. I eksempelet under er mappenavnet `_attachments` brukt til å lagre bildene.

![[obsidian_files_n_links.png]]

> [!INFO] Tips
> For å legge inn bilder i dokumentet ditt så er det enkleste å bruke Copy & Paste, `CTRL+C` og `CTRL+V`, men du kan også dra det inn i feltet der du vil ha det.

## Anbefalte Plug-ins
### [cMenu](obsidian://show-plugin?id=cmenu-plugin)
Flytende meny for ulike formateringsvalg
![[obsidian_plugin_cmenu.png]]
> [!IMPORTANT] Overskrifter
> Inneholder ikke en knapp for overskrifter. Overskrifter defineres av `#` symboler foran teksten.
> `# Overskrift 1`
> `## Overskrift 2`
> `### Overskrift 3`
> Osv...

### [Highlightr](obsidian://show-plugin?id=highlightr-plugin)
En nyttig <mark style="background: #FFB86CA6;">plug-in</mark> for å <mark style="background: #D2B3FFA6;">markere tekst</mark> med ulike markører.

### [Update Time on Edit](obsidian://show-plugin?id=update-time-on-edit)
Oppdaterer frontmatter (Metadata) automatisk

### [Advanced Tables](obsidian://show-plugin?id=table-editor-obsidian)
Gjør det enkelt å opprette tabeller.

| Eksempel | Tabell |
| -------- | ------ |
| Tekst    | Tekst  |

### [Clear Unused Images](obsidian://show-plugin?id=oz-clear-unused-images)
For å spare på plass kan denne benyttes for å slette bilder som ikke lenger er brukt.

## Avanserte Plugins
### [Templater](obsidian://show-plugin?id=templater-obsidian)
Frontmatter er metadata, som kan være nyttig å ha da det kan tilby ulike ekstra funksjoner ved for eksempel publisering, arkivering eller navigering. For å slippe å skrive frontmatteren selv så kan man benytte seg av Templater pluginen for å automatisere store deler av prosessen.

Lag en mappe `_cfg/templates` i rotmappen av Obsidian velvet ditt, og opprett et dokument som vil være din mal. En template du kan kopiere som er grei å bruke er [obsidian-template.md](https://raw.githubusercontent.com/VaagenIM/files/main/Generelt/Obsidian/obsidian-template.md).

For å aktivere en template på en tom side bruker du hurtigtasten `ALT+E`.

> [!HINT]+
> Under innstillinger kan man definere at malen skal aktiveres ved oppretting av fil.

> [!INFO]- Skjul `_cfg` mappen
> Det er også mulig å skjule `_cfg` mappen gjennom CSS. Dette gjør du via å opprette en ny fil i en ny mappe; `.obsidian/snippets/hide-cfg.css`
> ```css title ".obsidian/snippets/hide-cfg.css"
> div[data-path='_cfg'], 
> div[data-path='_cfg'] + div.nav-folder-children 
> {
>     display: none;
> }
> ```

### Zotero Desktop Connector (Kilderefering)
Litt for avansert til å skrive om her nå... Men nevner at den finnes :)

### Pandoc (Eksportering)
Litt for avansert til å skrive om her nå... Men nevner at den finnes :)