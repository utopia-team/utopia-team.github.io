---
layout: post
title: Fix orario dual-boot macOS / Windows 10
date:    2020-07-20 7:00:00 -0600
permalink: /guide/troubleshooting/ora
---
##  Sincronizzazione dell’orologio-Windows

Scaricare questo [file](http://www.hackintoshitalia.it/hackintosh/Fix Ora/Fixora.zip) ed eseguirlo come amministratore

Andate su `Impostazioni > Data e Ora` e riaggiornate l’ora con quella corrente.

## Sincronizzazione dell'orologio-Linux

Se hai un triple-boot, c'è anche un modo per sincronizzare Linux con il metodo di Windows di tenere il tempo. 
Questo non risolverà i tuoi problemi in macOS, tuttavia, quindi la soluzione sopra è ancora superiore.

Il modo più affidabile per concordare il tempo tra Linux e Windows è quello di cambiare la metodologia di mantenimento del tempo di Linux. Anche se questo non è esplicitamente supportato, è leggermente più affidabile che fare lo stesso in Windows. Funziona su qualsiasi tipo di Linux usando `systemd`, che include Ubuntu, Fedora, Red Hat, Debian e Mint. Modifica del tempo di Windows in genere funziona bene anche, ma a volte può portare a instabilità nel software di terze parti che si aspetta che il tempo memorizzato per essere ora locale.

1. Apri Terminale ed esegui il seguente comando:

`timedatectl set-local-rtc 1 --adjust-system-clock`

![Windows e macOS che mostrano tempi diversi](https://www.applegazette.com/wp-content/uploads/2018/01/windows-linux-dual-boot-time-0-550x105.png)

Questo dirà al sistema di interpretare l'ora memorizzata della scheda madre come ora locale. Linux non applicherà più le regolazioni del fuso orario all'ora memorizzata sulla scheda madre. Di conseguenza, i tuoi orologi si sincronizzeranno.

Se hai mai bisogno di invertire il comando, cambia `1` in uno `0`:

`timedatectl set-local-rtc 0 --adjust-system-clock`