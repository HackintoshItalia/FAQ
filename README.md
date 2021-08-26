# FAQ
Benvenuto! Queste FAQ sono un work in progress. Se vuoi aggiungere qualcosa apri una pull request oppure segnala con un issue

Prima di fare una qualsiasi domanda, consulta le regole, scrivendo /regole [nel gruppo Telegram](https://t.me/Hackintoshitalia).

## Il mio hardware è compatibile?

- CPU:
  - Intel:
      - generazione Skylake fino a Comet Lake
      - CPU HEDT (Xeon) da generazione Haswell-E fino a Cascade Lake-X/W
  - AMD:
      - per ragioni di stabilità solo CPU AMD Ryzen senza APU
 
- Motherboard:

    E' probabilmente la componente più importante per realizzare un hackintosh. Le principali caratteristiche che rendono una motherboard più compatibile dell'altra sono:
    1. `Chipset`: cuore pulsante della scheda madre, è la componente che mette in comunicazione le varie periferiche con la scheda madre stessa;
    2. `Memory Layout`: banalmente tradotto in mappa di allocazione della memoria, è indispensabile per poter avviare macOS. In assenza di una mappa nativamente compatibile, occorrerà ricorrere a patch che possono compromettere in maniera più o meno evidente il funzionamento di macOS;
    3. `Video Memory Layout`: mappa di allocazione delle uscite video, rilevante solo per motherboard Intel accoppiate con CPU con co-processore grafico. In assenza di una mappa nativamente funzionante occorrerà patchare i connettori video.
    4. Mappatura connettori USB: mappa che descrive le porte USB presenti sul PC (back-panel, front-panel, header interni) fino ad un massimo di 15 (per ogni porta USB2 viene considerata una sola porta, mentre per le USB3 2 porte, causa retrocompatibilità). E' importante che queste vengano mappate per rientrare nel limite delle 15 porte.

    Per quanto riguarda il chipset della scheda madre, quelli più indicati sono il chipset `Z`, per schede madri Intel, e il chipset `X` o `B`, per schede madri AMD.
    Ad ogni modo è bene prestare attenzione a quali sono le motherboard più indicate all'acquisto:
    
    - ASUS e AsRock:
      - Sono le motherboard più compatibili con macOS, in termini di memory layout, mappature delle porte USB, video memory layout (mappatura delle uscite video, Intel iGPU only) e opzioni del BIOS
    - MSI e Gigabyte:
      - sono motherboard con un memory layout non nativamente compatibile con macOS e richiedono patch per funzionare correttamente in termini di memory layout, mappatura delle porte USB e mappatura delle uscite video (Intel iGPU only)

- GPU: [lista compatibilità su hackintoshitalia.it](https://www.hackintoshitalia.it/guide/gpu-compatibility)
- Schede WiFi/BT: [lista compatibilità su hackintoshitalia.it](https://www.hackintoshitalia.it/guide/network-compatibility)

Dalla lista compatibilità, sono esclusi i laptop dotati di scheda grafica dedicata, qualunque essa sia, a causa dell'incompatibilità delle tecnologie di switching grafico (Optimus ecc) con macOS.

## Quale bootloader devo usare?

Sono stati creati svariati bootloader per macOS, a partire da iBoot, Chameleon, Clover, per infine arrivare ad OpenCore: un bootloader open source scritto dal team [acidanthera](https://github.com/acidanthera).
E' probabilmente il bootloader con la migliore documentazione in circolazione, nonchè con meccanismi di patching per niente "aggressivi" che può essere usato per avviare un Mac vero.

Il gruppo fornisce supporto solo ed esclusivamente ad EFI realizzate con OpenCore di acidanthera, ergo nessun fork. 

## Cos'è il `Power Management`?

Con questo termine generalmente ci si riferisce alla gestione delle risorse energetiche del PC in situazioni di stress (task intensivi) e situazioni di idle (riposo). Una errata configurazione del power management può risultare in consumi e temperature elevati in situazioni apparentemente di riposo, nonchè performance castrate.

Per ovviare a questo problema il primo consiglio è selezionare un SMBIOS appropriato per la propria configurazione hardware.

## Come posso creare una chiavetta USB con macOS?

- Per Windows/Linux cliccare [qui](https://www.hackintoshitalia.it/guide/usb-windows)
- Per macOS cliccare [qui](https://www.hackintoshitalia.it/guide/usb-mac)

**NON SONO SUPPORTATE DISTRO/INSTALLER MODIFICATI COME UNIBEAST O OLARILA**

Vi fidereste a scaricare un sistema operativo che potete tranquillamente ottenere dai server Apple in maniera legittima, da fonti terze?
Metodi come Unibeast/Multibeast vanno contro il principio dell'installazione di macOS vanilla, ossia priva di modifiche da parte di terzi, così come distro quali Olarila/HackintoshZone/iATKOS ecc.

## Mi sono perso... Cosa mi serve per fare un Hackintosh?
Per realizzare un hackintosh occorrono:

0. Conoscenze basilari di un computer:
   - come accendere un computer
   - come avviare il BIOS/Boot menu
   - come aprire un terminale e navigare fra i file di sistema
1. Un hardware compatibile con macOS
2. Un bootloader propriamente configurato come OpenCore
3. Una chiavetta USB con capienza da almeno 2 GB (nel caso di installer via internet) o 16 GB (nel caso di installer completo)
4. Un PC con Windows/Linux (per installer via internet) o un Mac (per installer completo)
5. Almeno 128GB di spazio su disco per installare macOS. E' altamente consigliato optare per un disco aggiuntivo, per evitare problemi con dual boot

## Una volta creata la chiavetta USB cosa devo fare?

Scrivere `/OPENCORE` [nel gruppo Telegram](https://t.me/Hackintoshitalia).

Guida inserimento Kext in EFI(https://macos86.gitbook.io/guida-opencore/varie/varie/kexts)

Kext necessari di default:
- [VirtualSMC](https://github.com/acidanthera/VirtualSMC/releases)
- [Lilu](https://github.com/acidanthera/Lilu/releases)
- [Whatevergreen](https://github.com/acidanthera/WhateverGreen/releases)
- [AppleALC](https://github.com/acidanthera/AppleALC/releases)
- Kext di [rete](https://dortania.github.io/OpenCore-Install-Guide/ktext.html#ethernet) o per il [WiFi/Bluetooth](https://dortania.github.io/OpenCore-Install-Guide/ktext.html#wifi-and-bluetooth)
- [NVMefix](https://github.com/acidanthera/NVMeFix/releases) per i dischi NVMe compatibili con macOS
- [Kext specifici per laptop](https://dortania.github.io/OpenCore-Install-Guide/ktext.html#laptop-specifics)

## Che cos'è la EFI e come si monta?

Per `EFI` (`Extensible Firmware Interface`) generalmente ci si riferisce ad una partizione o ad un dispositivo di storage contenente i file necessari al boot di un dato sistema operativo. Nel caso di Hackintosh, OpenCore.

- Nel caso di chiavette create col metodo `Internet Recovery Install`, basterà aprire con un gestore file il contenuto della chiavetta USB.
- Nel caso di chiavette create col metodo `Full Install` (possibile solo su macOS) occorrerà utilizzare un terminale (vedi `diskutil list` e `diskutil mount`) oppure usare software come [TINU](https://github.com/ITzTravelInTime/TINU) o [MountEFI](https://github.com/corpnewt/MountEFI)

## Troppo casino... Potete aiutarmi nel processo di creazione della EFI nonchè installazione di macOS?

Ti capiamo... Non è semplice dover assimilare tutte queste nozioni in poco tempo. Fortunatamente il team di HackintoshItalia è più che preparato per aiutarti.

Per richiedere assistenza, digita `/ASSISTENZA` [nel gruppo Telegram](https://t.me/Hackintoshitalia).

**N.B. NON RISPONDEREMO A RICHIESTE INVIATE IN PRIVATO/VIA ALTRI SISTEMI DI COMUNICAZIONE**

## Crediti

- Apple per macOS
- Acidanthera per OpenCore
- Hackintosh Italia per l'aiuto dato
- Utopia Team per la EFI utilizzata per il SysReport
- Dortania per le guide
- macOS86 per le guide scritte sul loro forum
