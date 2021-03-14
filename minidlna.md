## MiniDLNA

### Installazione

Installa MiniDLNA:
```
sudo apt update
sudo apt install minidlna
```

### Configurazione

Apri il file di configurazione di MiniDLNA:
```
sudo nano /etc/minidlna.conf
```

e applica le seguenti impostazioni:
```
media_dir=/media/hdd
```

Apri il file di configurazione del kernel:
```
sudo nano /etc/sysctl.conf
```

e applica le seguenti impostazioni:
```
fs.inotify.max_user_watches=100000
```

### Utilizzo

Avvia un browser e inserisci il seguente URL:
```
http://<IP>:8200
```
