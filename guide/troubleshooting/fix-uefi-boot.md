---
layout: post
title: Fix UEFI Boot Windows 10
date:    2020-07-20 7:00:00 -0600
permalink: /guide/troubleshooting/uefi-boot
---

Verificare prima di tutto dal bios se il boot è impostato in UEFI

Inserire il disco di installazione di Windows 10 ed avviare l'installazione

Fare clic su Ripristina il computer o premere F8 nella schermata Installa ora

Fai click su risoluzione dei problemi

![Windows 10 Risoluzione Problemi](https://www.hackintoshitalia.it/wp-content/uploads/2020/07/01-win10-480x388-1.png)

Digitare i comandi di seguito assicurandosi di selezionare il disco ed il volume relativi alla partizione EFI.

<details>
<summary>Comandi:</summary>

<code class="language-plaintext highlighter-rouge">
list disk<br>
sel disk 0<br>
list vol<br>
sel vol X<br>
assign letter=G<br>
exit
</code>
</details>


Per ripristinare il boot loader di Windows 10, infine, digitare i comandi di seguito:

<details>
<summary>Comandi:</summary>
<code class="language-plaintext highlighter-rouge">

cd /d G:\EFI\Microsoft\Boot\<br>
bootrec /fixboot<br>
ren BCD BCD.bak<br>
bcdboot C:\Windows /l it-it /s w: /f ALL<br>
bootrec /rebuildbcd<br> 
exit
</code>
</details>

Fatto questo è possibile riavviare il computer.

# Crediti

- [Microsoft](https://www.microsoft.com/it-it)