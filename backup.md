### Backup

Puoi utilizzare un software di backup per scrivere un copia incrementale del sistema operativo in esecuzione su un dispositivo di memoria esterna.
Tale copia può essere ripristinata sulla scheda SD utilizzando Raspberry Pi Imager.

Installa image-utils:
```
git clone https://github.com/seamusdemora/RonR-RPi-image-utils ~/.image-utils
sudo install ~/.image-utils/image-* /usr/local/sbin
rm -r ~/.image-utils -f
```

ed effettua il backup iniziale:
```
sudo image-backup --initial /mnt/hdd/backup.img
```

Apri il file di configurazione di cron
```
sudo crontab -e
```

e configura l'esecuzione di un backup incrementale:
```
0 0 * * * /usr/local/sbin/image-backup /mnt/hdd/backup.img | logger
```
