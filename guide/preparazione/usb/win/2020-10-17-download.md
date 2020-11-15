---
layout: post
title: Creazione USB da Windows – gibMacOS Recovery Install
date:    2020-10-17 7:00:00 -0600
permalink: /guide/preparazione/usb/win/download
---

# Download dell'installer

GibMacOS è uno strumento utilizzato per scaricare e flashare su USB l'installer di MacOS da qualsiasi sistema operativo. In questo caso andremo ad utilizzarlo direttamente su Windows per scaricare la Recovery di macOS, la quale scaricherá il sistema durante l'installazione.

![Screen gibMacOS Clone](https://www.hackintoshitalia.it/wp-content/uploads/2020/05/screen-gib.png)

Per prima cosa, rechiamoci sulla [repository gitHub](https://github.com/corpnewt/gibMacOS) dello sviluppatore CorpNewt, scarichiamo gibMacOS cliccando su `Clone or Download > Download ZIP` ed estraiamolo.


![Windows download GIF](https://www.hackintoshitalia.it/GIFs/gib-download-windows.gif) 

Adesso avviamo lo script `gibMacOS.bat`. Si avvierà un terminale con delle istruzioni molto chiare, ma per sicurezza vi guiderò nella selezione.  
GibMacOS ha bisogno di Python per funzionare. Se questo non è presente sul vostro PC, vi chiederà di installarlo automaticamente.  
Premiamo `M` e poi `Invio`. Scriviamo la versione di MacOS che vogliamo scaricare (Es.: `10.15`) e premiamo `Invio`. Ora premiamo `R` e nuovamente `Invio` per caricare la lista delle recovery.  
Ora, dalla lista, dobbiamo scegliere la versione fullinstall che fa al caso nostro (consiglio la più recente riconoscibile dalla scritta `Added` seguita dalla data `AAAA-MM-GG`). Accanto alla versione scelta ci sarà un numero. Scriviamolo e premiamo `Invio` per iniziare il download. Quando gibMacOS avrà finito, mostrerà un resoconto. Controlliamo che non ci siano errori nel download e, se non ce ne sono, chiudiamo gib.

![GIF Windows](https://www.hackintoshitalia.it/GIFs/makeinstall-windows-gibmacos.gif) 

Adesso andiamo nella cartella di gibMacOS e poi in `gibMacOS/macOS Downloads/publicrelease`. Troveremo al suo interno un'altra cartella con un codice e la versione che abbiamo scaricato. Apriamola e all'interno ci sarà un file chiamato `RecoveryHDMetaDmg.pkg`. Clicchiamoci sopra, premiamo in cima all'explorer il tasto `Home` e successivamente su `Copia percorso`. Facciamo click destro sul terminale e premiamo `Invio`. Ora attendiamo che gibMacOS finisca e la USB sarà pronta.