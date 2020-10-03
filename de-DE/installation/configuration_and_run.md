---
name: Konfiguration und Start
---

# Konfiguration und Start

## Konfiguration

### Standard-Konfiguration

Die Standard-Konfiguration ist in `conf/app.ini` gespeichert. Du brauchst diese Datei **NICHT** verändern, seit `v0.6.0` ist das im Programm eingebunden.

### Manuelle Konfiguration

Wie macht man nun eigene Änderungen, wenn man die `conf/app.ini` nicht verändern darf? Erstelle einfach eine `custom/conf/app.ini`! Die entsprechenden Schlüssel in den entsprechenden Sektionen werden die Werte aus `conf/app.ini` überschreiben.

Zum Beispiel kann man, um den Wurzelpfad, in dem die Repository-Rohdaten gespeichert werden, zu verändern, eine Zeile wie die folgende hinzufügen:

```
[repository]
ROOT = /home/jiahuachen/gogs-repositories
```

Natürlich kann man auch die Datenbankeinstellungen ändern

```
[database]
PASSWORD = root
```

### Warum tun wir das?

Ja, warum nicht einfach `conf/app.ini` verändern? Der Grund ist, die eigene Konfiguration sicher zu speichern:

- Alle, die das Programm aus der Binärdateien installieren, können jedes Mal, wenn eine neue Version rauskommt, die Dateien einfach in den Ordner kopieren, ohne etwas neu konfigurieren zu müssen.
- Für alle, die das Programm aus den Quelldateien installieren, haben wir die `custom/conf/app.ini` in der `.gitignore` aus der Versionskontrolle ausgenommen, sodass es keine neue Version erzeugt, wenn man Konfigurationsänderungen macht oder eine neue Version herunterlädt.

## Gogs Server starten

### Für Entwickler

- Setze den Schlüssel `security -> INSTALL_LOCK` auf `true` in der `custom/conf/app.ini`, um Gogs aus den Quelldateien zu starten
- Du kannst Live-Compiling anschalten mit `bra run` im Gogs Quell-Ordner
	- Installation von [bra](https://github.com/Unknwon/bra): ` go get -u github.com/Unknwon/bra`

### Für normalen Einsatz

**Die Skripte liegen im `scripts`-Ordner, aber führe sie immer im Wurzelverzeichnis des Repositorys aus**

- Es gibt einige Wege, Gogs zu starten:
	- Einfach: Nutze einfach `./gogs web`
	- Daemons: siehe [scripts](https://github.com/gogs/gogs/tree/main/scripts) Ordner
- Sieh in `/install` nach, um die erste Konfiguration zu erstellen.
