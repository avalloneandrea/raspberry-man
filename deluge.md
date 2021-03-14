## Deluge

### Installazione

Installa Deluge:
```
sudo apt update
sudo apt install deluged deluge-web deluge-console
```

### Configurazione

Apri la console di configurazione di Deluge:
```
deluged
deluge-console
```

e applica le seguenti impostazioni:
```
config -s download_location /media/hdd
config -s autoadd_enable true
config -s autoadd_location /home/pi/Downloads
config -s max_download_speed -1.0
config -s max_upload_speed -1.0
config -s ignore_limits_on_local_network false
config -s allow_remote true
config -s dont_count_slow_torrents true
config -s stop_seed_at_ratio true
config -s share_ratio_limit 2.0
config -s remove_seed_at_ratio true
exit
```

Apri il file di configurazione di Deluge Web:
```
deluge-web --fork
sudo killall deluge-web
sudo killall deluged
nano ~/.config/deluge/web.conf
```

e applica le seguenti impostazioni:
```
"default_daemon": "127.0.0.1:58846",
```

Imposta l'avvio automatico di Deluge:
```
sudo tee /etc/systemd/system/deluge.service<<EOF
[Unit]
Description=Deluge
After=network-online.target media-hdd.mount

[Service]
User=pi
Group=pi
UMask=000
Type=simple
ExecStart=/usr/bin/deluged -d
Restart=on-failure

[Install]
WantedBy=multi-user.target
EOF
sudo systemctl enable deluge
sudo systemctl start deluge
```

Imposta l'avvio automatico di Deluge Web:
```
sudo tee /etc/systemd/system/delugeweb.service<<EOF
[Unit]
Description=Deluge Web
After=network-online.target media-hdd.mount

[Service]
User=pi
Group=pi
UMask=000
Type=simple
ExecStart=/usr/bin/deluge-web
Restart=on-failure

[Install]
WantedBy=multi-user.target
EOF
sudo systemctl enable delugeweb
sudo systemctl start delugeweb
```

### Utilizzo

Avvia un browser, inserisci il seguente URL:
```
http://<IP>:8112
```

e autenticati utilizzando le credenziali di default:
```
Password: deluge
```

Premi il pulsante \texttt{Preferences}, seleziona la voce \texttt{Interface}, applica le seguenti impostazioni e premi il pulsante \texttt{Change}:
```
Old Password: deluge
New Password: raspberry
```
