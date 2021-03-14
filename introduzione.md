### Introduzione

Scarica Raspberry Pi Imager, avvialo, e seleziona una immagine di Raspbian, una scheda SD di almeno 8 GB, e il pulsante _Write_.
Al termine, crea il file `ssh` nella partizione `boot`, senza estensione e senza contenuto.
Espelli la scheda SD, inseriscila nel Raspberry e collega il cavo di alimentazione.

Autenticati utilizzando le credenziali di default:
```
Username: pi
Password: raspberry
```

installa gli aggiornamenti del sistema operativo:
```
sudo apt update
sudo apt upgrade
sudo apt autoremove
sudo apt clean
```

ed esegui la configurazione iniziale:
```
sudo raspi-config
```

Al termine, riavvia il sistema operativo per salvare le modifiche:
```
sudo reboot
```
