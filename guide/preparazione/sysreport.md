---
layout: post
title: Guida SysReport
date:   2020-10-15 7:00:00 -0600
permalink: /guide/preparazione/sysreport
---

Prima di poter proseguire con la creazione della nostra cartella EFI di OpenCore è necessario ottenere una serie di informazioni relative alla macchina, fra cui:

- Stato del CFG Lock se è una macchina Intel;
- Stato del MAT Support;

nonchè l'estrazione delle tabelle ACPI necessarie alla generazione dei principali SSDT indispensabili per l'avvio di macOS.

## Prerequisiti

- BIOS impostato secondo la [guida](https://utopia-team.github.io/guide/preparazione/bios)
- [EFI di Debug](https://github.com/utopia-team/opencore-debug/releases/latest)
- Macchina di destinazione
- Saper formattare una chiavetta USB
- Chiavetta USB di qualsiasi dimensione

## Step 1: formattazione della chiavetta USB

Formattare la chiavetta USB come di seguito:

![Formattazione chiavetta USB](https://raw.githubusercontent.com/utopia-team/utopia-team.github.io/master/images/Guide/sysreport/1.png)

![Formattazione chiavetta USB completata](https://raw.githubusercontent.com/utopia-team/utopia-team.github.io/master/images/Guide/sysreport/2.png)

## Step 2: copia della EFI di debug

Copiare la EFI di Debug rispettando il tree come di seguito:

![Copia della EFI di debug sulla USB](https://raw.githubusercontent.com/utopia-team/utopia-team.github.io/master/images/Guide/sysreport/3.png)

## Step 3: avviare il PC dalla chiavetta USB

Riavviare il PC lasciando collegata la chiavetta contenente la EFI di debug appena copiata e premere il tasto relativo al boot menu.

Di seguito una lista dei tasti più comuni per aprire il boot-menu su alcune marche di schede madri:

- **ASRock**: `F8`
- **ASUS**: `F8`
- **Dell**: `F12`
- **Gigabyte**: `Canc`
- **MSI**: `F11`

Una volta selezionata la chiavetta USB fra la lista di dispositivi rilevati, verranno visualizzate a schermo una serie di righe:

![OpenCore Debug running](https://raw.githubusercontent.com/utopia-team/utopia-team.github.io/master/images/Guide/sysreport/4.jpg)

Una volta terminato il processo verrà visualizzato il menu del boot-picker come di seguito:

![OpenCore Debug boot-picker](https://raw.githubusercontent.com/utopia-team/utopia-team.github.io/master/images/Guide/sysreport/5.jpg)

A questo punto spegnere il PC premendo il tasto di accensione del PC.

## Conclusione

All'interno della chiavetta USB troveremo:

- una cartella chiamata `SysReport` contenente nella sottocartella `ACPI` le tabelle ACPI della macchina di destinazione;
- un file chiamato `opencore-YYYY-MM-DD-hhmmss.txt` contenente informazioni sullo stato del `CFG Lock` e del `MAT Support`.

![SysReport e opencore.txt](https://raw.githubusercontent.com/utopia-team/utopia-team.github.io/master/images/Guide/sysreport/6.png)

# Credits

- Il [team Utopia](https://github.com/utopia-team) per la creazione della EFI di Debug
- [@dreamwhite](https://github.com/dreamwhite) per la scrittura di questa guida
- [@maydayalaska](https://github.com/maydayalaska) per aver contribuito al materiale multimediale
