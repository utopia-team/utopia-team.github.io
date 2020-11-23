---
layout: post
title: Creazione USB da macOS
date:    2020-10-17 7:00:00 -0600
permalink: /guide/preparazione/usb/mac/creazione
---

### 1) Metodo TINU

Per scaricare l’app recarsi su questo <a rel="noreferrer noopener" href="https://github.com/ITzTravelInTime/TINU/releases" target="_blank">link</a>. Se ci sono problemi con l’app scrivere nel <a rel="noreferrer noopener" href="https://t.me/hackintoshitalia" target="_blank">gruppo Telegram</a>

### 2) Metodo Terminale 

# Formattazione USB

Adesso dobbiamo preparare la nostra chiavetta USB. Ovviamente, ne dobbiamo scegliere una che non abbia nessun file importante all'interno, poichè il flash dell'installer andrà ad eliminare tutto il contenuto della chiavetta USB.

![1](https://raw.githubusercontent.com/utopia-team/utopia-team.github.io/master/images/Guide/creazione_usb_macos/1.gif) 

Apriamo `Utility Disco` e abilitiamo la visualizzazione di tutti i dischi. Noteremo ora che sopra alla partizione della nostra chiavetta (in questo caso chiamata USB) sarà apparso l'intero disco (indicato come UFD 2.0 Silicon-Power ecc. nell'esempio).

![2](https://raw.githubusercontent.com/utopia-team/utopia-team.github.io/master/images/Guide/creazione_usb_macos/2.gif) 

Selezioniamo l'intero disco ed inizializziamolo. Per comodità lo rinomineremo sempre USB.

# Flash dell'installer

Ora che la chiavetta è pronta, possiamo procedere con il flash dell'installer.  
Per farlo utilizzeremo il programma `createinstallmedia` presente all'interno dell'installer stesso.

![3](https://raw.githubusercontent.com/utopia-team/utopia-team.github.io/master/images/Guide/creazione_usb_macos/3.gif) 

Clicchiamo col tasto destro sull'installer di MacOS e facciamo Mostra Contenuto Pacchetto e andiamo in **Contents>Resources**. Qui troveremo `createinstallmedia`

![4](https://raw.githubusercontent.com/utopia-team/utopia-team.github.io/master/images/Guide/creazione_usb_macos/4.png) 

Apriamo il terminale, scriviamo `sudo` e facciamo uno spazio. Adesso trasciniamo `createinstallmedia` sul terminale. Scriviamo `-—volume /Volumes/USB`.  
Il risultato dovrebbe essere come quello nell'immagine sopra.

Adesso il terminale ci chiederà di inserire la nostra password (quella che inseriamo al login o quando modifichiamo qualche impostazione). Come misura di sicurezza, il terminale censura la password dando l'impressione di non star scrivendo nulla, ma anche se non verrà visualizzato nulla staremo comunque scrivendo.  
Inseriamo la password e premiamo `Invio`.  
Ora il terminale ci chiederà una conferma. Per confermare basterà scrivere `y` e premere `Invio`.

![5](https://raw.githubusercontent.com/utopia-team/utopia-team.github.io/master/images/Guide/creazione_usb_macos/5.gif) 

Ed eccoci finalmente alla fine! Ora basterà aspettare che il processo termini. La durata varia in base al tipo di porta USB e chiavetta USB che staremo utilizzando. (Es.: utilizzando una chiavetta USB 2.0 i tempi saranno molto più lunghi rispetto ad una 3.0 o più. Inoltre, utilizzare una chiavetta 3.0 su una porta 2.0 limiterà comunque la chiavettà alla velocità di una 2.0)

# Montaggio EFI

Per il montaggio delle EFI seguire questa [guida](https://utopia-team.github.io/2019/09/16/comandi-terminale.html) e vedere la sezione [**Montare la partizione EFI**](https://utopia-team.github.io/2019/09/16/comandi-terminale.html#montareefi).