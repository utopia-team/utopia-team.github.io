---
layout: post
title: Download installer da macOS
date:    2020-07-20 7:00:00 -0600
permalink: /guide/preparazione/usb/mac/download
---

# Download dell'installer

GibMacOS è uno strumento utilizzato per scaricare e flashare su USB l'installer di MacOS da qualsiasi sistema operativo. In questo caso andremo ad utilizzarlo direttamente su MacOS, poichè di recente le immagini scaricate direttamente dall'AppStore potrebbero dare problemi durante il flashing su USB.

![1](https://raw.githubusercontent.com/utopia-team/utopia-team.github.io/master/images/Guide/download_installer_macos/1.png)

Per prima cosa, rechiamoci sulla [repository GitHub](https://github.com/corpnewt/gibMacOS) dello sviluppatore CorpNewt, scarichiamo gibMacOS cliccando su `Clone or Download > Download ZIP` ed estraiamolo.

![2](https://raw.githubusercontent.com/utopia-team/utopia-team.github.io/master/images/Guide/download_installer_macos/2.gif) 

Adesso avviamo lo script `gibMacOS.command`. Si avvierà un terminale con delle istruzioni molto chiare, ma per sicurezza vi guiderò nella selezione.
Premiamo `M` e poi `Invio`. Scriviamo la versione di MacOS che vogliamo scaricare (Es.: `10.15`) e premiamo `Invio`.  
Ora, dalla lista, dobbiamo scegliere la versione fullinstall che fa al caso nostro (consiglio la più recente riconoscibile dalla scritta `Added` seguita dalla data in formato `AAAA-MM-GG`. Accanto alla versione scelta ci sarà un numero. Scriviamolo e premiamo `Invio` per iniziare il download. Quando gibMacOS avrà finito, mostrerà un resoconto. Controlliamo che non ci siano errori nel download e, se non ce ne sono, chiudiamo il terminale.


![3](https://raw.githubusercontent.com/utopia-team/utopia-team.github.io/master/images/Guide/download_installer_macos/3.gif) 

##### N.B. Se scaricate Big Sur dovete eseguire l’InstallAssistant.pkg che creerà il .app e lo sposterà in applicazioni. Seguire come ultimo questa [guida](https://www.hackintoshitalia.it/guide/creazione-usb-da-macos/) per creare la USB

Adesso avviamo lo script BuildmacOSInstallApp.command. Si aprirà nuovamente un terminale. Questa volta dovremo trascinare al suo interno i pacchetti che abbiamo appena scaricato con gibMacOS. Tutto quello che gibMacOS ha scaricato ora lo troveremo nella cartella `gibMacOS>macOS Downloads>publicrelease`. Troveremo al suo interno un'altra cartella con un codice e la versione che abbiamo scaricato. Trasciniamola nel terminale e premiamo `Invio`.  
Adesso attendiamo qualche minuto (varia in base alla potenza di calcolo disponibile alla macchina).

![4](https://raw.githubusercontent.com/utopia-team/utopia-team.github.io/master/images/Guide/download_installer_macos/4.png) 

  
Una volta che lo script avrà finito, apriamo la cartella che abbiamo trascinato poco fa ed al suo interno troveremo l'installer di MacOS.  
Per evitare problemi, trasciniamo l'installer nelle applicazioni.

Prossima guida: [Creazione USB da MacOS](https://utopia-team.github.io/guide/preparazione/usb/mac/creazione)