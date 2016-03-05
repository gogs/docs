---
name: Detaillierte Konfiguration aus den Quellen
---

# Detaillierte Konfiguration für Erstellung aus den Quelldateien

Folge den Anweisungen zum Erstellen [aus den Quellen](/docs/installation/install_from_source), du solltest dann einen lokalen Benutzer `git` und ein funktionierendes Setup von `go` und [Gogs](http://gogs.io/) haben.
Wir werden Gogs mit **Nginx** installieren. Bei diesem Weg werden wir die Vorteile von Nginx nutzen. Das ist auf Servern, auf denen Nginx schon läuft sehr hilfreich.

Für den Rest dieses Dokuments werden wir folgendes annehmen:

- Du möchtest 'Gogs' auf der Domain 'example.com' ausliefern
- Nginx ist dein Webserver
- `postgresql` ist dein Datenbankserver
- Du möchtest, dass alle deine Git-URL wie `git.example.com` aussehen.

Wie schon in [Konfiguration und Start](/docs/installation/configuration_and_run) erwähnt, solltest du deine eigene Konfigurationsdatei in `$GOPATH/src/github.com/gogits/gogs/custom/conf/app.ini` anlegen.

Als ersten Schritt legen wir einige Ordner an:

```bash
sudo mkdir -p /var/log/gogs
sudo chown git:git /var/log/gogs
sudo su - git
cd ~
mkdir -p $GOPATH/src/github.com/gogits/gogs/custom/conf
mkdir -p ~/gogs-repositories
```

Kopiere jetzt die Standard-Konfigurationsdatei, sodass du sie editieren kannst:

```bash
cd $GOPATH/src/github.com/gogits/gogs
cp conf/app.ini custom/conf/
```

Öffne jetzt in deinem Editor die Datei

`$GOPATH/src/github.com/gogits/gogs/custom/conf/app.ini`

Zum Beispiel:

```bash
vim $GOPATH/src/github.com/gogits/gogs/custom/conf/app.ini
```

## Server aufsetzen

Beginnend vom Anfang, ändere die folgenden Schlüssel in den verschiedenen Sektionen:

### Standard-Sektion

```
RUN_USER=git
```

### `[repository]` Sektion

```
ROOT=/home/git/gogs-repositories
```

### `[server]` Sektion

```
DOMAIN = example.com
ROOT_URL = %(PROTOCOL)s://git.%(DOMAIN)s/
HTTP_ADDR = localhost
HTTP_PORT = 3000
```

## `postresql` einrichten

Unter `Debian`/`Ubuntu` kannst du PostgreSQL installieren mit:

```bash
sudo apt-get install -y postgresql postgresql-client libpq-dev
```

Unter OSX benutze `brew`:

```
brew install postgresql
```

Jetzt richten wir eine Datenbank ein, auf die der `git` Benutzer zugreifen kann:

Erstmal logge dich in psql ein:

```bash
# Login to PostgreSQL
sudo -u postgres psql -d template1
```

Danach, in der PostgreSQL-Prompt, gib ein:

```sql
# Erstelle einen User für git
# Das folgende wird in den Prompt geschrieben
CREATE USER git CREATEDB;

# Setze ein Passwort fuer git
# Merke dir das Passwort fuer den naechsten Schritt
\password git

# Erstelle die Datenbank und gib alle Rechte an git
CREATE DATABASE gogs_production OWNER git;

#Schließe die Datenbanksitzung
\q

#Versuche dich mit dem neuen User zu verbinden
sudo -u git -H psql -d gogs_production

# Und schließe die Datenbanksitzung wieder
gogs_production> \q
```

Jetzt können wir `app.ini` anpassen. öffne also `$GOPATH/src/github.com/gogits/gogs/custom/conf/app.ini` in deinem Editor und ändere das folgende (stelle dabei sicher, dass du gerade der User `git` bist, falls nicht, gib vorher noch `sudo su - git` ein):

### `[database]` Sektion

```ini
DB_TYPE = postgres
HOST = 127.0.0.1:5432
NAME = gogs_production
USER = git
PASSWD =__postgresql_passwort_aus_vorherigem_schritt__
PATH = data/gogs.db
```

## Nginx-Server einrichten

Wenn noch nicht installiert, installiere Nginx unter `Debian`/`Ubuntu` mit:

```bash
sudo apt-get install -y nginx
```

Jetzt erstellen wir eine Nginx-Konfiguration für unser Gogs:

```bash
sudo su - git
# Benutze deinen Editor und erstelle eine temporäre Datei
vim /tmp/gogs
```
Und füge dann folgendes ein:

```
server {
    listen 80;
    server_name git.example.com;

    location / {
        proxy_pass http://localhost:3000;
    }
}
```

Füge diese Datei nun Nginx hinzu und starte Nginx neu.

```bash
sudo mv /tmp/gogs /etc/ningx/sites-available
sudo ln -s /etc/nginx/sites-available/gogs /etc/ningx/sites-enabled/gogs
sudo service nginx restart
```
Danach:

```bash
sudo su - git
cd $GOPATH/src/github.com/gogits/gogs
./gogs web
```

Öffne jetzt in deinem Webbrowser die URL `git.example.com`

Natürlich wirst du, falls du das initiale Setup noch nicht durchgeführt hast, jetzt die Installationsseite angezeigt bekommen:

![installation page screenshot](/docs/images/installation_page_screenshot.png)

Ändere den **Datenbank-Typ** auf *PostgreSQL*, falls es nicht schon ausgewählt ist. Nach dem du überprüft hast, dass alle Einstellungen denen entsprechen, die du in der `app.ini` gesetzt hast, klicke auf installieren und freue dich über deine neue Git Webseite!

Grundsätzlich bist du an dieser stelle fertig, die nächsten Schritte beschreiben, wie man Gogs startet wenn `Debian`/`Ubuntu` neu gestartet werden.

### Gogs zu `init.d` hinzufügen

Diese Sektion beschreibt, wie man *Gogs* startet, wenn das Linux-System neu gestartet wird. Für andere Plattformen gucke die Dokumentation durch, um herauszufinden, wie du das tun kannst. Für Mac OSX schaue dir [dieses Dokument](/docs/installation/install_gogs_on_mac#run-gogs-server) um Autostart-Programme zu verwalten

Wenn du den vorherigen Schritten gefolgt bist, kannst du jetzt das automatische Starten von gogs aktivieren. Unter `Debian`/`Ubuntu` werden wir das Skript aus `$GOPATH/src/githb.com/gogits/gogs/scripts/init/debian/gogs` benutzen.

Kopieren wir also die Datei und verändern sie:

```bash
sudo su - git
cd ~
cp $GOPATH/src/github.com/gogits/gogs/scripts/init/debian/gogs ./gogs.init
```

Editiere jetzt die Datei `~/gogs.init` wie folgt:

- Ändere die zwei Zeilen oben:

```ini
# Required-Start:   $syslog $network
# Required-Stop:    $syslog
```

zu

```ini
# Required-Start:   $syslog $network $local_fs nginx postgresql
# Required-Stop:    $syslog $local_fs
```

Weiter unten in der gleichen Datei setze den Pfad, sodass `init.d` unsere `gogs`-Installation finden kann, indem wir die `WORKING_DIR` Zeile ändern zu:

```ini
WORKING_DIR=/home/git/go/src/github.com/gogits/gogs
```

Verschiebe die Datei nach `/etc/init.d` und update es:

```bash
#erstmal wieder zum normalen Benutzer werden. wenn nicht schon geschehen
exit

sudo mv /home/git/gogs.init /etc/init.d/gogs
sudo chmod ug+x /etch/init.d/gogs
sudo update-rc.d gogs defaults 30 70
```

Teste dein Setup jetzt mit

```sudo service gogs start```

und besuche die URL deiner Seite (z,B. `git.example.com`)

Wenn du Gogs mit `systemd` starten willst, schaue dir den [entsprechenden FAQ](/docs/intro/faq#systemd-service) an.
