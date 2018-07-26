---
name: FAQs
---

#FAQs

### Einrichtung

#### Was mache ich wenn ein anderer Service auf Port 3000 läuft?

Ändere den Port, auf dem Gogs läuft, wenn es das erste Mal gestartet wird mit:

	./gogs web -port 3001

Dieser Parameter verändert für dich auch den Port in der Installationsseite, nimm also hier einen Port, den du Gogs zuweisen willst.

#### Wie benutze ich NGINX mit Reverse Proxy?

Füge die folgende `server` Sektion in die `http` Sektion in der Datei `nginx.conf` ein und lade die Konfiguration neu:

```
server {
    listen 80;
    server_name git.crystalnetwork.us;

    location / {
        proxy_pass http://localhost:3000;
    }
}
```

##### Wie erstelle ich eine Sub-URL mit NGINX?

Falls du einen Unterpfad für deine Gogs-Instanz brauchst, kannst du die NGINX-Konfiguration wie folgt ändern
(beachte den Suffix `/`):


```
server {
    listen 80;
    server_name git.crystalnetwork.us;

    location /gogs/ {
        proxy_pass http://localhost:3000/;
    }
}
```

Setze dann in deiner Konfiguration `[server] ROOT_URL = http://git.crystalnetwork.us/gogs/`

##### Warum bekomme ich Fehlermeldungen, wenn ich große Dateien hochlade?

Um NGINX zu erlauben, große Dateien in die Repositorys hochzuladen, schau dir bitte [hier](http://stackoverflow.com/a/15021750) (englisch) die Diskussion an. `413` ist ein verbreiteter NGINX-Fehler; füge einfach die folgende zeile in deinem Server-Block ein, um das Problem zu beheben:
```
client_max_body_size 50m;
```

#### Wie benutze ich Apache 2 mit Reverse Proxy?

Stelle sicher, daß die folgenden Apache 2 Module geladen sind: proxy, proxy_http.

`custom/conf/app.ini`:
```
[server]
ROOT_URL = http://git.domain.tld/
...
```
`/etc/apache2/vhost.d/<yourconfig>.conf`:
```
<VirtualHost *:80>
    ...
    ProxyPreserveHost On
    ProxyRequests off
    ProxyPass / http://127.0.0.1:3000
    ProxyPassReverse / http://127.0.0.1:3000
</VirtualHost>
```

##### Wie erstelle ich eine Sub-URL mit Apache 2?

Benutze die folgenden Konfigurations-Vorlagen:

`custom/conf/app.ini`:
```
[server]
ROOT_URL = http://domain.tld/git
...
```
`/etc/apache2/vhost.d/<yourconfig>.conf`:
```
<VirtualHost *:80>
    ...
    <Proxy *>
         Order allow,deny
         Allow from all
    </Proxy>

    ProxyPass /git http://127.0.0.1:3000
    ProxyPassReverse /git http://127.0.0.1:3000
</VirtualHost>
```

Wichtig ist hier, den Schrägstrich nach 3000 wegzulassen.

#### Wie benutze ich lighttpd mit Reverse Proxy?

```
server.modules  += ( "mod_proxy" )
$HTTP["host"] == "git.example.com" {
    proxy.server = ( "" => ( ( "host" => "127.0.0.1", "port" => "3000" ) ) )
}
```

##### Wie erstelle ich eine Sub-URL mit lighttpd?

```
# requires lighttpd 1.4.46 or later
server.modules  += ( "mod_proxy" )
$HTTP["url"] =~ "^/gogs/" {
    proxy.server = ( "" => ( ( "host" => "localhost", "port" => "3000" ) ) )
    proxy.header = ( "map-urlpath" => ( "/gogs/" => "/" ) )
}
```

#### Wie konfiguriere ich HTTPS?

Ändere die folgenden Konfigurations-Optionen in der Datei `custom/conf/app.ini` in dem Bereich, der wie folgt aussieht:

```
[server]
PROTOCOL = https
ROOT_URL = https://try.gogs.io/
CERT_FILE = custom/https/zertifikat.cert
KEY_FILE = custom/https/privater-schluessel.key
```

Wenn du ein selbst-signiertes Zertifikat benutzen möchtest, kannst du das folgende Kommando ausführen, um die Zertifikats- und Schlüssel-Dateien zu erzeugen (stelle sicher, dass du das Programm mit dem Build-Tag `cert` kompilierst oder das offizielle Programm verwendest):

	$ ./gogs cert -ca=true -duration=8760h0m0s -host=myhost.example.com

Möchtest du SSL mit einer Apache 2 Proxykonfiguration nutzen, so konfiguriere gogs für http und Apache 2 für SSL.

#### Wie starte ich Gogs im Offline-Modus/im Intranet?

Um Gogs im Intranet zu starten, ändere die Konfigurationsoption `server -> OFFLINE_MODE` auf `true` in der Datei `custom/conf/app.ini`.

#### Wie erstelle ich eine eigene robots.txt?

Erstelle eine Datei mit dem Namem `robots.txt` im Ordner `custom`

#### Wie starte ich Gogs als Daemon?

Gogs hat einige Drittanbieter-Skripte, die das Starten von Gogs als Daemon unterstützen:

- [init.d/centos](https://github.com/gogs/gogs/blob/master/scripts/init/centos/gogs)
- [init.d/debian](https://github.com/gogs/gogs/blob/master/scripts/init/debian/gogs)
- Systemd in der folgenden Sektion.

#### Wie kann ich Gogs mit Systemd starten?

Es gibt eine [systemd-Vorlage-Datei](https://github.com/gogs/gogs/blob/master/scripts/systemd/gogs.service) im Gogs GitHub Repository. Es benötigt einige Anpassungen um für deine Installation lauffähig zu sein:

1. Ersetze den `start.sh`-Pfad in `ExecStart` mit dem Pfad zu deiner Gogs-Installation.
2. Ersetze auch den Pfad in `WorkingDirectory` mit diesem Pfad.
3. (Optional) Wenn du Gogs mit `MySQL/MariaDB`, `PostgreeSQL`, `Redis` oder `memcached` betreiben willst, entferne den Kommentar vor der entsprechenden `After`-Zeile .

Wenn du deine Änderungen abgeschlossen hast, speichere die Datei im Ordner `/etc/systemd` und starte Gogs mit `sudo systemd restart gogs`.

Den Status des Gogs-Systemd-Services kannst du mittels `sudo systemd status gogs -l` oder mit `sudo journalctl -b -u gogs.service` die journald-Einträge direkt anzeigen lassen

### Administration

#### Wie kann ich Administrator werden?

Der erste registrierte Benutzer mit `ID = 1` ist ein Administrator. Eine e-Mail-Bestätigung ist dafür nicht erforderlich (selbst wenn sie eingeschaltet ist). Der Standard-Administrator kann unter `Admin` > `Users` andere Benutzer autorisieren. Registriert sich der Benutzer auf der Installationsseite, wird er auch automatisch zum Administrator.

### Repository-Management

#### Wie gewähre ich Benutzern Git-Hook-Berechtigungen?

Das ist eine **hohes Berechtigungs-Level, das das System beschädigen kann**. Deshalb muss es vom Administrator-Panel gegeben werden (`/admin/users/:userid`). Gewähre diese Berechtigung nur Benutzern, denen du wirklich vertraust.

### Anderes

#### Wie finde ich heraus, welche Version von Gogs ich benutze?

Die aktuelle Version steht als einfacher Text in der Datei `templates/.VERSION`

#### Wofür ist das `gogs serv` Kommando?

Es gibt keinen Grund, diesen Befehl manuell auszuführen. Es wird von git update hooks aufgerufen, sobald ein neuer SSH-Push ankommt.
