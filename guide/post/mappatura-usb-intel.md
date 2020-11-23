---
layout: post
title: Mappatura porte USB Intel
date:   2020-08-10 7:00:00 -0600
permalink: /guide/post/mappatura-usb-intel
---

**Questa sezione della guida è presa da [questo link](https://aplus.rs/2020/usb-mapping-how/). Tutti i crediti relativi a questa sezione vanno ai rispettivi autore**

Quando si sceglie un SMBIOS da emulare - ad esempio iMacPro1,1 - macOS caricherà una mappatura delle porte USB relativa a tale macchina. Apple conosce perfettamente la configurazione hardware dei suoi modelli 
dunque non occorre effettuare una scansione dell'hardware (come fanno Windows e Linux). Tutto è noto in anticipo.

Una cosa che Apple sa è che nessuna delle loro macchine ha più di una dozzina di porte USB per controller, tant'è che a partire da macOS 10.11 (El Capitan) hanno introdotto un limite rigido di porte USB per controller, pari a 15.

D'altronde, l'hardware dei PC è molto vario. La maggior parte delle schede madri presenta un grande numero di porte USB interne ed esterne. Non è raro trovare 6-8 o più porte USB nel back-panel.

Eventuali porte USB presenti sul case sono collegate agli header interni della scheda madre.
Ogni porta USB 3.0 è retrocompatibile con le USB 2.0 e per tanto ogni porta USB 3.0 viene contata due volte (una USB 3.0 e una USB 2.0). In più ci sono le porte USB Type-C che sono compatibili USB 3.0 e USB 2.0 ma sono anche invertibili e per tanto richiedono uno speciale trattamento.

In generale, in funzione del chipset e delle specifiche della scheda madre, questo limite di 15 porte può essere facilmente sforato.

Tuttavia, ciò che ci salva è che di solito ci sono diversi controller USB nell'hardware del PC e dipende dal chipset e dalle scelte del produttore. 

Eventuali HUB USB e altri dispositivi non vengono considerati in quatno sono sempre collegati ad una sola porta.

Cosa significa tutto ciò? 

La conseguenza più ovvia è che alcune porte USB potrebbero non funzionare: macOS ignorerà ogni porta USB numerata dopo la 15esima su quel particolare controller.

Non c'è alcuna logica specifica relativa a quale porta non funzionerà ma generalmente vengono enumerate prima le porte logiche USB 2.0 e poi le porte USB 3.0. E' possibile addirittura che alcune porte verranno ignorate, nonostante il numero totale di porte sia inferiore a 15, proprio a causa della mappatura hardware di macOS; sulla mia scheda madre ASRock, le porte 1 e 9 sono state rimosse da uno dei 3 controller USB presenti.

Come potete notare, questa mappa non è sequenziale e le porte fisiche vengono mappate su posizioni (più o meno) casuali.



## Requisiti  

  * Sito e manuale della scheda madre/laptop
  * Dispositivo USB 2.0 (un mouse, una tastiera et similia)
  * Dispositivo USB 3.0 (una chiavetta USB 3.0, un HDD esterno et similia)
  * Chiavetta USB su cui mettere OpenCore
  * Tabelle ACPI estratte tramite la [EFI di debug](/guida-sysreport.markdown)
  * [MaciASL](https://github.com/acidanthera/MaciASL/releases/latest)
  * [Hackintool](https://github.com/headkaze/Hackintool/releases/latest)
  * Saper montare una partizione EFI
  * Modificare il config.plist di OpenCore

## Iniziamo

Come prima cosa è bene contare le porte USB presenti sulla propria macchina seguendo il seguente criterio:  


  * le porte USB 2.0 vengono contate come porte singole 
  * le porte USB 3.0 vengono contate come se fossero due porte USB, per via della retrocompatibilità
  * eventuali periferiche collegate agli header interni della scheda madre vengono contate come porte singole (esempio: porte del front panel del case o Fenvi T919)
  * non rientrano nella mappatura eventuali porte del controller ASMedia
  * non rientrano nella mappatura eventuali HUB USB collegati alla macchina: questi sono pur sempre collegati ad una singola porta USB

Esempio

Scheda madre: Asus Z370 Prime A II ([link sito](https://www.asus.com/it/Motherboards/PRIME-Z370-A-II/specifications/))

Secondo la pagina ufficiale della scheda madre abbiamo fino a 12 porte USB (inclusi gli header USB della motherboard):

![1](https://raw.githubusercontent.com/utopia-team/utopia-team.github.io/master/images/Guide/mappatura_usb/1.png)

La seguente è una foto del back panel della scheda madre stessa:

![2](https://raw.githubusercontent.com/utopia-team/utopia-team.github.io/master/images/Guide/mappatura_usb/2.png) 

Procedendo da sinistra verso destra e dall'alto verso il basso, possiamo contare ben:

  * 1 porta USB 3.1 Gen 2 Type-A, appartenente al controller ASMedia (la porta color verde acqua)
  * 1 porta USB 3.1 Gen 2 Type-C, appartenente al controller ASMedia (la porta Type-C)
  * 2 porte USB 2.0 Type-A
  * 2 porte USB 3.1 Gen 1 Type-A

Q: Dunque quante porte della scheda madre dobbiamo mappare?  
A: Escludendo le porte appartenenti al controller ASMedia, dobbiamo mappare le 2 porte USB 2.0 Type-A e le due porte USB 3.1 Gen 1 Type-A, per un totale di 6 porte USB:

  * 2 porte USB 2.0
  * 4 porte USB (2 USB 3.0 e le due porte USB 2.0 retrocompatibili con le USB 3.0) 

**N.B. Qualora il numero di porte USB calcolate sia superiore a 15, bisogna abilitare il quirk `config.plist/Kernel/Quirks/XhciPortLimit`**

## Step 1: Estraiamo le tabelle ACPI ed identifichiamo la tabella USB

Prima di spiegare come estrarre le tabelle ACPI ci terrei a ringraziare [@A23SS4NDRO](https://www.macos86.it/profile/996-a23ss4ndro/) per il testing di questa procedura.

Per prima cosa, scaricare la [EFI di Debug di OpenCore](https://github.com/utopia-team/opencore-debug/releases/latest) e dopo averla messa nella partizione EFI della chiavetta USB, avviare il PC dalla stessa.

Compariranno diverse scritte: non c'è motivo di temere. Una volta arrivati al boot-menu spegnere il PC, riavviare su macOS e montare la partizione EFI della USB.

Oltre alla cartella EFI precedentemente posizionata, troverete due nuovi elementi:

  * cartella `SysReport`
  * `opencore-YYYY-MM-DD_hh-mm-ss.txt`

Il risultato è simile alla seguente foto:  

![3](https://raw.githubusercontent.com/utopia-team/utopia-team.github.io/master/images/Guide/mappatura_usb/3.png)

Arrivati a questo punto, aprire la cartella `SysReport/ACPI` e identificare la tabella ACPI contenente la mappatura delle porte USB.

**Q**: Come diamine identifico questa tabella?

**A**: Generalmente la tabella ACPI che definisce il comportamento delle porte USB si chiama `SSDT-xxxxxx.aml`: aprire ogni singolo file che si chiama così e cercare `HS01`. Iterare questo procedimento finchè non viene identificata la tabella giusta. Qualora non sia stato possibile identificare la tabella ACPI, ripetere il procedimento appena spiegato con il file chiamato `DSDT.aml`

Esempio: nel mio caso la tabella ACPI che definisce il comportamento delle porte USB si chiama `SSDT-2-xh_OEMBD.aml`. So per certo che è la tabella ACPI giusta dal momento che fra le external references ci sono le varie porte USB disponibili sulla mia scheda madre

![4](https://raw.githubusercontent.com/utopia-team/utopia-team.github.io/master/images/Guide/mappatura_usb/4.png)

Q: Ok. e adesso cosa faccio?

A: Adesso occorre identificare il nome delle porte USB tramite Hackintool. E' bene iniziare dalle porte del back panel per poi procedere con le porte del front panel

## Step 2: Identificazione delle porte USB tramite Hackintool

Aprire Hackintool e recarsi nella sezione USB:

![5](https://raw.githubusercontent.com/utopia-team/utopia-team.github.io/master/images/Guide/mappatura_usb/5.png)
Cliccare sull'icona della scopa ed in seguito cliccare sull'icona del refresh button.

Il risultato è simile alla foto di cui sopra.

Arrivati a ciò, staccare ogni periferica USB esterna collegata al PC (mouse, tastiera ecc).

Prendere una periferica USB 2.0, come da requisiti, e collegarla ad una porta USB del back panel. Iterare questo procedimento per ogni porta USB.

Il risultato dovrebbe essere simile al seguente:

![6](https://raw.githubusercontent.com/utopia-team/utopia-team.github.io/master/images/Guide/mappatura_usb/6.png)
  
Nel mio caso, le seguenti porte USB2.0 sono state testate:

  * `HS01` (è la porta retrocompatibile USB3.0)
  * `HS03`
  * `HS04` (è la porta retrocompatibile USB3.0)
  * `HS06` (lettore schede microSD)

**N.B. non tutti i lettori di schede (micro)SD sono mappabili via USB. Dipende dalla motherboard in questione.**

Fanno eccezione le seguenti porte, che sono interne alla motherboard (nel mio caso un laptop):

  * `HS05`
  * `HS07`

Ripetere la procedura per le porte USB 3.0 e segnarsi le porte.  
  
Nel mio caso:  
![7](https://raw.githubusercontent.com/utopia-team/utopia-team.github.io/master/images/Guide/mappatura_usb/7.png)

Le porte USB 3.0 sono:

  * `SS01`
  * `SS03`
  * `SS04`

## Step 3: Mappare le USB modificando il metodo `_UPC`

Prima di mappare le porte USB è bene segnare da qualche parte il valore della `Table Length`, che trovate in cima al file, come da foto: 
 
![8](https://raw.githubusercontent.com/utopia-team/utopia-team.github.io/master/images/Guide/mappatura_usb/8.png)  

Nel mio caso, la Table Length ha un valore di `1879`. E' bene ricordare questo valore perchè servirà in seguito per caricare la mappatura patchata.

Iniziamo la mappatura aggiungendo il metodo `GENG` tramite il menù patch.

Trovate in allegato la patch: [patch.txt.zip](https://www.macos86.it/applications/core/interface/file/attachment.php?id=21188)

![9](https://raw.githubusercontent.com/utopia-team/utopia-team.github.io/master/images/Guide/mappatura_usb/9.png) 

Applicate la patch e cercate la prima porta USB 2.0 della lista che avete appuntato prima. Esempio: `HS01`

Nel mio caso, le porte USB sono definite come segue:

![10](https://raw.githubusercontent.com/utopia-team/utopia-team.github.io/master/images/Guide/mappatura_usb/10.png)  
  
Secondo l'[Advanced Configuration and Power Interface (ACPI) Specification, version 6.3](https://uefi.org/sites/default/files/resources/ACPI_6_3_May16.pdf), pagina [673](https://uefi.org/sites/default/files/resources/ACPI_6_3_May16.pdf#page=673), il metodo `_UPC` ha come valore di ritorno il seguente Package:

```
Return Value Information:
    Package {
    Connectable // Integer (BYTE)
    Type // Integer (BYTE)
    Reserved0 // Integer
    Reserved1 // Integer)
}
```


Dove:

  * `Connectable` è un valore booleano che disattiva/attiva la porta USB (rispettivamente 0/1)
  * `Type` specifica la tipologia di connettore USB

Per semplificarvi la vita ho creato un elenco di valori di `Type`

|Hex|USB Type|
|---|---|
|`0x00`|Type 'A' connector aka USB2|
|`0x01`|Mini-AB connector|
|`0x02`|ExpressCard|
|`0x03`|USB 3 Standard-A connector|
|`0x04`|USB 3 Standard-B connector|
|`0x05`|USB 3 Micro-B connector|
|`0x06`|USB 3 Micro-AB connector|
|`0x07`|USB 3 Power-B connector|
|`0x08`|Type C connector - USB2-only|
|`0x09`|Type C connector USB2 and SS with Switch|
|`0x0A`|Type C connector - USB2 and SS without Switch|
|`0x0B-0xFE`|Reserved|
|`0xFF`|Proprietary connector|

**N.B. lo switch presente nella porta USB identificata dal tipo `0x09`, sta ad indicare che la porta assume il comportamento di una USB3.0 in funzione del verso in cui viene inserita la periferica**

Q: Dunque come mappo?  
A: Devi cambiare il valore di ritorno del metodo `_UPC` come segue:  

  * le porte USB 2.0 sono identificate dal nome `HSxx` e come valore di Type `0x00` se sono porte USB 2.0 appartenenti al back panel, altrimenti `0xFF` (esempio: la Fenvi T919 ha come Type `0xFF`)
  * le porte USB 3.0 sono identificate dal nome `SSxx` e come valore di Type `0x03` o addirittura `0x07` qualora sia presente l'icona di una batteria di fianco alla porta stessa (che sta ad indicare `powered`) 
  * non occorre modificare il metodo `_UPC` per eventuali porte USB Type-C

Dunque nel caso di una porta USB 2.0 presente sul back panel, avrò un risultato simile a quanto segue:  

![11](https://raw.githubusercontent.com/utopia-team/utopia-team.github.io/master/images/Guide/mappatura_usb/11.png)

dove il primo parametro `One` sta ad indicare che la porta è attiva, mentre `Zero` indica la tipologia di connettore.

Iterare questo procedimento per ogni porta USB 2.0 del back panel.

**N.B. Per le porte USB 2.0 del front panel il valore di Type deve essere `0xFF`**:
  
![12](https://raw.githubusercontent.com/utopia-team/utopia-team.github.io/master/images/Guide/mappatura_usb/12.png)

Per le porte USB 3.0 invece, il valore di Type è `0x03` (o in casi estremi `0x07`):   

![13](https://raw.githubusercontent.com/utopia-team/utopia-team.github.io/master/images/Guide/mappatura_usb/13.png)

Per tutte le altre porte USB non rilevate dalla mappatura (ossia quelle non evidenziate in verde su Hackintool) assicurarsi che il metodo `_UPC` ritorni il valore `GUPC(Zero)`.   
Esempio:  

![14](https://raw.githubusercontent.com/utopia-team/utopia-team.github.io/master/images/Guide/mappatura_usb/14.png)

Una volta conclusa la mappatura delle porte USB, salvare il file e posizionarlo nella cartella `OC/ACPI` della EFI.

Infine, aprire il config.plist e, dopo aver aggiunto l'SSDT della mappatura USB (consiglio l'utilizzo di OC-Snapshot) recarsi nella sezione `config.plist/ACPI/Block` e aggiungere quanto segue:

![15](https://raw.githubusercontent.com/utopia-team/utopia-team.github.io/master/images/Guide/mappatura_usb/15.png)

Sostituire il valore del campo `OemTableId` con il `Table Id`,che è possibile ricavare dallo step 3 alla voce `OEM Table Id`, convertito in esadecimale.

**N.B. per evitare il drop di tabelle ACPI indesiderate, consiglio vivamente di lasciare vuoto il campo `OemTableId` ed utilizzare il campo `TableLength`**

Salvare il config.plist e riavviare.

Per assicurarsi che la mappatura delle porte USB sia andata a buon fine, ripetere lo step 2 ed assicurarsi che siano presenti ed evidenziate in verde solo le porte USB mappate.

Credits:

  * [@Gengik84](https://www.macos86.it/profile/1-gengik84/) per il suo thread originale ([link](https://www.macos86.it/topic/9-mappatura-porte-usb/page/1)) e la patch GENG che ho convertito in patch MaciASL
  * [@A23SS4NDRO](https://www.macos86.it/profile/996-a23ss4ndro/) per avermi aiutato con OpenCore e la creazione della EFI di Debug
  * Il progetto ACPICA
  * Apple
  * Acidanthera per lo sviluppo di OpenCore e MaciASL
  * Headkaze per lo sviluppo di Hackintool