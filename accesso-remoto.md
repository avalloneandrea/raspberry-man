### Accesso remoto

Per accedere a Raspberry Pi da remoto hai bisogno di configurare una connessione di rete. 
Configura la connessione a una rete cablata:
```
sudo tee -a /etc/dhcpcd.conf << EOF
interface eth0
static ip_address=192.168.1.141/24
static routers=192.168.1.1
static domain_name_servers=1.1.1.1
EOF
```

oppure configura la connessione a una rete senza fili:
```
sudo tee -a /etc/wpa_supplicant/wpa_supplicant_test.conf << EOF
$(wpa_passphrase "<SSID>" "<PSK>")
EOF
sudo tee -a /etc/dhcpcd.conf << EOF
interface wlan0
static ip_address=192.168.1.141/24
static routers=192.168.1.1
static domain_name_servers=1.1.1.1
EOF
```

e riavvia il sistema operativo per salvare le modifiche:
```
sudo reboot
```

#### Protocollo SSH

Per accedere da remoto al terminale di Raspberry Pi puoi utilizzare il protocollo SSH.
Avvia `Raspberry Pi Configuration`, seleziona il tab `Interfaces`, poi il pulsante `Enabled` alla voce `SSH` e infine il pulsante `OK`.

Per utilizzare il protocollo SSH avvia un browser, inserisci il seguente URL:
```
ssh://pi@192.168.1.141:22
```

e autenticati utilizzando la password di default `raspberry`.

#### Protocollo VNC

Per accedere da remoto al desktop di Raspberry Pi puoi utilizzare il protocollo VNC.
Avvia `Raspberry Pi Configuration`, seleziona il tab `Interfaces`, poi il pulsante `Enabled` alla voce `VNC` e infine il pulsante `OK`.

Per utilizzare il protocollo VNC avvia un browser, inserisci il seguente URL:
```
vnc://pi@192.168.1.141:5900
```

e autenticati utilizzando la password di default `raspberry`.
