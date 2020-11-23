---
layout: post
title: Schede di rete wireless - Lista compatibilità
date:   2020-10-13 7:00:00 -0600
permalink: /guides/hardware/rete/compatibilità
---

In questa guida andremo ad elencare **solo** chipset nativamente compatibili con MacOS e le sue varie versioni, escludendo qualsiasi scheda che non funzioni in maniera completa, in modo da indirizzare l'utente nell'acquisto di una nuova scheda.  

Se siete giá in possesso di una scheda di rete e necessitate di scoprire se quest'ultima é compatibile, vi consigliamo di controllare la guida [Wireless Buyers Guide](https://dortania.github.io/Wireless-Buyers-Guide/), dove potrete trovare maggiori dettagli su ogni chipset in generale.

N.B.: i Chipset compatibili con una determinata versione di MacOS sono compatibili con le sue versioni precedenti, ma non sono necessariamente compatibili con le versioni successive. Ad esempio, un chipset compatibile con Catalina sará compatibile con Mojave o High Sierra, ma non necessariamente Big Sur.  
  
Legenda:

<span style="color:orange"><strong>•</strong></span> = Compatibile con Big Sur (10.16.x)  
<span style="color:blue"><strong>•</strong></span> = Compatibile con Catalina (10.15.x)  
<span style="color: #CC9900"><strong>•</strong></span> = Compatibile con Mojave (10.14.x)  
<span style="color: #00FFFF"><strong>•</strong></span> = Compatibile con High Sierra (10.13.x)

### PCIe

#### <span style="color:orange"><strong>•</strong></span> BCM94360CD

Fenvi T919

#### <span style="color:orange"><strong>•</strong></span> BCM94360CS2

Fenvi FV-HB1200

### Mini PCIe


 <span style="color: #a6a6a6">Attenzione: il Mini PCIe presenta due varianti chiamate Full Size (grandezza intera), Half Size (metá grandezza).<br>Queste, come si evince dal nome, differiscono in dimensione poiché la Half (LxA=30mm x 26,8mm) é lunga circa la metá di una Full (LxA=30mm x 50,95mm). Un'altra cosa da tenere a mente quando si sceglie una scheda Mini PCIe, é che alcune case produttrici di portatili implementano una whitelist di schede wireless sui propri laptop.<br>Per tanto, se si tenta di utilizzare una scheda di rete diversa da quella installata originariamente, il laptop si bloccherá senza avviarsi.<br>
I marchi piú colpiti da questa piaga sono:<br>
• Lenovo (7<sup>a</sup> gen o precedenti)<br>
• Toshiba<br>
• HP (3<sup>a</sup> gen o precedenti)<br>
• Compaq



#### <span style="color:orange"><strong>•</strong></span> BCM94360HMB (3 antenne)

- Monland AW-CB160H
- Azurewave AW-CB160H

#### <span style="color:orange"><strong>•</strong></span> BCM94352HMB (2 antenne)

- Dell DW1550
- Adanse BCM4352 Half-Size
- AzureWave AW-CE123H Half-Size
- Tutti le schede qui elencate hanno bisogno dei seguenti kext per funzionare:

  * [AirportBrcmFixup](https://github.com/acidanthera/AirportBrcmFixup/releases/latest)
  * [BrcmPatchRAM](https://github.com/acidanthera/BrcmPatchRAM/releases/latest) di cui: 
      1. BrcmBluetoothInjector
      2. BrcmFirmwareData
      3. BrcmPatchRAM in base alla versione di MacOS: 
          * BrcmPatchRAM3 per 10.14+ (obbligatoriamente con BrcmBluetoothInjector)
          * BrcmPatchRAM2 per 10.11-10.14
          * BrcmPatchRAM for 10.10 o precedenti

---

### M.2

<img src="https://i.imgur.com/jBP1D3t.jpg" width="435" height="120"/></figure>

<span style="color: #a6a6a6">Attenzione: il connettore M.2 presenta quattro varianti, chiamate chiavi.<br>
Le chiavi sono A, B, E ed M. I key B ed M sono utilizzati per connessioni PCIe (2x o 4x) e SATA, e vengono accoppiati nella variante ibrida B+M.<br>
Le chiavi A+E sono invece utilizzate per connessioni PCIe 2x e USB e vengono utilizzati per le schede di rete solitamente in un formato ibrido A+E.<br>
Inoltre, bisogna tener conto delle dimensioni della scheda: i formati M.2 piú diffusi sono quelli con una larghezza di 22mm e, nello specifico per le schede di rete, 30mm di altezza (indicata con il codice 2230).<br>
Prima di procedere all'acquisto, consigliamo di controllare le dimensioni massime ospitabili dall'alloggiamento (piú info sui connettori M.2 </span><span style="color: #a6a6a6">[qui](https://www.delock.de/infothek/M.2/M.2_e.html) e [qui](https://arstechnica.com/gadgets/2015/02/understanding-m-2-the-interface-that-will-speed-up-your-next-ssd/)).<br>
Un'altra cosa da tenere a mente quando si sceglie una scheda M.2, é che alcune case produttrici di portatili implementano una whitelist di schede wireless sui propri laptop. Per tanto, se si tenta di utilizzare una scheda di rete diversa da quella installata originariamente, il laptop si bloccherá senza avviarsi.<br>
I marchi piú colpiti da questa piaga sono:<br>
• Lenovo (7<sup>a gen o precedenti. Sulle gen 6 e 7 potrebbe essere rimossa la whitelist su versioni aggiornate del BIOS. Si raccomanda l'update.)

##### <span style="color:orange"><strong>•</strong></span> BCM943602

**ATTENZIONE: prendere RIGOROSAMENTE il chip prodotto da Fenvi, poiché é basato su chip genuino Apple Airport e pertanto nativamente e perfettamente compatibile)**

- Fenvi BCM94360NG

##### <span style="color:orange"><strong>•</strong></span> BCM94352Z

- Fenvi BCM94352Z

---

### USB

**N.B. sconsigliamo altamente l'acquisto delle seguenti schede di rete per coloro che hanno intenzione di effettuare l'installazione di macOS tramite il metodo Internet Recovery Install.<br> Queste schede sono compatibili solo tramite l'applicazione apposita fornita dal produttore**

- TP-Link Archer T4U
- TP-Link Archer T3U
- TP-Link Archer T2U
- TP-Link TL-WN823Nv2
- TP-Link T9UH
- TRENDnet N150 Micro
- Asus AC68
- Asus N13
- Edimax EW-7722UTn V2
- Edimax EW-7822ULC
- EDIMAX EW-7612Uan V2
- EDIMAX EW-7811Un
- Linksys WUSB6300
- Linksys WUSB6400M
