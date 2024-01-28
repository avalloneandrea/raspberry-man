### aMule

Puoi accedere alla rete ed2k da Raspberry Pi installando aMule:
```
sudo apt update
sudo apt install amule-daemon
```

Apri il file di configurazione:
```
amuled -f
sudo killall amuled 
curl http://upd.emule-security.org/nodes.dat -o ~/.aMule/nodes.dat
curl http://upd.emule-security.org/server.met -o ~/.aMule/server.met
nano ~/.aMule/amule.conf
```

e applica le seguenti impostazioni:
```
[eMule]
MaxUpload=0
MaxDownload=0
TempDir=/mnt/hdd/Temp
IncomingDir=/mnt/hdd/Incoming
[ExternalConnect]
AcceptExternalConnections=1
ECAddress=127.0.0.1
ECPassword=ef7628c92bff39c0b3532d36a617cf09
[WebServer]
Enabled=1
Password=ef7628c92bff39c0b3532d36a617cf09
```

Imposta l'avvio automatico:
```
sudo tee /etc/systemd/system/amule.service << EOF
[Unit]
Description=aMule
After=network-online.target mnt-hdd.mount

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

Avvia un browser, inserisci il seguente URL:
```
http://192.168.1.141:4711
```

e autenticati utilizzando la password di default `amule`.
