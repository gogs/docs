---
name: aus Quelldateien
---

# Installation aus Quelldateien

## Abhängigkeiten

### Allgemein

- [Go Programming Language](http://golang.org): Version >= 1.8

Wir erstellen einen neuen Benutzer mit dem Namen `git` und installieren alles unter diesem Benutzer:

```sh
sudo adduser --disabled-login --gecos 'Gogs' git
```

### Drittanbieter-Software

Wenn dich interessiert, welche Drittanbieter-Pakete wir benutzen, schaue dir das [gopmfile](https://github.com/gogs/gogs/blob/master/.gopmfile). Möglicherweise brauchst du das, wenn du Pakete für Gogs erstellst.

## Go-Installation

Wenn Go auf deinem System schon den Anforderungen entspricht, überspringe diesen Abschnitt.

### Download
Die aktuellen Versionen für dein Betriebssystem findest du auf der offiziellen Seite [golang.org](https://golang.org/dl/)

Installiere Go in `/home/git/local/go`, sodass es keine Konflikte mit zukünftigen Updates des Paketmanagers gibt:

```sh
# Zum Benutzer `git` wechseln
sudo su - git
cd ~
# einen Ordner erstellen, um 'go' zu installieren
mkdir local
# go herunterladen (ändere go$VERSION.$OS-$ARCH.tar.gz zur aktuellsten Version)
wget https://storage.googleapis.com/golang/go$VERSION.$OS-$ARCH.tar.gz
# Archiv in ~/local entpacken
tar -C /home/git/local -xzf go$VERSION.$OS-$ARCH.tar.gz
```

### Umgebung einrichten

Pfade entsprechend deinem System einrichten:

```sh
sudo su - git
cd ~
echo 'export GOROOT=$HOME/local/go' >> $HOME/.bashrc
echo 'export GOPATH=$HOME/go' >> $HOME/.bashrc
echo 'export PATH=$PATH:$GOROOT/bin:$GOPATH/bin' >> $HOME/.bashrc
source $HOME/.bashrc
```

### Installation von Gogs

Der allgemeine Weg um Go zu installieren:

```sh
# Abhängigkeiten herunterladen und installieren
$ go get -u github.com/gogs/gogs

# Hauptprogramm erstellen
$ cd $GOPATH/src/github.com/gogs/gogs
$ go build
```

Wenn du gopm installiert hast, kannst du Gogs auch wie folgt installieren:

```sh
# gopm auf Updates überprüfen
$ gopm update -v

# Herunterladen und erstellen der Binärdatei
$ gopm bin -u -v gogs -d path/to/anywhere
```

### Build aus dem `develop`-Branch

Falls du den `develop`-branch ausprobieren möchtest:

```sh
$ mkdir -p $GOPATH/src/github.com/gogs
$ cd $GOPATH/src/github.com/gogs

# Sicherstellen dass du nicht "https://github.com/gogs/gogs.git" benutzt
$ git clone --depth=1 -b develop https://github.com/gogs/gogs
$ cd gogs
$ go get -u ./...
$ go build
```

### Testen der Installation

Um zu testen, ob Gogs funktioniert:

```sh
cd $GOPATH/src/github.com/gogs/gogs
./gogs web
```

Wenn du keine Fehlermeldungen siehst, drücke `Ctrl-C` um Gogs wieder zu stoppen.

### Build mit Tags

Einige Dinge sind nicht automatisch bei Gogs mit dabei, du musst Gogs mit den entspechenden [build tags](https://golang.org/pkg/go/build/#hdr-Build_Constraints) kompilieren.

Verfügbare Build-Tags sind:

- `sqlite`/`tidb`: SQLite3/TiDB-Datenbank-Unterstützung
- `pam`: PAM-Authentifizierungs-Support
- `cert`: Unterstützung für selbst-signierte Zertifikate
- `miniwinsvc`: Eingebauter Windows Service Support (alternativ NSSM nutzen um den Service zu erstellen)

**Hinweis** Solltest du TiDB verwenden wollen, folge bitte dieser [Anleitung](https://github.com/pingcap/tidb/blob/master/docs/QUICKSTART.md#pre-requirement)

Beispiel: Wenn du alles mit dabei haben willst, lösche zuerst den Ordner `$GOPATH/pkg/${GOOS}_$GOARCH}/github.com/gogs/gogs` und führe dann folgende Befehle aus:

```sh
$ go get -u -tags "sqlite tidb pam cert" github.com/gogs/gogs
$ cd $GOPATH/src/github.com/gogs/gogs
$ go build -tags "sqlite tidb pam cert"
```

## Weitere Schritte

- [Konfiguration und Start](/docs/installation/configuration_and_run) um fortzufahren
- Für detailliertere Instruktionen, auch um einen Webserver und eine Datenbank aufsetzen, schaue dir die [detaillierten Schritte](/docs/advanced/configuration_for_source_builds) an
