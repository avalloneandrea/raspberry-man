### Memoria esterna

Per accedere ai dati contenuti in un dispositivo di memoria esterna da Raspberry Pi hai bisogno di montare il suo file system.

Installa i driver per i file system più diffusi:
```
sudo apt update
sudo apt install exfat-fuse ntfs-3g hfsplus
```

Imposta il montaggio automatico del file system:
```
sudo tee -a /etc/fstab << EOF
UUID=$(sudo blkid -s UUID -o value /dev/sda1) /mnt/hdd auto defaults,auto,users,rw,nofail,x-systemd.device-timeout=30,umask=000 0 0
EOF
```

e riavvia il sistema operativo per salvare le modifiche:
```
sudo reboot
```
