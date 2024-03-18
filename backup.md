## Backup

Puoi effettuare una copia di backup del sistema operativo in esecuzione su un dispositivo di memoria esterna installando image-utils:
```
git clone https://github.com/seamusdemora/RonR-RPi-image-utils ~/.image-utils
sudo install ~/.image-utils/image-* /usr/local/sbin
rm -r ~/.image-utils -f
```

Effettua il backup iniziale:
```
sudo image-backup --initial /mnt/hdd/backup.img
```

Apri il file di configurazione di cron:
```
sudo crontab -e
```

e configura l'esecuzione di un backup incrementale:
```
0 0 * * SAT /usr/local/sbin/image-backup /mnt/hdd/backup.img
```

Puoi ripristinare la copia di backup prodotta da image-utils utilizzando Raspberry Pi Imager.