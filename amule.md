## aMule

### Installazione

Installa aMule:
```
sudo apt update
sudo apt install amule-daemon
```

### Configurazione

Apri il file di configurazione di aMule:
```
amuled -f
curl http://upd.emule-security.org/nodes.dat -o ~/.aMule/nodes.dat
curl http://upd.emule-security.org/server.met -o ~/.aMule/server.met
nano ~/.aMule/amule.conf
```

e applica le seguenti impostazioni:
```
[eMule]
MaxUpload=0
MaxDownload=0
TempDir=/media/hdd/Temp
IncomingDir=/media/hdd/Incoming
[ExternalConnect]
AcceptExternalConnections=1
ECAddress=127.0.0.1
ECPassword=b89749505e144b564adfe3ea8fc394aa
[WebServer]
Enabled=1
Password=b89749505e144b564adfe3ea8fc394aa
```

Imposta l'avvio automatico di aMule:
```
sudo tee /etc/systemd/system/amule.service<<EOF
[Unit]
Description=aMule
After=network-online.target media-hdd.mount

[Service]
User=pi
Group=pi
UMask=000
Type=simple
ExecStart=/usr/bin/amuled
Restart=on-failure

[Install]
WantedBy=multi-user.target
EOF
sudo systemctl enable amule
sudo systemctl start amule
```

### Utilizzo

Avvia un browser, inserisci il seguente URL:
```
http://<IP>:4711
```

e autenticati utilizzando le credenziali di default:
```
Password: raspberry
```
