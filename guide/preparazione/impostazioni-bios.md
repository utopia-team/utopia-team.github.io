---
layout: post
title: Impostazioni BIOS
date:    2020-05-16 7:00:00 -0600
permalink: /guide/preparazione/bios
---

**ATTENZIONE: la posizione delle opzioni può variare in base al modello della scheda e alla versione del BIOS. <br>Usate questo elenco come linea guida per trovare le opzioni sul vostro BIOS.**

## Prima di iniziare

Prima di iniziare ad impostare il BIOS, è consigliabile aggiornarlo all'ultima versione stabile e reimpostare il BIOS alle impostazioni di fabbrica andando su **Save & Exit ➞ Load Optimized Defaults**

La procedura per aggiornare il BIOS varia da produttore a produttore. Le guide sul web sono numerose, tra cui anche quelle ufficiali dei produttori. Qualora abbiate dubbi nel trovare le impostazioni affidatevi a Google :").

<details>
<summary><b>ASUS</b></summary>

Per entrare nel BIOS premete <code>F2</code> continuamente durante l'accensione.<br>
Una volta nel BIOS, premete <code>F7</code> per entrare in <code>Advanced Mode</code>.

Il BIOS è impostato in modo da avere in cima <b>8 categorie principali</b>.<br>
Cliccando su quelle in cima o semplicemente spostandovi con i tasti direzionali <code>Destra</code> e <code>Sinistra</code> sulla tastiera, aprirete i menù contenenti tutte le categorie, sottocategorie ed opzioni.

Per prima cosa andate in <code>Exit</code>, premete su <code>Load Optimized Defaults</code> e confermate.<br>
Successivamente, muovendovi fra questi menù, cercate le seguenti opzioni ed impostatele come indicato:

<ul>
<li><b>AI Tweaker ➞ Ai Overclock tuner</b> = <code>Auto</code></li>
<li><b>Advanced ➞ CPU Configuration ➞ Intel Virtualization Technology</b> = <code>Enabled</code></li>
<li><b>Advanced ➞ CPU Configuration ➞ CPU Power Management Control ➞ CFG Lock</b> = <code>Disabled</code></li>
<li><b>Advanced ➞ System Agent (SA) Configuration ➞ Vt-d</b> = <code>Enabled</code></li>
<li><b>Advanced ➞ PCH Configuration ➞ IOAPIC 24-119 Entries</b> = <code>Enabled</code></li>
<li><b>Advanced ➞ Onboard Devices Configuration ➞ RGB LED Lighting ➞ When system is in sleep, hibernate or soft off states</b> = <code>Aura Off</code></li>
<li><b>Advanced ➞ AMP Configuration ➞ Power On By PCI-E/PCI</b> = <code>Disabled</code></li>
<li><b>Advanced ➞ Network Stack Configuration ➞ Network Stack</b> = <code>Disabled</code></li>
<li><b>Advanced ➞ USB Configuration ➞ Legacy USB Support</b> = <code>Enabled</code></li>
<li><b>Advanced ➞ USB Configuration ➞ XHCI Hand-off</b> = <code>Enabled</code></li>
<li><b>Boot ➞ Fast Boot</b> = <code>Disabled</code></li>
<li><b>Boot ➞ Secure Boot ➞ OS Type</b> = <code>Other OS</code></li>
<li><b>Boot ➞ Secure Boot ➞ Secure Boot Key Management</b> = cliccare su <code>Clear all keys</code></li>
</ul>



Inoltre, impostare la scheda grafica in base a quanto segue:

<details>
<summary><b>Impostazioni BIOS per GPU dedicata</b></summary>

<ul>
<li><b>Advanced ➞ System Agent (SA) Configuration ➞ Graphics Configuration ➞ Primary Display</b> = <code>PCIE</code></li>
<li><b>Advanced ➞ System Agent (SA) Configuration ➞ Graphics Configuration ➞ iGPU Multi Monitor</b> = <code>Enabled</code></li>
<li><b>Exit ➞ Save and Reset</b> = <code>Yes</code></li>
<li><b>Rientrate nel BIOS premendo <code>F2</code> e poi passate allo step successivo</b></li>
<li><b>Advanced ➞ System Agent (SA) Configuration ➞ Graphics Configuration ➞ DVMT Pre-allocated</b> = <code>128MB</code></li>
</ul>

<h4>ATTENZIONE: con schede video AMD il <code>CSM</code> deve essere su impostato su <code>Disable</code>:</h4>

<ul>
<li><b>Boot ➞ Compatibility Support Module ➞ CSM</b> = <code>Disable</code></li>
</ul>

</details>

<details>
<summary><b>Impostazioni BIOS per GPU integrata</b></summary>

<ul>
<li><b>Advanced ➞ System Agent (SA) Configuration ➞ Graphics Configuration ➞ Primary Display</b> = <code>CPU Graphics</code></li>
<li><b>Advanced ➞ System Agent (SA) Configuration ➞ Graphics Configuration ➞ iGPU Multi Monitor</b> = <code>Enabled</code></li>
<li><b>Exit ➞ Save and Reset</b> = <code>Yes</code></li>
<li><b>Rientrate nel BIOS premendo <code>F2</code> e poi passate allo step successivo</b></li>
<li><b>Advanced ➞ System Agent (SA) Configuration ➞ Graphics Configuration ➞ DVMT Pre-allocated</b> = <code>128MB</code></li>
</ul>

</details>
</details>

<hr>
<details>
<summary><b>MSI</b></summary>

Per entrare nel BIOS premete <code>Canc</code> o <code>Del</code> continuamente durante l'accensione.<br>
Una volta nel BIOS, premete <code>F7</code> per entrare in <b>Advanced Mode</b>.</p>


Il BIOS MSI è strutturato in modo da essere diviso in due macrosezioni, che al loro interno comprendono altre sezioni, a loro volta contenenti impostazioni e sottosezioni.

<ul>
<li><b>Settings → Advanced → Integrated Peripherals → Network Stack</b> = <code>Disabled</code></li>
<li><b>Settings → Advanced → Integrated Peripherals → Intel Serial IO</b> = <code>Disabled</code></li>
<li><b>Settings → Advanced → USB Configuration → XHCI Hand-off</b> = <code>Enabled</code></li>
<li><b>Settings → Advanced → USB Configuration → Legacy USB Support</b> = <code>Enabled</code></li>
<li><b>Settings → Advanced → Windows OS Configuration → MSI Fast Boot</b> = <code>Disabled</code></li>
<li><b>Settings → Advanced → Windows OS Configuration → Fast Boot</b> = <code>Disabled</code></li>
<li><b>Overclocking → Extreme Memory Profile (X.M.P)</b> = <code>Enabled</code></li>
<li><b>Overclocking → CPU Features → Intel Virtualization Technology</b> = <code>Enabled</code></li>
<li><b>Overclocking → CPU Features → Intel VT-d Technology</b> = <code>Enabled</code></li>
<li><b>Settings → Boot → Boot mode select</b> = <code>LEGACY+UEFI</code></li>
</ul>
<p>E' possibile abilitare il wake da input USB impostando il BIOS quanto segue:</p>
<ul>
<li><b>Advanced → Wake Up Event Setup → Resume By USB Device</b> = <code>Enabled</code></li>
</ul>


<h4>ATTENZIONE: con schede video AMD il <code>CSM</code> deve essere su impostato su <code>Disable</code>:</h4>


Inoltre, impostare la scheda grafica in base a quanto segue:

<details>
<summary><b>Impostazioni BIOS per GPU dedicata</b></summary>

<ul>
<li><b>Settings ➞ Advanced → Integrated Graphics Configuration → Initiate Graphic Adapter</b> = <code>PEG</code></li>
<li><b>Advanced ➞ System Agent (SA) Configuration ➞ Graphics Configuration ➞ iGPU Multi Monitor</b> = <code>Enabled</code></li>
<li><b>Exit ➞ Save and Reset</b> = <code>Yes</code></li>
<li><b>Rientrate nel BIOS premendo <code>F2</code> e poi passate allo step successivo</b></li>
<li><b>Advanced ➞ System Agent (SA) Configuration ➞ Graphics Configuration ➞ DVMT Pre-allocated</b> = <code>128MB</code></li>
</ul>


<h4>ATTENZIONE: con schede video AMD il <code>CSM</code> deve essere su impostato su <code>Disable</code>:</h4>

<ul>
<li><b>Settings ➞ Boot ➞ CSM</b> = <code>Disable</code></li>
</ul>

</details>

<details>
<summary><b>Impostazioni BIOS per GPU integrata</b></summary>

<ul>
<li><b>Settings ➞ Advanced → Integrated Graphics Configuration → Initiate Graphic Adapter</b> = <code>IGD</code></li>
<li><b>Settings ➞ Advanced → Integrated Graphics Configuration → DVMT Pre-Allocated</b> = <code>128MB</code></li>
</ul>


</details>
</details>

<hr>

<details>
<summary><b>Gigabyte</b></summary>

<p>Per entrare nel BIOS premete <code>Canc</code> o <code>Del</code> continuamente durante l'accensione.<br>
Il BIOS è impostato in modo da avere in cima 7 categorie principali.<br>
Cliccando su quelle in cima o semplicemente spostandovi con i tasti direzionali <code>Destra</code> e <code>Sinistra</code> sulla tastiera, aprirete i menù contenenti tutte le categorie, sottocategorie ed opzioni.</p>
<p>Impostare il BIOS quanto segue:</p>
<ul>
<li><b>M.I.T. ➞ Advanced Memory Settings ➞ Extreme Memory Profile (X.M.P.)</b> = <code>Profile_1</code></li>
<li><b>BIOS ➞ Fast Boot</b> = <code>Disabled</code></li>
<li><b>BIOS ➞ CSM</b> = <code>Disabled</code></li>
<li><b>BIOS ➞ LAN PXE Boot Option ROM</b> = <code>Disabled</code></li>
<li><b>BIOS ➞ Storage Boot Option Control</b> = <code>UEFI</code></li>
<li><b>Peripherals ➞ Trusted Computing ➞ Security Device Support</b> = <code>Disable</code></li>
<li><b>Peripherals ➞ Network Stack Configuration ➞ Network Stack</b> = <code>Disabled</code></li>
<li><b>Peripherals ➞ USB Configuration ➞ Legacy USB Support</b> = <code>Auto</code></li>
<li><b>Peripherals ➞ USB Configuration ➞ XHCI Hand-off</b> = <code>Enabled</code></li>
<li><b>Chipset ➞ Vt-d</b> = <code>Enabled</code></li>
<li><b>Chipset ➞ Wake on LAN Enable</b> = <code>Disabled</code></li>
<li><b>Chipset ➞ IOAPIC 24-119 Entries</b> = <code>Enabled</code></li>
</ul>
</details>

<hr>

<details>
<summary><b>ASRock</b></summary>


<ul>
<li><b>OC Tweaker ➞ DRAM Configuration ➞ Load XMP Setting</b> =  <code>XMP 2.0 Profile 1</code>  </li>
<li><b>Advanced ➞ CPU Configuration ➞ Intel Virtualization Technology</b> = <code>Enabled</code>  </li>
<li><b>Advanced ➞ Chipset Configuration ➞ Vt-d</b> =  <code>Disabled</code>  </li>
<li><b>Advanced ➞ Chipset Configuration ➞ IOAPIC 24-119 Entries</b> =  <code>Enabled</code>  </li>
<li><b>Advanced ➞ Storage Configuration ➞ Sata Mode Selection</b> =  <code>AHCI</code>  </li>
<li><b>Advanced ➞ Super IO Configuration ➞ Serial Port</b> =  <code>Disabled</code>  </li>
<li><b>Advanced ➞ USB Configuration ➞ Legacy USB Support</b> =  <code>Enabled</code>  </li>
<li><b>Advanced ➞ USB Configuration ➞ PS/2 Simulator</b> =  <code>Disabled</code>  </li>
<li><b>Advanced ➞ USB Configuration ➞ XHCI Hand-off</b> =  <code>Enabled</code>  </li>
<li><b>Security ➞ Secure Boot ➞ Secure Boot</b> =  <code>Disabled</code>  </li>
<li><b>Boot ➞ Fast Boot</b> =  <code>Disabled</code>  </li>
<li><b>Boot ➞ Boot From Onboard LAN</b> =  <code>Disabled</code>  </li>
</ul>
<details>
<summary><b>Impostazioni BIOS per GPU integrata</b></summary>
- <b>Advanced ➞ Chipset Configuration ➞ Primary Graphics Adapter</b> =  <code>Onboard</code><br>
- <b>Advanced ➞ Chipset Configuration ➞ IGPU Multi-Monitor</b> =  <code>Enabled</code><br></details>
- <b>Advanced ➞ Chipset Configuration ➞ Shared Memory</b> =  <code>128MB</code>

<details>
<summary><b>Impostazioni BIOS per GPU dedicata</b></summary>
- <b>Advanced ➞ Chipset Configuration ➞ Primary Graphics Adapter</b> = <code>PCI Express</code><br>
- <b>Advanced ➞ Chipset Configuration ➞ IGPU Multi-Monitor</b> =  <code>Enabled</code>
- <b>Advanced ➞ Chipset Configuration ➞ Shared Memory</b> =  <code>128MB</code>

</details>
</details>


