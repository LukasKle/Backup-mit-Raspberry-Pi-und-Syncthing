# Backup-mit-Raspberry-Pi-und-Syncthing
Backup mit Raspberry Pi und Syncthing

## SSH Verbindung
```bash
ssh lukas@raspberrypi.local
```
## upgrade und update
```bash
sudo -s
apt update
apt upgrade -y
```
## rebbot now
```bash
sudo shutdown -r now
sudo reboot now
```
# Automatische updates und co
Cronjob für automatische Updates anlegen
Öffne den Crontab für den Benutzer root (damit Update-Rechte kein Problem sind):

```bash
sudo crontab -e
```
Füge folgende Zeile ganz unten hinzu:
```bash
Code kopieren
0 4 * * * apt update && apt upgrade -y >> /var/log/auto-updates.log 2>&1
```
✅ Bedeutung:

```0 4 * * *``` → Täglich um 04:00 Uhr morgens

```apt update && apt upgrade -y ```→ Sucht nach Updates und installiert sie

```>> /var/log/auto-updates.log ```→ Protokolliert die Aktion in eine Logdatei
## Optional: Auch nicht automatisch installierbare Updates (Reboot etc.)
Wenn du zusätzlich Kernel-Updates etc. automatisch einspielen willst, kannst du auch unattended-upgrades aktivieren.

```bash
sudo apt install unattended-upgrades
sudo dpkg-reconfigure unattended-upgrades
```
