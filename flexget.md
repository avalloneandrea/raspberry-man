### FlexGet

#### Installazione

Installa FlexGet:
```
sudo pip install flexget deluge-client subliminal
```

#### Configurazione

Configura l'interfaccia web di FlexGet:
```
mkdir -p ~/.flexget
tee ~/.flexget/config.yml<<EOF
tasks: {}
templates: {}
web_server: yes
EOF
flexget web passwd raspberyy
```

Imposta l'avvio automatico di FlexGet:
```
sudo tee /etc/systemd/system/flexget.service<<EOF
[Unit]
Description=FlexGet
After=network-online.target media-hdd.mount

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

#### Utilizzo

Avvia un browser, inserisci il seguente URL:
```
http://<IP>:5050
```

e autenticati utilizzando le credenziali di default:
```
Password: raspberyy
```
