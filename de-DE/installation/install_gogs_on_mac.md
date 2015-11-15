---
name: Auf Mac OS
---

# Installation von Gogs auf Mac OS X

> 

## Abhängigkeiten

* [homebrew][]
* [git][]
* [postgresql][]
* [go][]
* [gopm][]

## Installation

### Homebrew

```sh
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

### git

```sh
brew install git
```

### postgresql

```sh
brew install postgresql
```

### go

```
brew install go
```

### gopm

```
go get -u github.com/gpmgo/gopm
```

### gogs
Erstellen aus dem Quellcode:

```sh
go get -u github.com/gogits/gogs
mkdir -p ~/services && cd ~/services
git clone --branch=dev file:///$GOPATH/src/github.com/gogits/gogs
cd gogs
gopm get -v
gopm build -v
```

## Konfiguration

### postgresql

#### postgresql einrichten
```sh
createdb
psql --command "CREATE USER root WITH SUPERUSER PASSWORD 'THE_DB_PASSWORD';"
createdb -O root gogs
```

#### Postgresql Server starten

```sh
cp /usr/local/opt/postgresql/homebrew.mxcl.postgresql.plist ~/Library/LaunchAgents/
launchctl unload ~/Library/LaunchAgents/homebrew.mxcl.postgresql.plist
launchctl load ~/Library/LaunchAgents/homebrew.mxcl.postgresql.plist
```

Oder einfach:

```sh
postgres -D /usr/local/var/postgres
```

### gogs

#### custom/conf/app.ini

Du kannst einen git-Benutzer hinzufügen oder den benutzen, der aktuell eingeloggt ist.
Wenn du einen Benutzer hinzuf[gen willst, um Gogs auszuführen, guck dir http://wiki.freegeek.org/index.php/Mac_OSX_adduser_script an

```sh
# Lege custom-Ordner an
mkdir -p custom/conf
cp conf/app.ini custom/conf
```


```
...

RUN_USER = git

[server]
SSH_PORT = 22

...

[database]
DB_TYPE = postgres
HOST = 127.0.0.1:5432

...

[security]
INSTALL_LOCK = true
SECRET_KEY = YOU_MUST_CHANGE

...
```

## Gogs Server starten

```
cd ~/services/gogs
./gogs web
# open 127.0.0.0:3000
```

Oder füge eine Lauchpad pliste in die Datei `~/Library/LaunchAgents/io.gogs.web.plist` ein.

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple Computer//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
  <key>Label</key>
  <string>io.gogs.web</string>
  <key>ProgramArguments</key>
  <array>
    <string>sh</string>
    <string>-c</string>
    <string>cd /Users/fundon/services/gogs; ./gogs web</string>
  </array>
  <key>RunAtLoad</key>
  <true/>
  <key>KeepAlive</key>
  <true/>
  <key>WorkingDirectory</key>
  <string>/Users/fundon/services/gogs</string>
</dict>
</plist>
```

```sh
launchctl load ~/Library/LaunchAgents/io.gogs.web.plist
```

## SSH-Zugriff

### SSH Konfiguration `/etc/sshd_config` anpassen

```
sudo cp /etc/sshd_config /etc/sshd_config~previous
sudo vi /etc/sshd_config
```

Bearbeite `/etc/sshd_config`

```
PermitRootLogin no

RSAAuthentication yes
PubkeyAuthentication yes

UsePAM no
```

### SSH Server starten

```
Öffne Systemeinstellungen > Freigabe > Remote Login
```

### Andere SSH Artikel

https://help.github.com/categories/ssh/

## <3 Viel Spaß!

## Anderes

* http://gogs.io/docs/intro/

[Homebrew]: http://brew.sh
[git]: http://git-scm.com
[postgresql]: http://www.postgresql.org
[gogs]: http://gogs.io
[gopm]: http://gopm.io
[go]: http://golang.org
