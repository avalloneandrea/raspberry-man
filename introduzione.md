### Introduzione

Per usare Raspberry Pi hai bisogno di installare un sistema operativo.
Di default, Raspberry Pi avvia il sistema operativo dalla scheda SD.
Scarica e avvia la versione più recente di [Raspberry Pi Imager](https://www.raspberrypi.com/software/), seleziona il tuo modello di Raspberry Pi, il sistema operativo da installare, la scheda SD su cui installarlo, e avvia l'installazione.
Al termine, crea un file `ssh` nella directory radice della scheda SD, senza estensione e senza contenuto.
Espelli la scheda SD, inseriscila nel lettore di schede SD di Raspberry Pi e collega il cavo di alimentazione.

Avvia il terminale e aggiorna il sistema operativo alla versione più recente:
```
sudo apt update
sudo apt upgrade
sudo apt autoremove
sudo apt clean
```

Al termine, riavvia il sistema operativo per salvare le modifiche:
```
sudo reboot
```
