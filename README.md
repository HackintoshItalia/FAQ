# FAQ: come faccio un hackintosh???
Benvenuto! Questa guida è un work in progress. Se vuoi aggiungere qualcosa fai un pull request oppure segnala con un issue

Prima di fare una qualsiasi domanda, consulta le regole del gruppo, avviando il [bot del gruppo](https://t.me/Hackintosh_Italia_BOT).

## Il mio Hardware è compatibile?
- CPU: qualsiasi CPU Intel Core I (il gruppo supporta da Skylake-Comet Lake)
- MotherBoard: casi limite (TODO)
- GPU: Nvidia (Solo serie 6XX e 7XX) o AMD (TODO)
- Periferiche I/O (per laptop)
- NON avere questi dischi Nvme: (TODO)

## Che tipi di Hack supportate?
**OpenCore** se devi costruirlo, altrimenti anche conversioni da **Clover**.

**NON SUPPORTATI DISTRO O PRECOMPILATI COME UNIBEAST O OLARILA**

## Mi sono perso... Cosa mi serve per fare un Hackintosh?
Per fare un hackintosh ti servono i seguenti componenti:
- Un hardware compatibile con macOS
- Un bootloader (come ad esempio OpenCore). Esso richiede:
    - Dei KErnel EXtension, in breve kext, (estensioni che ingannano macOS per avviarlo su un Hackintosh) compatibili con il tuo sistema.
    - Degli SSDT per il tuo sistema se usi OpenCore (per ingannare il Power Management e per la mappatura delle USB)
- Una chiavetta usb da 16 GB o più se usi macOS, altrimenti se usi Windows una qualsiasi chiavetta USB. Dentro la chiavetta ci installeremo l'installer di macOS
- Un OS decente su cui lavorare
- Un po' di spazio sul disco

## Ho capito che mi serve una chiavetta. Ma come diavolo la faccio!?
### Windows
https://www.hackintoshitalia.it/guide/usb-windows
### macOS
https://www.hackintoshitalia.it/guide/usb-mac
### Come monto la EFI?
- Da Windows basta che la copi nella root della usb
- Da mac usa [mountEFI](https://github.com/corpnewt/MountEFI)

## Poi fatta la chiavetta che devo fare?
### Scaricare OPENCORE
[OpenCorePkg](https://github.com/acidanthera/OpenCorePkg)
### Prendere i kext
Seguire la guida [dortania](https://dortania.github.io/OpenCore-Install-Guide/ktext.html) o la sua traduzione (SOON!!!). Copiarli tutti in EFI/OC/kext. Non prendere più kext del necessario.

Kext necessari di default:
- [VirtualSMC](https://github.com/acidanthera/VirtualSMC/releases)
- [Lilu](https://github.com/acidanthera/Lilu/releases)
- [Whatevergreen](https://github.com/acidanthera/WhateverGreen/releases)
- [AppleALC](https://github.com/acidanthera/AppleALC/releases)
- Kext di [rete](https://dortania.github.io/OpenCore-Install-Guide/ktext.html#ethernet) o per il [WiFi/Bluetooth](https://dortania.github.io/OpenCore-Install-Guide/ktext.html#wifi-and-bluetooth)
- [NVMefix](https://github.com/acidanthera/NVMeFix/releases) per i dischi NVMe
- [Kext voodoo per i trackpad/tastiere portatili](https://dortania.github.io/OpenCore-Install-Guide/ktext.html#laptop-specifics)
### Prendere gli ssdt
Anche qua seguire la guida [dortania](https://dortania.github.io/Getting-Started-With-ACPI/). Copiarli in EFI/OC/ACPI
### Editare il config
Ed ora... seguire la guida [dortania!](https://dortania.github.io/OpenCore-Install-Guide/config.plist/) oppure la traduzione (SOON!!!)

## Troppo casino... VOGLIO farmi fare la EFI
Ho capito... Se per favore ci dici: hardware e fai un sysreport come indicato dalla [guida](https://utopia-team.github.io/guide/preparazione/sysreport). Chiedi su discord o sul gruppo telegram. Costruiamo **solo** OpenCore.

## Crediti
- Apple for macOS
- Acidanthera per OpenCore
- Hackintoshitalia per l'aiuto dato
- utopia-team per il sysreport
- dortania per le guide
