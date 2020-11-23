---
layout: post
title: GPU - Guida all'acquisto
date:   2020-10-11 7:00:00 -0600
permalink: /guide/hardware/gpu/buy
---

## Prerequisiti

Al fine di garantire la massima compatibilità, consigliamo di installare i seguenti kext a prescindere dal modello di GPU utilizzata:

- [Lilu.kext](https://github.com/acidanthera/Lilu/releases)
- [WhateverGreen.kext](https://github.com/acidanthera/WhateverGreen/releases)

## GPU da EVITARE

Le GPU da evitare sono un po’ un mix – i brand da evitare al 100% sono `Powercolor`, `HIS` and `VisionTek`, indipendentemente core presente all’interno. Sono le GPU che più comunemente presentano problemi di sbabilità e molti utenti si sono ritrovati senza alcun segnale video in uscita al di fuori della schermata di boot di Clover, rendendo l’installazione di MacOS praticamente impossibile. Dovreste anche evitare `XFX` se possibile, poiché alcuni utenti stanno riscontrando problemi con il brand, nonostante la maggior parte delle GPU XFX funzionano disabilitando la CMS/Legacy Mode (le GPU XFX hanno problemi col VBIOS, ma il VBIOS UEFI funziona). Anche se è possibile far fuzionare le XFX RX 460/560 tramite un flash del VBIOS, è comunque una procedura rischiosa e non raccomandabile. Mentre Sapphire risulterebbe essere il miglior brand per le GPU Polaris, con le GPU Vega la storia è un po’ diversa. Nonostante molte persone hanno un sistema funzionante con schede Sapphire Vega, una grossa fetta di utenti riscontrano instabilità e problemi a far funzionare MacOS correttamente. Update: Con l’arrivo di MacOS 10.14.5, il supporto alle schede Sapphire Vega è stato sensibilmente aumentato. C’è da tener conto, però, che i problemi che si riscontravano erano decisamente sei, quindi fate attenzione poichè non tutti i problemi potrebbero essere stati risolti.

Tutte le `RX 550` NON SONO COMPATIBILI, fatta eccezzione per la `Sapphire Pulse 550 640 SP`. Mentre le altre 550 montano un core Lexa, le Sapphire Pulse 550 640 SP montano un core Polaris.

Per quelli che si stanno chiedendo perché questa lista contraddice la buyer’s guide di Tonymacx86, ricordate che il loro obiettivo è far comprare agli utenti i componenti tramite i loro link referenziali. Tonymacx86 è lo stesso sito che continua a consigliare GPU Pascal a distanza di 5 mesi dal rilascio di Mojave, il quale ha tagliato via ogni compatibilità con le schede Nvidia. Voi vi fidereste di un sito che non è mantenuto e aggiornato e che “offre” tools come UniBeast e MultiBeast?

<details>
<summary>Powercolor (EVITARE OGNI MODELLO)</summary>

<ul>

<li> PowerColor Red Devil RX VEGA 56/64</li>
<li> PowerColor Red Dragon/Devil RX 580</li>
<li> PowerColor Red Dragon RX 560/570</li>
</ul>

</details>

<details>
<summary>XFX (EVITARE le Vega e i modelli 590/560/460)</summary>

<ul>
<li> XFX Reference RX Vega 56/64</li>
<li> XFX Vega 56 Double Dissipation</li>
<li> XFX RX 590 Fatboy</li>
<li> XFX RX 580/570</li>
<li> XFX RX 560</li>
<li> XFX RX 460</li>
</ul> 

</details>

<details>
<summary>HIS (EVITARE OGNI MODELLO)</summary>
<ul>
<li> HIS RX 580 IceQ X² OC</li>
<li> HIS RX 570 IceQ X² OC</li>
<li> HIS RX 560 iCooler OC</li>
</ul>
</details>

<details>
<summary>VisionTek (EVITARE OGNI MODELLO)</summary>
<ul>
<li> VisionTek RX 590 OC Limited Edition</li>
<li> VisionTek OCPC RX 580</li>
<li> VisionTek RX 560 Overclocked</li>
</ul>

</details>
<br>

___

## GPU da acquistare

Quindi ti serve solo un consiglio su che GPU prendere? Onestamente, nella situazione attuale, le uniche schede che potremmo consigliare sono le AMD che vanno dalle Polaris(RX 4xx, 5xx) in poi in termini di data di uscita, poichè le schede AMD su architettura GCN 3 o più vecchie e le Nvidia Kepler potrebbero perdere perdere il supporto in qualsiasi momento. Qui sotto trovate le schede video che consigliamo e ricordate che i modelli Reference sono solitamente la scelta più sicura.

## Modelli fanless (0 dB):

Sfortunatamente c’è poca scelta su questi modelli. Anche se ci sono molti modelli con la funzione fan-stop, non sono comunque soluzioni perfette. Gli unici modelli fanless sono le GT 1030, le quali non sono supportate oltre High Sierra, e le GT 710, che potrebbero perdere il supporto in qualsiasi momento.

<ul>
<li> GT 710 (praticamente ogni modello è single-slot o half-height, molti dei quali fanless) </li>
</ul>


___



## Modelli con Fan-Stop:
###### Solitamente la ventola rimane ferma sotto i 50/60°C


### AMD

<details>
<summary>Navi</summary>
<ul>
<li> Sapphire Nitro+ RX 5700 XT</li>
<li> Sapphire Pulse RX 5700 XT</li>
<li> Gigabyte Gaming OC RX 5700 XT</li>
<li> Asus Strix RX 5700 XT</li>
</ul>
</details>

<details>
<summary>Vega</summary>
<ul>
<li> Asus Strix Vega 56/64</li>
<li> Gigabyte RX Vega 56/64 Gaming</li>
<li> Sapphire NITRO+ RX VEGA 56/64</li>
<li> Sapphire Pulse Vega 56</li>
</ul>
</details>

<details>
<summary>Polaris</summary>
<ul>
<li> Asus Strix RX 580</li>
<li> ASUS Dual series RX 580</li>
<li> Sapphire Pulse RX 580</li>
<li> Sapphire Nitro RX 580</li>
<li> Gigabyte RX 580 Gaming</li>
</ul>
</details>


## Modelli Single Slot:

<h3>AMD</h3>

<details>
<summary>Polaris</summary>

<ul>
<li>Sapphire Pulse RX 550 640SP(assicurati che abbiano un core Polaris o Baffin. Questo modello è uno dei primi a montare un core Baffin anzichè un Lexa)</li>
</ul>
</details>

<details>
<summary>Radeon Pro Vega</summary>

<ul>
<li> Radeon Pro WX 7100</li>
</ul>
</details>

<details>
<summary>Radeon Pro Polaris</summary>

<ul>
<li> Radeon Pro WX 5100</li>
<li> Radeon Pro WX 4100</li>
</ul>
</details>

<h3>Nvidia</h3>

<details>
<summary>Kepler</summary>

<ul>
<li> GT 710 (praticamente ogni modello è single-slot o half-height, molti dei quali fanless)</li>
</ul>
</details>

<details>
<summary>Quadro</summary>

<ul>
<li> Quadro K4200</li>
<li> Quadro K2000D</li>
<li> Quadro K2000</li>
<li> Quadro K600</li>
<li> Quadro K420</li>
<li> Quadro 410</li>
</ul>
</details>


## Modelli Half-height

<h3>AMD</h3>

<details>
<summary>Radeon Pro Polaris</summary>

<ul>
<li>Radeon Pro WX 4100</li>
</ul>
</details>

<h3>Nvidia</h3>

<details>
<summary>Kepler</summary>

<ul>
<li> GT 710 (praticamente ogni modello è single-slot o half-height, molti dei quali fanless)</li>
</ul>
</details>

<details>
<summary>Quadro</summary>

<ul>
<li> Quadro K600</li>
<li> Quadro K420</li>
<li> Quadro 410</li>
</ul>
</details>

## Le GPU più potenti

Nonostante la GPU più potente possa ovviamente sembrare la Radeon VII, tenete a mente che che i driver per quest’ultima non sono maturi come quelli per Vega 10. Per una maggiore affidabilità, converrebbe prendere una GPU Vega 10 (es. RX Vega64) o aspettare che i problemi con il MacPro 7.1 vengano risolti.

### AMD

* Radeon VII
* Sapphire Nitro+ RX 5700 XT
* Sapphire Pulse RX 5700 XT
* Gigabyte Gaming OC RX 5700 XT
* Asus Strix RX 5700 XT
* Asus Strix Vega 64
* Gigabyte RX Vega 64 Gaming
* Sapphire Reference Vega 64


## La GPU più economica

Praticamente qualsiasi GPU integrata (iGPU) presente nella tua CPU.


## Le migliori GPU per hackintosh in generale

### AMD

<details>
<summary>Polaris</summary>

<ul>
<li> Sapphire Nitro+ RX 580</li>
<li> Sapphire Pulse RX 580</li>
<li> MSI Armor RX 580</li>
<li> Asus Strix RX 580</li>
</ul>
</details>

<details>
<summary>Vega</summary>

<ul>
<li> Asus Strix Vega 56/64</li>
<li> Gigabyte RX Vega 56/64 Gaming</li>
<li> MSI Airboost Vega 56/64</li>
<li> Radeon VII</li>
</ul>
</details>

<details>
<summary>Navi</summary>

<li> Sapphire Nitro+ RX 5700 XT</li>
<li> Sapphire Pulse RX 5700 XT</li>
<li> Gigabyte Gaming OC RX 5700 XT</li>
<li> Asus Strix RX 5700 XT</li>
</details>

# Credits
- Dortania per la [GPU Buyers Guide](https://github.com/dortania/GPU-Buyers-Guide)
- maydayalaska per la traduzione 
- Utopia Team