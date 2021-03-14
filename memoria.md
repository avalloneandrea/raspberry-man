### Dispositivi di memoria

Raspbian monta automaticamente le partizioni ext quando colleghi un dispositivo di memoria al Raspberry, ma è possibile configurarlo affinché monti  manualmente le partizioni formattate con file system differenti.
Puoi conoscere i dispositivi di memoria collegati digitando:
```
sudo blkid
```

Installa i driver per i file system più diffusi:
```
sudo apt update
sudo apt install exfat-fuse ntfs-3g hfsplus
```

configura il dispositivo di memoria:
```
sudo blkid | grep <DEV> | awk '{print $3, "/media/hdd", "auto", "defaults,auto,users,rw,nofail,umask=000,x-systemd.device-timeout=30", "0", "0"}' | sudo tee -a /etc/fstab
```

e riavvia il sistema operativo per salvare le modifiche:
```
sudo reboot
```
