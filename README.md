# FAQ: come faccio un hackintosh???
Benvenuto! Questa guida è un work in progress. Se vuoi aggiungere qualcosa fai un pool request oppure segnala con un issue

## Mi sono perso... Cosa mi serve per fare un Hackintosh?
Per fare un hackintosh ti servono i seguenti componenti:
- Un hardware compatibile con macOS
- Un bootloader (~~Cl**er~~ oppure OpenCore). Esso richiede:
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