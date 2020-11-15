---
layout: post
title: Comandi terminale
date:    2019-09-16 7:00:00 -0600
permalink: /guide/troubleshooting/comandi-terminale
---
## Disabilitare il Gatekeeper

Se si è arrivati a questo punto del sito, è perchè ci siamo stufati del solito messaggio del Gatekeeper:

![1](https://raw.githubusercontent.com/utopia-team/utopia-team.github.io/master/images/Guide/comandi_terminale/1.png) 

Per disabilitare il Gatekeeper occore scrivere da terminale il seguente comando:

`sudo spctl --master-disable`

Infine:

  1. aprire le `Impostazioni di Sistema`, `Sicurezza e Privacy`, `Generali` 
  2. Abilitare le modifiche cliccando sull'icona a forma di lucchetto in basso a sinistra
  3. Selezionare `Anywhere` come raffigurato dal seguente screen

![2](https://raw.githubusercontent.com/utopia-team/utopia-team.github.io/master/images/Guide/comandi_terminale/2.png)

## Aprire applicazioni non riconosciute<figure class="wp-block-image">

![3](https://raw.githubusercontent.com/utopia-team/utopia-team.github.io/master/images/Guide/comandi_terminale/3.png)

Da un terminale scrivere:

`sudo xattr -r -d com.apple.quarantine` 

e trascinare l'app nel terminale

## macOS Catalina: montare il filesystem in lettura-scrittura

E' necessario a volte modificare dei file presenti all'interno del filesystem di macOS.

A partire da macOS Catalina 10.15, il filesystem è stato diviso in due sotto-partizioni:

  * partizione contenente il sistema operativo, accessibile in sola-lettura
  * partizione contenente i dati degli utenti, accessibile in lettura-scrittura

Ciò è stato fatto per garantire l'integrità dei dati dell'utente nel caso qualcosa vada storto con il sistema operativo.

Per abilitare le modifiche sul filesystem, digitare da una finestra di terminale:

`sudo mount -uw /`

Oppure da recovery, digitare:

`csrutil disable; reboot`

<h2 id="montareefi">Montare la partizione EFI</h2>

Ci sono diversi metodi per montare la partizione EFI, ma consigliamo il metodo da terminale:

Digitare:

`diskutil list`

![4](https://raw.githubusercontent.com/utopia-team/utopia-team.github.io/master/images/Guide/comandi_terminale/4.png)

In particolare, prestare attenzione sul seguente pezzo di codice:

![5](https://raw.githubusercontent.com/utopia-team/utopia-team.github.io/master/images/Guide/comandi_terminale/5.png)

La partizione `EFI` ha come `IDENTIFIER` `disk0s1`

Per montare tale partizione scrivere

`sudo diskutil mount disk0s1`

## Trasferire EFI da usb a disco

Montare la partizione EFI del disco e della usb (come detto in precedenza), e trasferire la cartella EFI dalla USB alla partizione del disco

## Verificare stato SIP

Il SIP (dall'inglese System Integrity Protection) è una tecnologia di sicurezza presente da `OS X El Capitan` che previene la modifica di file e cartelle protette sul Mac.

Tuttavia, tale tecnologia, deve essere disabilitata se si ha intenzione di caricare kext custom.

Per verificare lo stato del SIP (che deve essere impostato su `disabled`), digitare da terminale:

`csrutil status`

Da recovery, digitare:

`csrutil disable; reboot`

![6](https://raw.githubusercontent.com/utopia-team/utopia-team.github.io/master/images/Guide/comandi_terminale/6.png)

## App Store: Si è verificato un errore inatteso durante l'accesso

![7](https://raw.githubusercontent.com/utopia-team/utopia-team.github.io/master/images/Guide/comandi_terminale/7.png)

## Step 1: verificare il BSD name

E' importante assicurarsi che il nome della periferica della scheda di rete sia `en0`. Senza di questo si potrebbero riscontrare questi errori.

Per verificare il nome della periferica della scheda di rete, aprire `Hackintool` e recarsi nella sezione `System/Peripherals`:

![8](https://raw.githubusercontent.com/utopia-team/utopia-team.github.io/master/images/Guide/comandi_terminale/8.png)

Leggere la prima riga e assicurarsi che `BSD name` sia impostato su `en0`

Eventualmente questa sia diversa da `en0` reimpostare le impostazioni di rete con i seguenti comandi da terminale:  


N.B. il secondo comando reimposta `Impostazioni di Sistema`

`sudo rm -rf /Library/Preferences/SystemConfiguration/NetworkInterfaces.plist`

`sudo rm -rf /Library/Preferences/SystemConfiguration/preferences.plist`

Riavviare e riprovare ad effettuare l'accesso su App Store.