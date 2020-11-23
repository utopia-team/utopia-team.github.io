---
layout: post
title: GPU - Lista compatibilitá
date:   2020-10-13 7:00:00 -0600
permalink: /guide/hardware/gpu/compatibilità
---

## Prerequisiti

Al fine di garantire la massima compatibilità, consigliamo di installare i seguenti kext a prescindere dal modello di
GPU utilizzata:

- [Lilu.kext](https://github.com/acidanthera/Lilu/releases)
- [WhateverGreen.kext](https://github.com/acidanthera/WhateverGreen/releases)

Inoltre consigliamo di consultare la [Framebuffer Patching
Guide](https://github.com/acidanthera/WhateverGreen/blob/master/Manual/FAQ.IntelHD.en.md) di
[Acidanthera](https://github.com/acidanthera/) per le iGPU Intel.

#### Navigazione veloce:

- [dGPU Nvidia](#nvidia)
- [iGPU Intel](#intel)
- [Credits](#credits)

<br><br>

## GPU AMD Native

****
<br>

### Navi 10 Series

> OS più recente supportato: Big Sur (11)<br>
> OS di inizio del supporto: Catalina (10.15)

<br>

Dalla versione 10.15.1, Apple ha finalmente ampliato il supporto alle GPU RDNA e Navi!

<details>
    <summary>Schede supportate:</summary>
    <ul>
        <li>RX 5500</li>
        <li>RX 5500 XT</li>
        <li>RX 5600</li>
        <li>RX 5600 XT</li>
        <li>RX 5700</li>
        <li>RX 5700 XT</li>
        <li>RX 5700 XT 50th Anniversary Edition</li>
        <li>Radeon Pro W5700</li>
    </ul>
</details>
<br>

Attenzione: la maggior parte delle GPU Navi richiedono il boot argument agdpmod=pikera per ottenere un output. Nota
inoltre che il funzionamento della DisplayPort è un po’ una scommessa, poiché WhateverGreen deve ancora essere adattato.
Per maggiori informazioni: [RX5700XT: No dual monitor with WEG](https://github.com/acidanthera/bugtracker/issues/617).

<br><br>

### Vega 20 Series

> OS più recente supportato: Big Sur (11)<br>
> OS di inizio del supporto: Mojave (10.14.5)

<br>

Tutte le GPU Vega sono supportate nativamente da MacOS. In particolare, le Vega 20 a partire da Mojave.

Schede supportate:

<ul>
    <li>Radeon VII</li>
</ul>
<br><br>

### Vega 10 Series

> OS più recente supportato: Big Sur (11)<br>
> OS di inizio del supporto: High Sierra (10.13)

<br>

Come le Vega 20, le Vega 10 sono supportate nativamente da macOS, ma il loro supporto parte da High Sierra.

Per coloro che volessero eseguire overclock/undervolt, provate [PyVega](https://github.com/corpnewt/PyVega).

L’unico Brand da evitare per le Vega 10 è `XFX` poichè il `VBIOS` presenta problemi di comunicazione fra OS e GPU, che
non possono essere risolti con un semplice flash del VBIOS di schede reference per via di come la tabella powerplay Vega
interagisce tra OS e GPU.

<details>
    <summary>Schede supportate:</summary>

    <ul>
        <li>Vega 64 Liquid</li>
        <li>Vega 64</li>
        <li>Vega 56</li>
    </ul>

    Radeon Pro:

    <ul>
        <li>Vega Frontier Edition</li>
        <li>Radeon Pro WX 9100</li>
        <li>Radeon Pro WX 7100</li>
    </ul>
</details>
<br><br>

### Radeon Polaris 10 e 20 Series (4xx/5xx)

> OS più recente supportato: Big Sur (11)<br>
> OS di inizio del supporto: Sierra (10.12)

<br>

Per quanto riguarda le Polaris, praticamente ogni modello è supportato se monta core Polaris o Baffin (schede economiche
come la RX 550 montano un core Lexa, e sono quindi non supportate).

Gli unici brand custom che dovresti evitare per le GPU Polaris sono `XFX`, `PowerColor`, `HIS` e `VisionTek`, in quanto
molti utenti hanno avuto problemi a visualizzare Clover e MacOS, e nonostante alcuni abbiano trovato dei workaround,
questi ultimi non sono abbastanza stabili e consistenti da poter essere consigliati.

Schede supportate:

<details>
    <summary>400 Series:</summary>
    <ul>
        <li>RX 480</li>
        <li>RX 470D</li>
        <li>RX 470</li>
        <li>RX 460</li>
    </ul>
</details>

<details>
    <summary>500 Series:</summary>
    <ul>
        <li>RX 590</li>
        <li>RX 580X</li>
        <li>RX 580</li>
        <li>RX 570X</li>
        <li>RX 570</li>
        <li>RX 560X</li>
        <li>RX 560</li>
    </ul>
</details>

<details>
    <summary>Radeon Pro:</summary>
    <ul>
        <li>WX 5100</li>
        <li>WX 4100</li>
        <li>E9550</li>
    </ul>
</details>
<br><br>

### Radeon R7/R9

> OS più recente supportato: Big Sur (11)<br>
> OS di inizio del supporto: Yosemite (10.10)

<br>

R7/R9 sono supportate nativamente da Catalina senza troppi problemi, ma non possiamo garantire il funzionamento delle R5
e R7 poichè non ci sono molti report di successi. Inoltre, tieni a mente che qualsiasi modello diverso dal modello
reference presentano molti problemi e richiedono molto lavoro extra per funzionare adeguatamente. I modelli Sapphire
sono la scelta migliore.

<details>
    <summary>Schede supportate:</summary>
    <ul>
        <li>R9 Fury X</li>
        <li>R9 Fury</li>
        <li>R9 Nano</li>
        <li>R9 390 (FakeID necessario)</li>
        <li>R9 290X/390X</li>
        <li>R9 290/390 (FakeID necessario)</li>
        <li>R9 280x/380x</li>
        <li>R9 280/380 (FakeID necessario)</li>
        <li>R9 270X/370X</li>
        <li>R7 270/370 (FakeID necessario)</li>
        <li>R7 265</li>
        <li>R7 260x/360x</li>
        <li>R9 260/360 (FakeID potrebbe risultare necessario in base al modello)</li>
        <li>R9 255</li>
        <li>R7 250X</li>
        <li>R7 250 (FakeID necessario)</li>
        <li>R7 240 (FakeID necessario)</li>
    </ul>
</details>
<br>

Extras:

- radpg=15: Necessario per l’avvio con modelli HD 7730/7750/7770, R7 250 e R7 250X
- `-raddvi` boot flag: Fix del DVI necessario per le 290X, 370, etc
- InjectAMD: nonostante sia una funzione deprecata, può risultare necessaria per un avvio corretto. (Evita di abilitare
InjectAMD se non strettamente necessario)
- [Guida all’applicazione del FakeID](https://dortania.github.io/Getting-Started-With-ACPI/Universal/spoof.html)

<br><br>

### Radeon HD 8000 Series

> OS più recente supportato: Big Sur (11)<br>
> OS di inizio del supporto: Mountain Lion (10.8)

<br>

<details>
    <summary>Schede supportate:</summary>
    <ul>
        <li>HD 8740</li>
        <li>HD 8760</li>
        <li>HD 8760</li>
        <li>HD 8770</li>
        <li>HD 8850</li>
        <li>HD 8870</li>
        <li>HD 8890</li>
        <li>HD 8950</li>
        <li>HD 8970</li>
    </ul>
</details>
<br><br>

### Radeon HD 7000 Series

> OS più recente supportato: Big Sur (11)<br>
> OS di inizio del supporto: Mountain Lion (10.8)

<br>

<details>
    <summary>Schede supportate:</summary>
    <ul>
        <li>Dual AMD FirePro D300</li>
        <li>Dual AMD FirePro D500</li>
        <li>Dual AMD FirePro D700</li>
        <li>FirePro W7000</li>
        <li>FirePro W9000</li>
        <li>HD 7700</li>
        <li>HD 7730</li>
        <li>HD 7750</li>
        <li>HD 7770</li>
        <li>HD 7790</li>
        <li>HD 7850</li>
        <li>HD 7870</li>
        <li>HD 7870 XT</li>
        <li>HD 7950</li>
        <li>HD 7970</li>
    </ul>
</details>
<br>

Extras:

- `radpg=15`: Necessario per l’avvio con modelli HD 7730/7750/7770, R7 250 e R7 250X GPU
- InjectAMD: Nonostante sia una funzione deprecata, può risultare necessaria per un avvio corretto. (Evita di abilitare
InjectAMD se non strettamente necessario)

<br><br>

## GPU AMD Legacy

****
<br>

Le GPU in lista sono **teoricamente** supportate, ma tieni a mente che la sicurezza è data solo dalla loro eventuale
presenza in un [Mac Pro](https://support.apple.com/en-lamr/HT201805).

Nota: InjectATI potrebbe essere necessario per queste GPU.

### Radeon HD 6000 Series (6xxx)

> OS più recente supportato: High Sierra (10.13.6)<br>
> OS di inizio del supporto: Snow Leopard (10.6)

<br>

<details>
    <summary>Schede supportate:</summary>
    <ul>
        <li>HD 6230</li>
        <li>HD 6250</li>
        <li>HD 6350</li>
        <li>HD 6450</li>
        <li>HD 6570</li>
        <li>HD 6510</li>
        <li>HD 6610</li>
        <li>HD 6670</li>
        <li>HD 6790</li>
        <li>HD 6850</li>
        <li>HD 6870</li>
        <li>HD 6950</li>
        <li>HD 6970</li>
        <li>FirePro V7900</li>
    </ul>
</details>
<br><br>

### Radeon HD 5000 Series (5xxx)

> OS più recente supportato: High Sierra (10.13.6)<br>
> OS di inizio del supporto: Snow Leopard (10.6)

<br>

<details>
    <summary>Schede supportate:</summary>
    <ul>
        <li>HD 5450</li>
        <li>HD 5470</li>
        <li>HD 5570</li>
        <li>HD 5630</li>
        <li>HD 5670</li>
        <li>HD 5690</li>
        <li>HD 5730</li>
        <li>HD 5770</li>
        <li>HD 5850</li>
        <li>HD 5870</li>
    </ul>
</details>
<br><br>

### Radeon HD 4000 Series (4xxx)

> OS più recente supportato: High Sierra (10.13.6)<br>
> OS di inizio del supporto: Snow Leopard (10.6)

- HD 4870

<br><br>

### Radeon HD 3000 Series (3xxx)

> OS più recente supportato: High Sierra (10.13.6)<br>
> OS di inizio del supporto: Tiger (10.4)

- HD 3870

<br><br>

### Radeon HD 2000 Series (2xxx)

> OS più recente supportato: High Sierra (10.13.6)<br>
> OS di inizio del supporto: Tigher (10.4)

- HD 2600 XT
- HD 2400 XT

<br><br>

### Radeon X1000 Series (1xxx)

> OS più recente supportato: Lion (10.7.5)<br>
> OS di inizio del supporto: Tiger (10.4)

- X1900 XT
- X1600
- X1300

<br><br>

### Radeon X800 Series (8xx)

> OS più recente supportato: Lion (10.7.5)<br>
> OS di inizio del supporto: Panther (10.3)


<br><br>

## GPU AMD NON SUPPORTATE

****

### Lexa Series

> OS più recente supportato: Nessuno

<br>

Come per le Navi e le Nvidia non supportate, avrai bisogno di disattivare le GPU Lexa GPU per evitare problemi con
alcune funzioni di MacOS come lo sleep. Guida: Come disattivare le GPU non supportate.

<details>
    <summary>Schede non supportate:</summary>

    <ul>
        <li>WX 3100</li>
        <li>WX 2100</li>
        <li>RX 550X</li>
        <li>RX 550</li>
        <li>RX 540X</li>
        <li>RX 540</li>
    </ul>
</details>
<br><br>

### AMD APU (Tutte le varianti)

> OS più recente supportato: Nessuno

<br>

Le GPU presenti su CPU AMD non sono mai state supportate e il supporto della community è sempre stato pressoché assente.
Nonostante sia possibile ottenere un output video lavorandoci un po’, è praticamente impossibile abilitare
l’accelerazione grafica, rendendo queste APU praticamente inutili su MacOS.

<details>
    <summary>APU non supportate:</summary>
    <ul>
        <li>Vega 11 (Zen)</li>
        <li>Vega 8 (Zen)</li>
        <li>GCN 3 (Escavator Gen 2, Steamroller)</li>
        <li>GCN 2 (Escavator Gen 1, Puma, Puma +)</li>
    </ul>
</details>

<br><br><br>

<h2 id="nvidia">GPU NVIDIA NATIVE</h2>

****
<br>

### Kepler Series (GTX 6xx, 7xx)
> OS più recente supportato: Big Sur (11)<br>
> OS di inizio del supporto: Mauntain Lion (10.8)

<br>

Attualmente, Kepler é l'unica achitettura Nvidia nativa al 100% che funziona con macOS 11 Big Sur. Alcuni utenti hanno
riscontrato problemi con le `GTX 650Ti`, `GTX 660`, `GTX 660ti`, causati da un problema con i driver dovuti al mancato
supporto da parte di Apple al core `GK106` (o comunque un supporto molto blando, dato che il problema sembra essere un
memory leakage che colpisce anche i Mac). Un altro problema con questa generazione é che le schede lower end della prima
generazione possono montare sullo stesso modello un core differente (Fermi). Ad esempio sulla GT 640 é possibile trovare
un core `GF 116` (Fermi, non compatibile) o `GK 107`.

**LE GTX 745, 750 e 750ti NON SONO KEPLER**.

Inoltre tieni a mente che i seguenti sistemi usano una GPU kepler e quindi il supporto a questere GPU dovrebbe rimanere
finché apple non cesserá il mantenimento per i componenti pre Skylake (praticamente tutto ció che é sprovvisto di
USB-C):

| SMBIOS | GPU | Initial Release | Discontinued |
| :--- | :--- | :--- | :--- |
| iMac13,1 | GT 640M | October 23, 2012 | June 18, 2014 |
| iMac13,2 | GT 660M | October 23, 2012 | September 24, 2013 |
| iMac14,1 | GT 750M | September 24, 2013 | October 13, 2015 |
| iMac14,2 | GT 755M | September 24, 2013 | October 13, 2015 |
| iMac14,3 | GT 750M | Septembr 24, 2013 | October 13, 2015 |
| MacBookPro9,1 | GT 650M | June 11, 2012 | October 22, 2013 |
| MacBookPro10,1 | GT 650M | June 11, 2012 | October 22, 2013 |
| MacBookPro11,3 | GT 750M | October 22, 2013 | May 19, 2015 |

Schede supportate:

<details>
    <summary>700 Series:</summary>

    <ul>
        <li>GTX Titan (variante con core <code class="language-plaintext highlighter-rouge">GK 110 Maxwell</code>)</li>
        <li>GTX Titan Black (variante con core <code class="language-plaintext highlighter-rouge">GK 110 Maxwell</code>)
        </li>
        <li>GTX Titan Z (una delle poche schede dual GPU supportate da macOS, ma solo un core sará attivo)</li>
        <li>GTX 780 Ti</li>
        <li>GTX 780</li>
        <li>GTX 770</li>
        <li>GTX 760 Ti</li>
        <li>GTX 760</li>
        <li>GT 740</li>
        <li>GT 730 (variante con core <code class="language-plaintext highlighter-rouge">GK208</code>)</li>
        <li>GT 720</li>
        <li>GT 710 (variante con core <code class="language-plaintext highlighter-rouge">GK208</code>)</li>
    </ul>
</details>

<details>
    <summary>600 Series:</summary>

    <ul>
        <li>GTX 690 (un'altra dual GPU compatibile con macOS, ma solo un core sará attivo)</li>
        <li>GTX 680</li>
        <li>GTX 670</li>
        <li>GTX 660 Ti</li>
        <li>GTX 660 (DEVE avere un core <code class="language-plaintext highlighter-rouge">GK 104</code>, NON <code
                class="language-plaintext highlighter-rouge">GK 106</code>)</li>
        <li>GTX 650 (core <code class="language-plaintext highlighter-rouge">GK 107</code>)</li>
        <li>GT 640 (Kepler edition, core <code class="language-plaintext highlighter-rouge">GK 107/208</code>)</li>
        <li>GT 635</li>
        <li>GT 630 (Kepler edition, core <code class="language-plaintext highlighter-rouge">GK 107/208</code>)</li>
    </ul>
</details>

<details>
    <summary>Quadro:</summary>

    <ul>
        <li>Quadro K6000</li>
        <li>Quadro K5200</li>
        <li>Quadro K5000</li>
        <li>Quadro K4200</li>
        <li>Quadro K2000D</li>
        <li>Quadro K2000</li>
        <li>Quadro K600</li>
        <li>Quadro K420</li>
        <li>Quadro 410</li>
        <li>NVS 510</li>
    </ul>
</details>
<br>

Extras:

* `shikigva=40` boot flag: cambia il boardID in iMac14,2 per migliorare il supporto ad Nvidia e le patch whitelist

<br><br>

## GPU NVIDIA NON SUPPORTATE

****
<br>

### Ampere Series (RTX 30xx)
> OS più recente supportato: Nessuno

<br>

Sfortunatamente non é presente alcun supporto in nessuna versione di macOS e nessun driver é stato mai scritto, nemmeno
per High Sierra. Non c'é molto altro da aggiungere


La serie include:

- RTX 3090
- RTX 3080
- RTX 3070

<br>

### Turing Series (RTX 20xx, GTX 16xx)
> OS più recente supportato: Nessuno

<br>

Sfortunatamente non é presente alcun supporto in nessuna versione di macOS e nessun driver é stato mai scritto, nemmeno
per High Sierra. Non c'é molto altro da aggiungere

<details>
    <summary>La serie include:</summary>

    <ul>
        <li>Titan RTX</li>
        <li>RTX 2080 Ti</li>
        <li>RTX 2080 Super</li>
        <li>RTX 2080</li>
        <li>RTX 2070 Super</li>
        <li>RTX 2070</li>
        <li>RTX 2060 Super</li>
        <li>RTX 2060</li>
        <li>GTX 1660 Ti</li>
        <li>GTX 1660</li>
        <li>GTX 1650</li>
    </ul>

    Quadro:

    <ul>
        <li>Quadro RTX 8000</li>
        <li>Quadro RTX 6000</li>
        <li>Quadro RTX 5000</li>
        <li>Quadro RTX 4000</li>
    </ul>
</details>

<br>


### Volta Series (V)
> OS più recente supportato: Nessuno

<br>

Come per Turing, nessun driver é stato mai scritto.

La serie include:

* Titan V
* Titan V CEO Edition
* Quadro GV100

<br>

### Kepler Series(varianti con core GK 106)

Le GPU con core `GK 106` soffrono il serio problema del VRAM leakage. Questo significa che che c'é un'alta probabilitá
di avere distorsioni e instabilitá generale usandole senza purtroppo alcuna soluzione, dato che anche installare i We
Driver risulta inefficace. Una lista di GPU con questo core puó essere trovata
[qui](https://www.techpowerup.com/gpu-specs/nvidia-gk106.g186).

<details>
    <summary>Schede incompatibili:</summary>

    Kepler seconda generazione:
    <ul>
        <li>GT 740</li>
    </ul>

    Kepler prima generazione:

    <ul>
        <li>GTX 660</li>
        <li>GTX 650 Ti</li>
        <li>GTX 650</li>
        <li>GTX 645</li>
    </ul>

    Quadro:
    <ul>
        <li>K4000</li>
    </ul>
</details>

<br>

### Fermi rebranded(GF108, GF117 and GF119)
> OS più recente supportato: High Sierra (10.13.6)<br>
> OS di inizio del supporto: Lion (10.7)

<br>

Visto che nVidia pare non riuscire ad attenersi a nessun nome convezionale, hanno intelligentemente deciso di costruire
alcune schede serie 600/700 usando la loro precedente e incompatibile architettura Fermi.

<details>
    <summary>Tali schede sono:</summary>

    <ul>
        <li>GT 730 (core <code class="language-plaintext highlighter-rouge">GF108)</code></li>
        <li>GT 720A</li>
        <li>GT 710 (core <code class="language-plaintext highlighter-rouge">GF119</code>)</li>
        <li>GT 705</li>
        <li>GT 640 (core <code class="language-plaintext highlighter-rouge">GF108</code> e <code
                class="language-plaintext highlighter-rouge">GF116</code>)</li>
        <li>GT 630 (core <code class="language-plaintext highlighter-rouge">GF108</code>)</li>
        <li>GT 620</li>
        <li>GT 610</li>
    </ul>
</details>

<br>

### Pascal Series (GTX 10xx)
> OS più recente supportato: High Sierra (10.13.6)<br>
> OS di inizio del supporto: Sierra (10.12.4)

<br>

Un po' tutti sanno cosa é successo con Pascal e Maxwell: Apple ha tagliato i ponti con nVidia a partire da Mojave.
Pertanto, queste GPU sono supportate fino ad High Sierra 10.13.6 con l'ausilio degli nVidia's Web Drivers.

Schede supportate:

<details>
    <summary>GTX</summary>
    <ul>
        <li>GTX Titan X (core <code class="language-plaintext highlighter-rouge">GP 102-400</code> Pascal)</li>
        <li>GTX Titan Xp (core <code class="language-plaintext highlighter-rouge">GP 102-450</code> Pascal)</li>
        <li>GTX 1080 Ti</li>
        <li>GTX 1080</li>
        <li>GTX 1070 Ti</li>
        <li>GTX 1070</li>
        <li>GTX 1060 (ATTENZIONE: la variante core <code class="language-plaintext highlighter-rouge">GP104</code> con
            VRAM <code class="language-plaintext highlighter-rouge">GDDR5X</code> non é supportata)</li>
        <li>GTX 1050 Ti</li>
        <li>GTX 1050</li>
        <li>GT 1030</li>
    </ul>
</details>

<details>
    <summary>Quadro</summary>

    <ul>
        <li>Quadro GP100</li>
        <li>Quadro P6000</li>
        <li>Quadro P5000</li>
        <li>Quadro P4000</li>
        <li>Quadro P2000</li>
        <li>Quadro P1000</li>
        <li>Quadro P620</li>
        <li>Quadro P600</li>
        <li>Quadro P400</li>
    </ul>
</details>

Driver necessari:

* [Nvidia’s Web drivers](https://www.nvidia.com/download/driverResults.aspx/125379/en-us)

Extras:

* `shikigva=40` boot flag: cambia il boardID in iMac14,2 per migliorare il supporto ad Nvidia e le patch whitelist
* `NvidiaWeb` property: forza `nvda_drv=1` ad ogni avvio. Necessario per sistemi con NVRAM non nativa (EmuVariableUEFI)

<br>

### Maxwell Series (GTX 9xx, 745, 750/ti)
> OS più recente supportato: High Sierra (10.13.6)<br>
> OS di inizio del supporto: Yosemite (10.10.x)

<br>

Anche per Maxwell il supporto si ferma ad High Sierra per via dei Web Drivers. Inoltre, la nomenclatura é un po'
confusa; infatti le GTX 745, 750 e 750ti sono tutte Maxwell anche se vengono vendute nella line Kepler. Pertanto,
prestate attenzione prima di acquistare.

Schede supportate:

<details>
    <summary>GTX</summary>

    <ul>
        <li>GTX Titan X (core <code class="language-plaintext highlighter-rouge">GM 200</code> Maxwell)</li>
        <li>GTX 980 Ti</li>
        <li>GTX 980</li>
        <li>GTX 970</li>
        <li>GTX 960</li>
        <li>GTX 950</li>
        <li>GTX 750 Ti</li>
        <li>GTX 750</li>
        <li>GTX 745</li>

    </ul>
</details>

<details>
    <summary>Quadro</summary>

    <ul>
        <li>Quadro M6000</li>
        <li>Quadro M5000</li>
        <li>Quadro M4000</li>
        <li>Quadro M2000</li>
        <li>Quadro K220</li>
        <li>Quadro K1200</li>
        <li>Quadro K620</li>
    </ul>

</details>

Driver necessari:

* [Nvidia’s Web drivers](https://www.nvidia.com/download/driverResults.aspx/125379/en-us)

Extras:

* `shikigva=40` boot flag: cambia il boardID in iMac14,2 per migliorare il supporto ad Nvidia e le patch whitelist
* `NvidiaWeb` property: forza `nvda_drv=1` ad ogni avvio. Necessario per sistemi con NVRAM non nativa (EmuVariableUEFI)

<br><br><br>

<h2 id="intel">iGPU INTEL SUPPORTATE</h2>

****
<br>

La cosa principale da fare per far funzionare tutto a dovere è applicare una patch al FrameBufer. Maggiori informazioni
[QUI](https://github.com/acidanthera/WhateverGreen/blob/master/Manual/FAQ.IntelHD.en.md). Escluderemo anche le iGPU
presenti nei Pentium, Atom e Celeron, poichè in genere non sono mai state supportate nativamente e richiedono un
quantitativo di lavoro non indifferente per farle funzionare. Nello specifico, le iGPU basate su `GT1` non funzionano.
Apple usa solo `GT2` o superiori sui mac.

***Problemi di DRM*** : Con le iGPU da Haswell in poi, il DRM non funziona su macOS Catalina, colpendo iTunes Movies,
Apple TV+, Amazon Prime e Netflix. L’unico fix è utilizzare una dGPU dedicata, preferibilmente Polaris o più recente,
che supporti `HEVC`.

Maggiori informazioni: [WhateverGreen’s DRM
Chart](https://github.com/acidanthera/WhateverGreen/blob/master/Manual/FAQ.Chart.md).

<br>

### Ivy Bridge i3/5/7-3XXX
> OS più recente supportato: Catalina (10.15)<br>
> OS di inizio del supporto: Lion (10.7)

<br>

Per i possessori di una Intel HD Graphics 4000, la scheda è nativamente supportata su macOS Catalina 10.15 (ma non
compatibile con macOS 11: Big Sur). Tuttavia, la Intel HD Graphics 2500 è parzialmente supportata su macOS Mojave 10.14,
di conseguenza bisogna disporre di una GPU dedicata compatibile.

<details>
    <summary>iGPU supportate:</summary>

    <ul>
        <li>Intel HD Graphics 2500</li>
        <li>Intel HD Graphics 4000</li>
        <li>Intel HD Graphics P4000</li>
    </ul>
</details>
<br>

### Haswell i3/5/7-4XXX
> OS più recente supportato: Big Sur (11)<br>
> OS di inizio del supporto: Mauntain Lion (10.8)

<br>

La maggior parte delle GPU elencate di seguito sono supportate. L’unica che non è nativamente supportata è la Intel HD
Graphics 4400 che richiede un DeviceID fake con WhateverGreen o con un path ACPI modificato.

<details>
    <summary>iGPU supportate:</summary>

    <ul>
        <li>Intel HD Graphics 4200</li>
        <li>Intel HD Graphics 4400 (HD 4600 FakeID richiesto)</li>
        <li>Intel HD Graphics 4600</li>
        <li>Intel HD Graphics 5000</li>
        <li>Intel HD Graphics 5100</li>
        <li>Intel HD Graphics P4600 (teoricamente)</li>
        <li>Intel HD Graphics P4700 (teoricamente)</li>
    </ul>
</details>
<br>


### Broadwell i3/5/7-5XXX
> OS più recente supportato: Big Sur (11)<br>
> OS di inizio del supporto: Yosemite (10.10.2)

<br>

Tutte le iGPU di seguito elencate sono supportate.

<details>
    <summary>iGPU supportate:</summary>

    <ul>
        <li>Intel HD Graphics 5300</li>
        <li>Intel HD Graphics 5500</li>
        <li>Intel HD Graphics 5600</li>
        <li>Intel HD Graphics 6000</li>
        <li>Intel HD Graphics 6100</li>
        <li>Intel HD Graphics 6200</li>
        <li>Intel HD Graphics P5700 (teoricamente)</li>
        <li>Intel HD Graphics Iris Pro P6300</li>
    </ul>
</details>
<br>

### Skylake i3/5/7-6XXX
> OS più recente supportato: Big Sur (11)<br>
> OS di inizio del supporto: El Capitan (10.11.4)

<br>

Tutte le iGPU di seguito elencate sono supportate.

<details>
    <summary>iGPU supportate:</summary>

    <ul>
        <li>Intel HD Graphics 515</li>
        <li>Intel HD Graphics 520</li>
        <li>Intel HD Graphics 530</li>
        <li>Intel HD Graphics P530</li>
        <li>Intel Iris Graphics 540</li>
        <li>Intel Iris Graphics 550</li>
        <li>Intel Iris Pro Graphics 580</li>
        <li>Intel Iris Pro Graphics P555</li>
        <li>Intel Iris Pro Graphics P580</li>
    </ul>
</details>
<br>


### Kabylake i3/5/7-7XXX
> OS più recente supportato: Big Sur (11)<br>
> OS di inizio del supporto: Sierra (10.12.6)

<br>

La maggior parte delle iGPU presenti nei Kabylake sono supportate, fatta eccezione per la HD 610 presente sul Pentium
G4560.
Supportati a partire da MacOS 10.12.6

<details>
    <summary>iGPU supportate:</summary>

    <ul>
        <li>HD 615</li>
        <li>HD 620</li>
        <li>HD 630</li>
        <li>Iris Plus 640</li>
        <li>Iris Plus 650</li>
    </ul>
</details>
<br>


### Kabylake refresh/ Coffee Lake/ Cometlake i3/5/7-8XXX/9XXX
> OS più recente supportato: Big Sur (11)<br>
> OS di inizio del supporto: High Sierra (10.13.6)

<br>

Tutte le iGPU di seguito elencate sono supportate, ma bisogna prestare attenzione all’[i3 8100 e 8350k che utilizzano
una
Intel UHD Graphics 630 diversa (184 shader units vs
192)](https://en.wikipedia.org/wiki/Intel_Graphics_Technology#Kaby_Lake_Refresh_/_Amber_Lake_/_Coffee_Lake_/_Whiskey_Lake_/_Comet_Lake),
la quare richiede un po’ di lavoro in piú per essere supportata in High Sierra.

<details>
    <summary>iGPU supportate:</summary>

    <ul>
        <li>Intel UHD Graphics 615</li>
        <li>Intel UHD Graphics 617</li>
        <li>Intel UHD Graphics 620</li>
        <li>Intel UHD Graphics 630</li>
        <li>Intel Iris Plus Graphics 645</li>
        <li>Intel Iris Plus Graphics 655</li>
    </ul>
</details>
<br>

### Icelake 10XXXX
> OS più recente supportato: Big Sur (11)<br>
> OS di inizio del supporto: Catalina (10.15.4)

<br>

Tutte le iGPU di seguito elencate, sono supportate a partire da macOS Catalina 10.15.4.
***N.B.***: il supporto è ancora giovane, pertanto é probabile che si incontrino bug da sistemare. Inoltre WhateverGreen
avrá bisogno di tempo per trovare ed adattare le patch migliori per queste nuove iGPU.

iGPU supportate:

- Iris Plus G7
- Iris Plus G4

<br><br>

## iGPU INTEL NON SUPPORTATE

****
<br>

Le iGPUs di seguito elencate non sono supportate:

### Braswell
> OS più recente supportato: Nessuno

- HD 400
- HD 405

### Skylake
> OS più recente supportato: Nessuno

- HD 510

### Apollo Lake
> OS più recente supportato: Nessuno

- HD 500
- HD 505

### Kabylake
> OS più recente supportato: Nessuno

- HD 610

### Kabylake refresh/ Coffee Lake/ Cometlake i3/5/7-8XXX/9XXX
> OS più recente supportato: Nessuno

- UHD 610

### Gemini Lake
> OS più recente supportato: Nessuno

- UHD 600
- UHD 605

<br><br>

<h1 id="credits"> Credits </h1>

- Dortania per la [GPU Buyers Guide](https://github.com/dortania/GPU-Buyers-Guide)
- maydayalaska per la traduzione
- Utopia Team