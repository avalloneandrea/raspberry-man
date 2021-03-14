## Kodi

### Installazione

Installa Kodi:
```
sudo apt update
sudo apt install kodi
```

### Configurazione

Apri il file di configurazione del Raspberry:
```
sudo nano /boot/config.txt
```

e applica le seguenti impostazioni:
```
hdmi_force_hotplug=1
hdmi_group=1
hdmi_mode=31
gpu_mem=512
start_x=1
```

Imposta l'avvio automatico di Kodi:
```
sudo tee /etc/systemd/system/kodi.service<<EOF
[Unit]
Description=Kodi
After=network-online.target

[Service]
User=pi
Group=pi
UMask=000
Type=simple
ExecStart=/usr/bin/kodi
Restart=on-failure

[Install]
WantedBy=multi-user.target
EOF
sudo systemctl enable kodi
sudo systemctl start kodi
```

### Utilizzo

Collega un televisore al Raspberry e sintonizzalo sull'uscita HDMI.
