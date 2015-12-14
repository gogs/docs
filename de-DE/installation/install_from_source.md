---
name: aus Quelldateien
---

# Installation aus Quelldateien

## Abhängigkeiten

### Generell

- [Go Programming Language](http://golang.org): Version >= 1.4

Wir erstellen einen neuen Benutzer mit dem Namen `git` und installieren alles unter diesem Benutzer:

```sh
sudo adduser --disabled-login --gecos 'Gogs' git
```

### Drittanbieter-Software

Wenn dich interressiert, welche Drittanbieter-Pakete wir benutzen, schaue dir das [gopmfile](https://github.com/gogits/gogs/blob/master/.gopmfile). Möglicherweise brauchst du das, wenn du Pakete für Gogs erstellst.

## Go-Installation

Wenn Go auf deinem System schon den Anforderungen entspricht, überspringe diese Sektion bitte.

### Download

Installiere Go in `/home/git/local/go`, sodass es keine Konflikte mit zukünftigen Updates des Paketmanagers gibtÖ

```sh
sudo su - git
cd ~
# create a folder to install 'go'
mkdir local
# Download go (change go$VERSION.$OS-$ARCH.tar.gz to the latest realse)
wget https://storage.googleapis.com/golang/go$VERSION.$OS-$ARCH.tar.gz
# expand it to ~/local
tar -C /home/git/local -xzf go$VERSION.$OS-$ARCH.tar.gz
```

### Umgebung einrichten

Setzen der Pfade entsprechend deinem System:

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
# Download and install dependencies
$ go get -u github.com/gogits/gogs

# Build main program
$ cd $GOPATH/src/github.com/gogits/gogs
$ go build
```

Wenn du gopm hast, kannst du den folgenden Weg ausprobieren:

```sh
# Check update of gopm
$ gopm update -v

# Download and build binary
$ gopm bin -u -v gogs -d path/to/anywhere
```

### Build aus dem `develop`-Branch

Falls du den `develop`-branch ausprobieren möchtest:

```sh
$ mkdir -p $GOPATH/src/github.com/gogits
$ cd $GOPATH/src/github.com/gogits

# Make sure you don't use "https://github.com/gogits/gogs.git"
$ git clone --depth=1 -b develop https://github.com/gogits/gogs
$ cd gogs
$ go get -u ./...
$ go build
```

### Testen der Installation

Um zu testen, das Gogs funktioniert:

```sh
cd $GOPATH/src/github.com/gogits/gogs
./gogs web
```

Wenn du keine Fehlermeldungen siehst, drücke `Ctrl-C` um Gogs wieder zu stoppen.

### Build mit Tags

Einige Dinge sind nicht automatisch bei Gogs mit dabei, du musst Gogs mit den entspechenden [build tags](https://golang.org/pkg/go/build/#hdr-Build_Constraints) kompilieren.

Verfügbare Build-Tags sind:

- `sqlite3`/`tidb`: SQLite3/TiDB-Datenbank-Unterstützung
- `pam`: PAM-Authentifizierungs-Support
- `cert`: Unterstützung für selbst-signierte Zertifikate

Beispiel: Wenn du alles mit dabei haben wilst, lösche zuerst den Ordner `$GOPATH/pkg/${GOOS}_$GOARCH}/github.com/gogits/gogs` und führe dann aus:

```sh
$ go get -u -tags "sqlite tidb pam cert" github.com/gogits/gogs
$ cd $GOPATH/src/github.com/gogits/gogs
$ go build -tags "sqlite tidb pam cert"
```

## Weitere Schritte

- [Konfiguration und Start](/docs/installation/configuration_and_run) für tiefergehende Informationen
- Für detailliertere Instruktionen, darin enthalten Webserver und Datenbank aufsetzen, schaue dir die [detaillierten Schritte](/docs/advanced/configuration_for_soruce_builds) an
