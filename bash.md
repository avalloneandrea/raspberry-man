### Bash

Apri il file di configurazione di Bash:
```
nano ~/.bashrc
```

applica le seguenti impostazioni:
```
alias cpu="LC_ALL=C top -bn2 | grep 'Cpu(s)' | tail -n1 | awk '{print \"cpu=\" 100-\$8 \"%\"}'"
alias mem="free -m | grep 'Mem' | awk '{print \"mem=\" \$3 \"MB\"}'"
alias temp="/opt/vc/bin/vcgencmd measure_temp"
status() { systemctl list-units -a | grep $1 | awk '{print $1,$4}' | sed 's/\W.*\s/=/g' ; }
alias mon="cpu && mem && temp && status hdd.mount && status ssh.service && status vncserver-x11-serviced.service && status amule.service && status deluge.service && status delugeweb.service && status jdownloader.service && status flexget.service && status minidlna.service && status kodi.service"
```

e riavvia Bash per salvare le modifiche:
```
exec bash
```

Da adesso in poi digita
- `cpu` per ottenere l'utilizzo del processore,
- `mem` per ottenere l'utilizzo della memoria,
- `temp` per ottenere la temperatura,
- `status` per ottenere lo stato di un servizio, oppure
- `mon` per ottenere tutte le suddette informazioni.
\end{inparaenum}
