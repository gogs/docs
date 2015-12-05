---
name: unter Windows
---

## Programm-Installation von Gogs auf Windows 7

> Beigetragen von [@victorsegall](https://github.com/victorsegall)

### Vorbereitungen

Lies die allgemeine [Installations-Seite](http://gogs.io/docs/installation/) bevor du hier weitermachst. Du brauchst [Git für Windows](http://git-scm.com/download/win).

Einen SSH-Server brauchst du auf deinem Windows-Rechner nicht, wenn die Gogs-Instanz nur für dich sein soll oder du bloß den HTTP(S)-Service benutzen willst, den Gogs anbietet.

Um Gogs als Service auszuführen benötigst du eines der folgenden Programme:

* Iain Patterson's [nssm.exe](http://nssm.cc/)
* Nick Rozanski's [SRVSTART.EXE](http://rozanski.org.uk/software)
* Microsoft's [Srvany.exe](https://support.microsoft.com/kb/137890)

Diese Anleitung benutzt nssm.exe, ein [Open Source](https://git.nssm.cc/?p=nssm.git) und [öffentliches](https://git.nssm.cc/?p=nssm.git;a=blob_plain;f=README.txt;hb=HEAD) Programm.

Während der Installation wirst du Gogs als der aktuelle Benutzer ausführen und es dann umkonfigurieren, dass es als Service läuft.

Wenn du Gogs über app.ini oder das Webinterface konfigurierst, verwende UNIX-Dateipfade (mit normalem Schrägstrich `/` als Separator) wo es geht. Wenn du einen UNC-Pfad zu einer Netzwerk-Freigabe brauchst, probiere es auf die [Cygwin-Art](https://cygwin.com/cygwin-ug-net/using.html#unc-paths) oder [binde den Pfad als lokales Laufwerk ein](http://www.sevenforums.com/tutorials/49517-map-network-drive.html).

### Als aktueller Benutzer starten

Gogs kann unter dem aktuell angemeldeten Benutzer sofort ohne Konfiguration starten. Entpacke einfach das [Windows-Programm](http://gogs.io/docs/installation/install_from_binary.html) (ZIP-Datei), gehe auf die Kommando-Zeile (CMD) und führe folgendes aus:

```
C:>cd C:\pfad\zu\gogs

C:\pfad\zu\gogs>gogs web
```

Im weiteren Verlauf werden wir davon ausgehen, dass Gogs in `C:\gogs` liegt

Ab diesem Punkt ist Gogs unter `http://127.0.0.1:3000` verfügbar und der Installer wird dich durch die erste Konfiguration zu einer funktionierenden Instanz führen.

### Erster Start

Standardmäßig wird Gogs `C:\Users\dein_benutzername` und `C:\gogs` für Dateioperationen benutzen.

In `C:\gogs` braucht Gogs Schreib-Berechtigungen für:

```
C:\gogs\custom\conf
C:\gogs\data
C:\gogs\log
```

Diese Ordner werden während der Installation angelegt, was zur Annahme führt, dass Gogs Schreibrechte auf `C:\gogs` hatte. Ist dem nicht so, lege die Ordner an, bevor du Gogs das erste mal startest.

Schau dir [Konfiguration und Start](http://gogs.io/docs/installation/configuration_and_run.html) um mehr über `C:\gogs\custom\conf\app.ini` zu lernen. Die Datei wird während der ersten Installation geschrieben.

Gogs wir die Datei `C:\Users\your_username\.gitconfig` mit folgendem Inhalt anlegen:

```
[user]
	name=Gogs
	email = gogitservice@gmail.com
```

Der Inhalt kann [verändert werden, zu immer du möchtest](http://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup), und das sollte auch getan werden. Das ist der User, dem alle deine Git-Operationen zugeordnet werden. Es kann auch pro Repository mit `C:\pfad\zum\repo\.git\config` gesetzt werden.

### Datenbank

Wenn du einen entfernten Datenbankserver benutzt, die [Ubuntu](http://gogs.io/docs/installation/install_gogs_on_ubuntu.html) und [Mac OS](http://gogs.io/docs/installation/install_gogs_on_mac.html) Anleitungen beschreiben die Datenbankeinrichtung, um die gebrauchten Tabellen anzulegen.

Für eine lokale Einfach-User-Gogs-Instanz kannst du Gogs auch erlauben, eine SQLite Datenbank anzulegen, indem du nichts sonst vor dem ersten Start konfigurierst. Das Ergebnis dessen sollte in `C:\gogs\custom\conf\app.ini` so aussehen:

```
[database]
DB_TYPE = sqlite3
HOST = 127.0.0.1:3306
NAME = gogs
USER = root
PASSWD =
SSL_MODE = disable
PATH = data/gogs.db
```

Dort werden alle Gogs-Daten außer den Git-Daten gespeichert. Git-Daten (Repository-Daten, Historie, etc.) wird außerhalb von Gogs im Dateisystem gespeichert, während Gogs eine Zwischenebene bietet, um Issues zu erstellen, die Historie sich anzugucken und Repositories zu konfigurieren.

Aufgrund dessen hat Benutzer-Verwaltung und Authorizierung, die du in Gogs einstellst keinen Effekt auf Git-Operationen die über das Dateisystem passieren.

### Lokal arbeiten

Standardmäßig sind die von Gogs verwaltete Repositories in `C:\Users\dein_benutzername\gogs-repositories`

Diese Einstellung wird in `C:\gogs\custom\conf\app.ini` gesetst durch:

```
[repository]
ROOT=C:/pfad/zu/repositories
```

Dort werden Roh-Repositoryies liegen ohne Arbeitsverzeichnis. Du kannst die Repos über das Dateisystem klonen, z.B. mit git.exe (Benötigt in [Installation](http://gogs.io/docs/installation/), oder mit [TortoiseGit](https://code.google.com/p/tortoisegit/), falls du lieber mit dem Windows-Explorer arbeitest.

Auf der Kommandozeile kannst du z.B. folgendes tun:

```
C:>cd C:\Users\dein_benutzername\Documents\repos

C:\Users\dein_benutzername\Documents\repos>md repo_name

C:\Users\dein_benutzername\Documents\repos>cd repo_name

C:\Users\dein_benutzername\Documents\repos>git.exe clone --progress -v "C:\Users\dein_benutzername\gogs-repositories\dein_gogs_benutzername\repo_name.git" "C:\Users\dein_benutzername\Documents\repos\repo_name"

Cloning into 'C:\Users\your_username\Documents\repos\repo_name'...

done.
```

Wenn du lokal arbeitest, brauchst du nicht alle Git-Operationen über den Gogs Service laufen zu lassen. Gogs wird sich aktualisieren, wenn du deinen Klon des Repos mit `git push` wieder zu seinem Ursprung in `C:\Users\dein_benutzername\gogs-repositories\...` hochlädst. Klone das Repo wenn du ein Arbeitsverzeichnis brauchst, selbst wenn es nur so rumfliegt. Das erlaubt dir, Gogs und die Repositories einfach zu verschieben, ohne dass der Prozess die Arbeitzverzeichnisse beeinflusst.

### Gogs als Service starten

An diesem Punkt solltest du die Datei- und Ordnerberechtigungen reduzieren. Beachte aber die Pfade, zu denen Gogs Schreibzugriff braucht, einschließlich des Gogs Repository `ROOT`-Verzeichnisses.

Die folgende Einstellung in `C:\gogs\custom\conf\app.ini`

```
RUN_USER = COMPUTERNAME$
```

lässt Gogs unter dem Lokalen Systembenutzer starten.

`COMPUTERNAME` ist das, was `echo %COMPUTERNAME%` zurückgibt. Wenn die Rückgabe `USER-PC` ist, dann setze RUN_USER = USER-PC$`.

```
[server]
DOMAIN = gogs
PROTOCOL = http
HTTP_ADDR = 127.0.1.1
HTTP_PORT = 80
OFFLINE_MODE = true
ROOT_URL = http://gogs/
```

Diese Konfiguration verschiebt den Port, auf dem Gogs läuft auf 80 im lokalen Subnetz und konfiguriert den Gogs HTTPd, dass seine virtuelle Domäne "gogs" ist. Das sorgt dafür, dass du keinen Port angeben musst, wenn du Gogs im Webserver aufrufen willst und verhindert Kollisionen mit anderen lokalen Services. Die IP kann irgendetwas im Bereich 127.0.0.2 - 127.254.254.254 sein, solange die nur für Gogs ist.

Um die Netzwerk-Routen zu komplettieren öffne einen Editor als Administrator und füge die folgenden Zeilen in `C:\Windows\System32\drivers\etc\hosts` ein:

```
# Go Git Service local HTTPd
127.0.1.1	gogs
```

Dieser Host-Datei-Eintrg garantiert, dass alle Anfragen an die "gogs"-Domäne an das lokale Interface gehen. In einem Webbrowser ist allgemein `gogs/` in der Adresszeile ausreichend, um auf diese Route zu kommen.

Lade dir jetzt [nssm.exe](http://nssm.cc/download) für deine Maschine herunter (32 oder 64 bit; beide sind im Zip-Archiv) und speichere sie in einem Verzeichnis, dass in der %PATH%-Umgebunsvariable enthalten ist (oder hinzugefügt wird)

Öffne jetzt eine Kommandozeile als Administrator und führe `nssm install gogs` aus, um Gogs als Service zu konfigurieren.

```
C:\>nssm install gogs
```

"NSSM service installer" wird jetzt starten. Konfiguriere alles wie folgt:

Application Tab:

* Path: C:\gogs\gogs.exe
* Startup directory: C:\gogs
* Arguments: web

![](/docs/images/install_gogs_on_windows_nssm_1.png)

Details Tab:

* Display name: Go Gits Service
* Description: Gogs (Go Git Service) ist ein schmerzfreier selbst gehosteter Git service in Go
* Startup type: Automatic (Delayed Start)

Beachte, dass wir [Verzögerten Start](http://stackoverflow.com/a/11015576), sodass der Service nicht die Initiale Boot-Zeit beeinflusst. Gogs wird zwei Minuten nach den nicht verzögerten Services starten.

![](/docs/images/install_gogs_on_windows_nssm_2.png)

I/O tab:

* Output (stdout): C:\gogs\log\gogs-nssm.txt
* Error (stderr): C:\gogs\log\gogs-nssm.txt

Diese Einstellungen werden allen Text-Output, den Gogs normalerweise in die Konsole schreiben würde, in die angegebene Datei stattdessen umleiten.

![](/docs/images/install_gogs_on_windows_nssm_3.png)

File Rotation Tab:

* Ankreuzen: Rotate files
* Restrict rotation to files bigger than: 1000000 bytes

![](/docs/images/install_gogs_on_windows_nssm_4.png)

Environment Tab:

* Environment variables: PATH=%PATH%;C:\gogs;C:\Program Files (x86)\Git\bin

oder

* Environment variables: PATH=%PATH%;C:\gogs;C:\Programme (x86)\Git\bin

Diese Einstellung garantiert, dass sowohl `gogs.exe` als auch `git.exe` im Gogs Service-Pfad sind während der Ausführung des Programms.

![](/docs/images/install_gogs_on_windows_nssm_5.png)

Jetzt auf "Install service" klicken. Das Programm bestätigt dann die
erfolgreiche Transaktion. Falls das Anlegen des Service fehlschlägt, gucke bitte
auf die Konsole, um die Error-Meldung zu sehen. Wenn es erfolgreich ausgeführt
wird, gehe auf die Kommandozeile und mache das folgende:

```
nssm start gogs
```

You should see:

```
gogs: Start: The operation completed successfully.
```

Jetzt überprüfe, ob das wahr ist, indem du `C:\gogs\log\gogs-nssm.txt` öffnest. Du solltest den Startvorgang von Gogs sehen, der endet mit:

```
timestamp [I] SQLite3 Enabled
timestamp [I] Run Mode: Production
timestamp [I] Listen: http://127.0.1.1:80
```

Jetzt gehe auf deinen Webbrowser auf `http://gogs/` und logge dich ein.

Gogs läuft als Service und muss nicht manuell gestartet werden, es sei denn irgendetwas geht schief. NSSM wird versuchen den Service für dich neu zu starten, falls der Gogs Server abbricht.

Wenn du Gogs neu starten musst, weil du `app.ini` verändert hast, gehe auf eine
Administratorkonsole, nach dem du die Datei verändert hast und führe aus:

```
nssm restart gogs
```

Gucke auf das [Konfigrations-Cheet-Sheet](http://gogs.io/docs/advanced/configuration_cheat_sheet.html) zu Referenzen für `custom\conf\app.ini`-Einstellungen.

Ein Beispiel zum Logging während der Laufzeit:

```
[log]
ROOT_PATH = C:\gogs\log
```

Wenn du diese Zeile für Go Git Service 0.5.13.0212 Beta in die Einstellungen packst, wird es folgendes in `C:\gogs\log\gogs-nssm.txt` stehen:

```
timestamp [T] Custom path: C:/gogs/custom
timestamp [T] Log path: C:\gogs\log
timestamp [I] Gogs: Go Git Service 0.5.13.0212 Beta
timestamp [log.go:294 Error()] [E] Fail to set logger(file): invalid character 'g' in string escape code
```

Das war erwartet mit `C:\custom\conf\app.ini`:

```
ROOT_PATH = C:\gogs\log
```

Und das war die `nssm`-Interaktion zum beheben:

```
C:\>nssm restart gogs
gogs: STOP: The operation completed successfully.
gogs: Unexpected status SERVICE_PAUSED in response to START control.

C:\>nssm start gogs
gogs: START: An instance of the service is already running.

C:\>nssm stop gogs
gogs: STOP: The operation completed successfully.

C:\>nssm start gogs
gogs: Unexpected status SERVICE_PAUSED in response to START control.

C:\>nssm restart gogs
gogs: STOP: The operation completed successfully.
gogs: START: The operation completed successfully.
```
