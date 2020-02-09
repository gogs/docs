---
name: Troubleshooting
---

# Troubleshooting

## Installation

- Fehler: `../gosrc/src/github.com/gogs/gogs/cmd/cert.go:79: undefined: elliptic.P224`
- Grund: Das golang-Paket in RHEL/CentOS unterstützt elliptische Kurven in Verschlüsselungen nicht, da es patentiert ist und es wurde speziell aus CentOS/RHEL entfernt.
- Lösung: Downloade und installiere Go von [golang.org/dl](http://golang.org/dl).

## SSH

- Fehler: SSH-Verbindung hängt 60 Sekunden lang
- Grund: Gogs fragt sich selbst (den Webservice) nach jedem SSH-Push an. Die Server-Firewall oder der ISP verbieten das aber.

## GIT

- Fehler: `bash /path/to/gogs: no such file or directory`
- Grund: Du hast die Gogs-Dateien verschoben und der alte Pfad war in der Datei `~/.ssh/authorized_keys` fest kodiert.
- Lösung: Gehe auf das Admin-Panel (`/admin`) und führe da die Operation `Überschreibe '.ssh/authorized_keys' Datei` und `Überschreibe alle Hooks der Repositories` aus.

-----

- Fehler:
	- `fatal: 'XX/XX.git' does not appear to be a git repository`
	- Commits werden gepusht, es wird aber immer noch ein leeres Repository angezeigt
- Grund: Es gibt doppelte SSH-Keys in der Datei `~/.ssh/authorized_keys`. Möglicherweise hast du oder benutzt immer noch Gitlab mit dem gleichen Benutzer.
- Lösung: Lösche das alte und behalte nur das, was von Gogs hinzugefügt wurde.

-----

- Fehler: `repo.NewRepoContext(fail to set git user.email):`
- Grund: Dieser Fehler passiert, wenn Windows-Benutzer die Git Bash ohne `cmd`-Option installieren
- Lösung: Installiere die Git Bash erneut mit der `cmd`-Option

## Formular-Validierung

- Fehler: `Repository/User name contains illegal characters`
- Grund: Um unerwartete Fehler zu vermeiden wird der User-/Repository-Name als illegal angesehen, wenn er auf folgende Regeln zutrifft:
	- Der Name ist irgendeines der Wörter `"debug", "raw", "install", "api", "avatar", "user", "org", "help", "stars", "issues", "pulls", "commits", "repo", "template", "admin", "new"`.
	- Der Name endet auf `".git"` oder `".keys"`.

## Cache

- Fehler: `cache: unknown adaptername "memcache" (forgotten import?)`
- Grund: Um unnötige Paket-Importe zu vermeiden benutzen wir Build-Tags um diese zu spezifizieren, wenn wir sie brauchen.
- Lösung:
	- Download: `go get -tags memcache github.com/gogs/gogs`
	- Erstellen: `go build -tags memcache`
	- Die gleichen Schritte für `redis` ausführen, wenn das der Cache-Adapter sein soll.

### MySQL

- Fehler: `Error 1071: Specified key was too long; max key length is 1000 bytes`
- Grund: Dieser Fehler wird von MyISAM hervorgerufen.
- Lösung: Wenn du die `config/mysql.sql` importiert hast, logge dich in MySQL ein und führe folgendes aus:

	```sql
	use gogs;
	set global storage_engine=INNODB;
	```

Danach gehe auf [http://localhost:3000/install](http://localhost:3000/install). Dann sollte alles funktionieren. (Dank geht an [@linc01n](https://github.com/linc01n)).

-----

- Fehler: `Database setting is not correct: This server only supports the insecure old password authentication. If you still want to use it, please add 'allowOldPasswords=1' to your DSN. See also https://github.com/go-sql-driver/mysql/wiki/old_passwords`
- Grund: Es wurden nur Passwörter für @localhost erneuert -- es gab einen zweiten Eintrag in der User-Tabelle, in dem @% immer noch das alte Passwort hat.
- Lösung: [GitHub Kommentare](https://github.com/gogs/gogs/issues/385#issuecomment-54357073)

## Mailer

#### Probleme mit Gmail

- Fehler: Gmail mit Fehler 534: `Please log in via your web browser and then try again`
- Grund: Das passiert, da Google deinem Server nicht vertraut.
- Lösung:
	- Gehe auf https://accounts.google.de und logge dich ein
	- Gehe weiter auf https://accounts.google.de/DisplayUnlockCaptcha und klicke auf `Weiter`
	- Kopiere den Link, der in etwa so aussieht (Ausgabe in Gogs Server Log): https://accounts.google.com/ContinueSignIn?sarp=1&scc=1&plt=AKgnsbvPPN_E_25__nyS*******f18O9uuLNtz0Imw und logge dich noch einmal ein.
	- Jetzt sollte es klappen. Last but not least, du solltest den Spam-Ordner überprüfen, falls der Mail-Anbieter denkt, deine GMail ist ein Spam-Konto.

#### Authentifizierung fehlgeschlagen

- Fehler: `gomail: could not send email 1: Auth: 535`
- Grund: Das Passwort enthält Sonderzeichen
- Lösung: Setze das Passwort in einfache Anführungszeichen: `PASSWD = 'P4§$w0rd'`

## Windows

- Fehler:

```
2014/09/18 15:04:40 [repo.go:115 CreatePost()] [E] CreatePost: initRepository: initRepository(git clone): cygwin warning:
MS-DOS style path detected: C:\Users\user\gogs-repositories\unos\test3.git/.git
Preferred POSIX equivalent is: /cygdrive/c/Users/user/gogs-repositories/unos/test3.git/.git
CYGWIN environment variable option "nodosfilewarning" turns off this warning.
Consult the user's guide for more details about POSIX paths:
http://cygwin.com/cygwin-ug-net/using.html#using-pathnames
Cloning into 'C:\Users\user\AppData\Local\Temp\484264900'...
fatal: '/cygdrive/d/svnroot/research/gogs/C:\Users\user\gogs-repositories\unos\test3.git' does not appear to be a git repository
fatal: Could not read from remote repository.
```

- Grund: Du hast eine andere Shell installiert, die einen anderen Pfad-Stil benutzt.
- Lösung: Versuche Gogs aus der Standard-CMD zu starten

-----

- Fehler: `Resource interpreted as Stylesheet but transferred with MIME type application/x-css`
- Grund: Falscher Wert in der Windows Registry
- Lösung: Suche `.css` in `HKEY_CLASSES_ROOT` in der Registry und ändere den Wert `Content Type` in `text/css`.

## Anderes

- Fehler: Extrem langsamer Seitenaufbau, obwohl im Seitenfuß die Zeit normal aussieht (unter 100ms)
- Grund: Es könnte von NGINX hervorgerufen werden, der versucht IPv4 als IPv6-Adressen aufzurufen
- Lösung: Nutze expliziten Hostnamen `127.0.0.1` statt `localhost`

-----

- Fehler: `Error 1062: Duplicate entry 'Unknown-Mac' for key 'UQE_public_key_name'`
- Grund: Das wird von altem Code hervorgerufen. Die `public_key`-Tabelle hatte eine `UQE_public_key_name` Einzigartigkeits-Regel für den SSH-Key-Namen in früheren Versionen.
- Lösung: Du kannst diese Regel manuell löschen um das Problem zu lösen.

-----

- Fehler: `GLIBC_2.14 not found`
- Lösung: versuche `sudo apt-get -t testing install libc6-dev`.

-----

- Fehler: `[Macaron] PANIC: session(start): mkdir data: permission denied`
- Grund: Gogs erstellt den Ordner `data` als Unterordner des Ordners, in dem sich die ausführbare Datei befindet.
- Lösung: Kontrolliere, dass Gogs alle Berechtigungen hat, Unterordner in dem Ordner zu erstellen.

-----

- Fehler: `! [remote rejected] master -> master (hook declined)`
- Grund: Git konnte das Update-Skript nicht ausführen
- Lösung: Kontrolliere, dass die `bash` auf deinem System verfügbar ist. Alle Hook-Skripte benötigen diese Shell.
