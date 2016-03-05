---
name: Installation
---

## Abhängigkeiten:

- Datenbank (wähle eine der folgenden)
    - [MySQL](http://dev.mysql.com): Version >= 5.5.3
    - [PostgreSQL](http://www.postgresql.org/)
    - oder **KEINE** mit SQLite3 or TiDB (experimentell)
- [Git](http://git-scm.com/) (bash):
    - Version >= 1.7.1 sowohl für den Server als auch für Clients
    - Am besten die neuste Version für Windows benutzen
- Ein funktionierender SSH-Server:
    - **Ignoriere das, wenn du Gogs nur mit HTTP/HTTPS benutzen willst**
    - Empfohlen: [Cygwin OpenSSH](http://docs.oracle.com/cd/E24628_01/install.121/e22624/preinstall_req_cygwin_ssh.htm) oder [Copssh](https://www.itefix.net/copssh) für Windows.

### Installation der Datenbank

Gogs unterstützt MySQL, PostgreSQL, SQLite3 und TiDB. Je nach dem , wofür du dich entscheidest, installiere die jeweilige Datenbank oder überspringe diesen Schritt.

 - [MySQL](http://dev.mysql.com/downloads/mysql/) (Engine: INNODB)
 - [PostgreSQL](http://www.postgresql.org/download/)

**WICHTIG** Benutze `etc/mysql.sql` um eine Datenbank mit dem Namen `gogs` anzulegen (das ist der Standard-Name). Erzeugst du sie manuell, stelle sicher, dass das Encoding auf `utf8mb4` gesetzt ist.

### Andere Abhängigkeiten installieren

#### Mac OS X

Angenommen, du hast [Homebrew](http://brew.sh/) schon installiert:

```
$ brew update
$ brew install git
```

#### Debian/Ubuntu

```
$ sudo apt-get update
$ sudo apt-get install git
```

#### Windows

[Downloade und installiere Git](http://git-scm.com/downloads)

## Installation von Gogs

- [Installation über Binärdatei](/docs/installation/install_from_binary)
- [Installation über Quellcode](/docs/installation/install_from_source)
