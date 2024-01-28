## FlexGet

Puoi automatizzare la ricerca e il download di file multimediali da Raspberry Pi installando Flexget:
```
sudo pip install flexget deluge-client
```

Crea il file di configurazione:
```
mkdir -p ~/.flexget
tee ~/.flexget/config.yml << EOF
tasks: {}
templates: {}
web_server: yes
EOF
flexget web passwd notstrongenough
```

Imposta l'avvio automatico:
```
sudo tee /etc/systemd/system/flexget.service << EOF
[Unit]
Description=FlexGet
After=network-online.target mnt-hdd.mount

[Service]
User=pi
Group=pi
UMask=000
Type=simple
ExecStart=/usr/local/bin/flexget daemon start --autoreload-config
ExecStop=/usr/local/bin/flexget daemon stop
ExecReload=/usr/local/bin/flexget daemon reload
Restart=on-failure

[Install]
WantedBy=multi-user.target
EOF
sudo systemctl enable flexget
sudo systemctl start flexget
```

Avvia un browser, inserisci il seguente URL:
```
http://192.168.1.141:5050
```

e autenticati utilizzando la password di default `notstrongenough`.
