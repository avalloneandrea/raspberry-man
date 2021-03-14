## RealVNC

### Installazione

Installa RealVNC:
```
sudo apt update
sudo apt install realvnc-vnc-server
```

### Configurazione

Apri il file di configurazione di RealVNC:
```
sudo nano /root/.vnc/config.d/vncserver-x11
```

e applica le seguenti impostazioni:
```
Authentication=VncAuth
Password=c3abbea3b003a0b231737c0541892d72
```

Imposta l'avvio automatico di RealVNC:
```
sudo systemctl enable vncserver-x11-serviced.service
sudo systemctl start vncserver-x11-serviced.service
```

### Utilizzo

Avvia un browser, inserisci il seguente URL:
```
vnc://<IP>:5900
```

e autenticati utilizzando le credenziali di default:
```
Password: raspberry
```
