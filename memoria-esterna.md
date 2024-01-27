### Dispositivi di memoria esterna

Per accedere ai dati contenuti in un dispositivo di memoria esterna da Raspberry Pi hai bisogno di configurarlo.

Installa i driver per i file system più diffusi:
```
sudo apt update
sudo apt install exfat-fuse ntfs-3g hfsplus
```

configura il dispositivo di memoria esterna:
```
sudo tee -a /etc/fstab << EOF
UUID=$(sudo blkid -s UUID -o value /dev/sda1) /mnt/hdd auto defaults,auto,users,rw,nofail,x-systemd.device-timeout=30,umask=000 0 0
EOF
```

e riavvia il sistema operativo per salvare le modifiche:
```
sudo reboot
```
