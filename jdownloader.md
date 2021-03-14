### JDownloader

#### Installazione

Attiva un nuovo account MyJDownloader al seguente URL:
```
https://my.jdownloader.org
```

Installa JDownloader:
```
sudo apt update
sudo apt install openjdk-8-jre-headless
mkdir -p ~/.jdownloader/folderwatch
curl http://installer.jdownloader.org/JDownloader.jar -o ~/.jdownloader/JDownloader.jar
java -jar ~/.jdownloader/JDownloader.jar -norestart
```

e inserisci le credenziali dell'account appena attivato:
```
java -jar ~/.jdownloader/JDownloader.jar -norestart
Email: <EMAIL>
Password: <PASSWORD>
```

#### Configurazione

Apri il file di configurazione di JDownloader:
```
nano ~/.jdownloader/cfg/org.jdownloader.settings.GeneralSettings.json
```

e applica le seguenti impostazioni:
```
"defaultdownloadfolder" : "/media/hdd",
"downloadspeedlimitenabled" : true,
"downloadspeedlimit" : 0,
"autostartdownloadoption" : "ALWAYS",
"cleanupafterdownloadaction" : "CLEANUP_ONCE_AT_STARTUP",
"iffileexistsaction" : "SKIP_FILE",
```

Imposta l'avvio automatico di JDownloader:
```
sudo tee /etc/systemd/system/jdownloader.service<<EOF
[Unit]
Description=JDownloader
After=network-online.target media-hdd.mount

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

#### Utilizzo

Avvia un browser, inserisci il seguente URL:
```
https://my.jdownloader.org
```

e autenticati utilizzando le credenziali dell'account MyJDownloader:
```
Email: <EMAIL>
Password: <PASSWORD>
```

Premi il pulsante \texttt{Settings}, seleziona la voce \texttt{Extension Manager} e applica le seguenti impostazioni:
```
Folder Watch: Install
Folder Watch: Enable
```
