### Interfacce di rete

Raspbian utilizza un server DHCP per ottenere un indirizzo IP dinamico ad ogni avvio, ma è possibile configurare un indirizzo IP statico se accedi spesso da remoto.
Puoi conoscere l'indirizzo attuale digitando:
```
hostname -I
```

Configura l'interfaccia di rete cablata:
```
sudo tee -a /etc/dhcpcd.conf<<EOF
interface eth0
static ip_address=<IP>/24
static routers=192.168.1.1
static domain_name_servers=1.1.1.1
EOF
```

oppure configura l'interfaccia di rete senza fili:
```
wpa_passphrase "<SSID>" "<PSK>" | sudo tee -a /etc/wpa_supplicant/wpa_supplicant.conf
sudo tee -a /etc/dhcpcd.conf<<EOF
interface wlan0
static ip_address=<IP>/24
static routers=192.168.1.1
static domain_name_servers=1.1.1.1
EOF
```

e riavvia il sistema operativo per salvare le modifiche:
```
sudo reboot
```
