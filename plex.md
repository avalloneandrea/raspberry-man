### Plex

Puoi organizzare e trasmettere i file multimediali da Raspberry Pi installando Plex:
```
echo deb https://downloads.plex.tv/repo/deb public main | sudo tee /etc/apt/sources.list.d/plexmediaserver.list
curl https://downloads.plex.tv/plex-keys/PlexSign.key | sudo apt-key add -
sudo apt update
sudo apt install plexmediaserver
```

Avvia un browser e inserisci il seguente URL:
```
http://192.168.1.141:32400/manage
```
