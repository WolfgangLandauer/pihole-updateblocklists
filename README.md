# Update Blocklist für Pihole
Quelle: https://github.com/jacklul/pihole-updatelists \
Quellen der Listen (URLs): https://www.technoy.de/lists/blocklists-fuer-pihole/ und https://firebog.net/ 
## Beschreibung
Man kann die Listen manuell in den Settings pflegen oder eine einzige Liste mit allen URLs pflegen und diese automatisch auslesen und die URLs aktualisieren lassen.\
Gleichzeitg werden dann auch die Inhalte der URls, also die einzelnen DNS-Einträge aktualisiert.
## Voraussetzungen
* Pi-hole v5+ installiert
* php-cli >=7.0 und ein paar Erweiterungen (`sudo apt-get install php-cli php-sqlite3 php-intl php-curl`)
* systemd ist optional aber empfohlen
## Installation
`cd ~`

`git clone https://github.com/jacklul/pihole-updatelists.git Pihole-Updatelists` 

`cd Pihole-Updatelists` 

`sudo bash install.sh`

## Konfiguration
Das Skript führt automatisch `pihole updateGravity`aus und sollte daher in der Standardkonfiguration dekativiert werden \
`sudo nano /etc/cron.d/pihole` \

Ein # vor diese Zeile setzen (Die Nummerierung kann anders sein). \
`#49 4   * * 7   root    PATH="$PATH:/usr/local/bin/" pihole updateGravity >/var/log/pihole_updateGravity.log || cat /var/log/pihole_updateGravity.log` \

**Dieser EIntrag sollte nach jedem Pihole Update kontrolloert werden.**

## Zukünftige Updates
`sudo pihole-updatelists --update`

## Deinstallation
wget -O - https://raw.githubusercontent.com/jacklul/pihole-updatelists/master/install.sh | sudo bash /dev/stdin uninstall

## Skript manuell starten
`pihole-updatelists`
