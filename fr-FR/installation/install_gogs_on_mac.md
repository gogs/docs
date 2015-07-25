---
name: Sous Mac OS
sort: 5
---

## Installation de Gogs sur Mac OS X

> Contribution par [@fundon](https://github.com/fundon)

## Dépendances

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
Construire à partir de la source de dev.

```sh
go get -u github.com/gogits/gogs
mkdir -p ~/services && cd ~/services
git clone --branch=dev file:///$GOPATH/src/github.com/gogits/gogs
cd gogs
gopm get -v
gopm build -v
```

## Configuration

### postgresql

#### Init postgresql
```sh
createdb
psql --command "CREATE USER root WITH SUPERUSER PASSWORD 'THE_DB_PASSWORD';"
createdb -O root gogs
```

#### Start postgresql server

```sh
cp /usr/local/opt/postgresql/homebrew.mxcl.postgresql.plist ~/Library/LaunchAgents/
launchctl unload ~/Library/LaunchAgents/homebrew.mxcl.postgresql.plist
launchctl load ~/Library/LaunchAgents/homebrew.mxcl.postgresql.plist
```

Ou tout simplement de fonctionner

```sh
postgres -D /usr/local/var/postgres
```

### gogs

#### custom/conf/app.ini

Vous pouvez ajouter un utilisateur git ou utiliser utilisateur actuellement connecté.
Si vous souhaitez ajouter un utilisateur git pour exécuter Gogs, voir http://wiki.freegeek.org/index.php/Mac_OSX_adduser_script.

```sh
# Create custom folder
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

## Exécuter le serveur Gogs

```
cd ~/services/gogs
./gogs web
# open 127.0.0.0:3000
```

Ou ajouter le fichier de liste lancé à `~/Library/LaunchAgents/io.gogs.web.plist`

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

## Connexion SSH distant

### Réglage de la configuration SSH `/etc/sshd_config`

```
sudo cp /etc/sshd_config /etc/sshd_config~previous
sudo vi /etc/sshd_config
```

Édité `/etc/sshd_config`

```
PermitRootLogin no

RSAAuthentication yes
PubkeyAuthentication yes

UsePAM no
```

### Démarré le serveur SSH

```
Open System Preferences > Sharing > Remote Login
```

### Autres articles sur SSH

https://help.github.com/categories/ssh/

## <3 En joie !

## Autres

* http://gogs.io/docs/intro/

[Homebrew]: http://brew.sh
[git]: http://git-scm.com
[postgresql]: http://www.postgresql.org
[gogs]: http://gogs.io
[gopm]: http://gopm.io
[go]: http://golang.org
