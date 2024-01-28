## JDownloader

Puoi gestire il download di file multimediali da Raspberry Pi installando JDownloader:
```
sudo apt update
sudo apt install openjdk-8-jre-headless
mkdir -p ~/.jdownloader/folderwatch
curl http://installer.jdownloader.org/JDownloader.jar -o ~/.jdownloader/JDownloader.jar
java -jar ~/.jdownloader/JDownloader.jar -norestart
```

Imposta l'account MyJDownloader:
```
java -jar ~/.jdownloader/JDownloader.jar -norestart
Email: <EMAIL>
Password: <PASSWORD>
CTRL+C
```

Apri il file di configurazione di JDownloader:
```
nano ~/.jdownloader/cfg/org.jdownloader.settings.GeneralSettings.json
```

e applica le seguenti impostazioni:
```
"defaultdownloadfolder" : "/mnt/hdd",
"downloadspeedlimitenabled" : false,
"autostartdownloadoption" : "ALWAYS",
"cleanupafterdownloadaction" : "CLEANUP_ONCE_AT_STARTUP",
"iffileexistsaction" : "SKIP_FILE",
```

Imposta l'avvio automatico:
```
sudo tee /etc/systemd/system/jdownloader.service << EOF
[Unit]
Description=JDownloader
After=network-online.target mnt-hdd.mount

[Service]
User=pi
Group=pi
UMask=000
Type=simple
RemainAfterExit=yes
ExecStart=/usr/bin/java -jar /home/pi/.jdownloader/JDownloader.jar
Restart=on-failure

[Install]
WantedBy=multi-user.target
EOF
sudo systemctl enable jdownloader
sudo systemctl start jdownloader
```

Avvia un browser, inserisci il seguente URL:
```
https://my.jdownloader.org
```

e autenticati utilizzando le credenziali dell'account MyJDownloader.

Premi il pulsante `Settings`, poi il pulsante `Extension Manager`, e infine il pulsante `Install` e il pulsante `Enable` alla voce `Folder Watch`.
