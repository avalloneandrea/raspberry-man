### OpenSSH

#### Installazione

OpenSSH è già installato in Raspbian.

#### Configurazione

Imposta l'avvio automatico di OpenSSH:
```
sudo systemctl enable ssh
sudo systemctl start ssh
```

#### Utilizzo

Avvia un browser, inserisci il seguente URL:
```
ssh://pi@<IP>:22
```

e autenticati utilizzando le credenziali di default:
```
Password: raspberry
```
