# FAQ: come faccio un hackintosh???
Benvenuto! Queste FAQ sono un work in progress. Se vuoi aggiungere qualcosa fai un pull request oppure segnala con un issue

Prima di fare una qualsiasi domanda, consulta le regole, scrivendo /regole [nel gruppo](https://t.me/Hackintoshitalia).

## Il mio Hardware è compatibile?
- CPU: qualsiasi CPU Intel Core e AMD(il gruppo supporta da Skylake-Comet Lake per Intel, mentre per AMD principalmente Ryzen)
- Motherboard: Cercare di evitare Gigabyte
- Hardware 11th(è supportato con delle limitazioni) 
  -Impossibilità di usare la IGPU, ma solo una gpu dedicata(NO LAPTOP)
  -POWER MANAGEMENT non adatto a questo tipo di CPU(causa SMBIOS NON ADATTO)

## Cos'è il POWER MANAGEMENT?

Quando c'è maggiore carico (causa task intensivi) la CPU aumenta la frequenza di clock. Viceversa in caso di "idle" la CPU scala la frequenza passando a frequenze più basse.

**NON SUPPORTATI DISTRO O PRECOMPILATI COME UNIBEAST O OLARILA**

## Mi sono perso... Cosa mi serve per fare un Hackintosh?
Per fare un hackintosh ti servono i seguenti componenti:
- Un hardware compatibile con macOS
- Un bootloader (come ad esempio OpenCore). Esso richiede:
    - Dei Kernel Extensions, in breve kext, (estensioni che ingannano macOS per avviarlo su un Hackintosh) compatibili con il tuo sistema.
    - Degli SSDT per il tuo sistema se usi OpenCore (per ingannare il Power Management e per la mappatura delle USB)
- Una chiavetta usb da 16 GB o più se usi macOS, altrimenti se usi Windows una qualsiasi chiavetta USB. Nella USB ci metteremo l'installer di macOS
- Un OS decente su cui lavorare
- Un po' di spazio sul disco

## Ho capito che mi serve una chiavetta. Ma come la faccio!?
### Windows
https://www.hackintoshitalia.it/guide/usb-windows
### macOS
https://www.hackintoshitalia.it/guide/usb-mac
### Come monto la EFI?
- Da Windows basta che la copi nella root della usb
- Da mac usa [mountEFI](https://github.com/corpnewt/MountEFI)

## Poi fatta la chiavetta che devo fare?
- Scrivere /OPENCORE [nel gruppo Telegram](https://t.me/Hackintoshitalia)

Guida inserimento Kext in EFI(https://macos86.gitbook.io/guida-opencore/varie/varie/kexts)

Kext necessari di default:
- [VirtualSMC](https://github.com/acidanthera/VirtualSMC/releases)
- [Lilu](https://github.com/acidanthera/Lilu/releases)
- [Whatevergreen](https://github.com/acidanthera/WhateverGreen/releases)
- [AppleALC](https://github.com/acidanthera/AppleALC/releases)
- Kext di [rete](https://dortania.github.io/OpenCore-Install-Guide/ktext.html#ethernet) o per il [WiFi/Bluetooth](https://dortania.github.io/OpenCore-Install-Guide/ktext.html#wifi-and-bluetooth)
- [NVMefix](https://github.com/acidanthera/NVMeFix/releases) per i dischi NVMe
- [Kext voodoo per i trackpad/tastiere portatili](https://dortania.github.io/OpenCore-Install-Guide/ktext.html#laptop-specifics) 

## Troppo casino... VOGLIO farmi fare la EFI
Ho capito...

Chiedi su Discord(scrivendo /assistenza nel gruppo Telegram, **NON RISPONDEREMO A RICHIESTE INVIATE IN PRIVATO/VIA ALTRI SISTEMI DI COMUNICAZIONE**. Inoltre, costruiamo **solo** OpenCore.

- Hardware
- Fai un sysreport:
  1. Scarica [questo file](https://github.com/utopia-team/opencore-debug/releases) ed estrailo.
  2. Formatta una chiavetta usb come FAT32 o FAT.
  3. Avvia la usb precedentemente creata tramite il bios 
  4. Appena finirà di processare, apparirà un menù da cui devi riavviare.
  5. Copia **ENTRAMBI** i dati che sono stati generati (la cartella Sysreport e i file .log) e inviali a chi fai la richiesta.

## Crediti
- Apple for macOS
- Acidanthera per OpenCore
- Hackintoshitalia per l'aiuto dato
- utopia-team per l'idea del sysreport
- dortania per le guide
