## Deluge

Puoi accedere alla rete torrent da Raspberry Pi installando Deluge:
```
sudo apt update
sudo apt install deluged deluge-web deluge-console
sudo find /usr -path "*/deluge/ui/console/cmdline/commands/config.py" -exec sh -c 'curl https://github.com/deluge-torrent/deluge/commit/2f1c008a26b50ab3487bd03bcabb39347d441f23.patch | patch {}' \;
sudo find /usr -path "*/deluge/core/" -exec sh -c "curl https://github.com/deluge-torrent/deluge/commit/8ff4683780921111f26fe051e0274aac8afe8bf3.patch | grep -v -e urllib -e flag | sed 's/6 +16,8/5 +16,7/' | sed 's/7 +711,7/4 +711,4/' | sed '/tests/d' | patch -F3 --no-backup-if-mismatch -d {}" \;
```

Apri la console di configurazione:
```
deluged
deluge-console
```

e applica le seguenti impostazioni:
```
config -s download_location /mnt/hdd/
config -s max_download_speed -1.0
config -s max_upload_speed -1.0
config -s ignore_limits_on_local_network false
config -s allow_remote true
config -s dont_count_slow_torrents true
config -s stop_seed_at_ratio true
config -s stop_seed_ratio 2.0
config -s remove_seed_at_ratio true
quit
sudo killall deluge-web
```

Imposta l'avvio automatico di Deluge:
```
sudo tee /etc/systemd/system/deluge.service << EOF
[Unit]
Description=Deluge
After=network-online.target mnt-hdd.mount

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
sudo tee /etc/systemd/system/delugeweb.service << EOF
[Unit]
Description=Deluge Web
After=network-online.target mnt-hdd.mount

[Service]
User=pi
Group=pi
UMask=000
Type=simple
ExecStart=/usr/bin/deluge-web -d
Restart=on-failure

[Install]
WantedBy=multi-user.target
EOF
sudo systemctl enable delugeweb
sudo systemctl start delugeweb
```

Avvia un browser, inserisci il seguente URL:
```
http://192.168.1.141:8112
```

e autenticati utilizzando la password di default `deluge`.
