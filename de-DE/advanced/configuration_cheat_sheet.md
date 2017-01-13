---
name: Config Cheat Sheet
---

### Konfigurations-Cheat-Sheet

Das hier ist ein Cheat-Sheet für die Gogs-Konfigurations-Datei. Es hilft dir etwas, wenn du ganz verstehen willst, wie es Gogs beeinflusst.

Bevor du anfängst: Stelle sicher, dass du alle Änderungen in der `custom/conf/app.ini` oder dem entsprechenden Pfad machst, nicht in der `conf/app.ini`

Alle Standard-Einstellungen können in [app.ini](https://github.com/gogits/gogs/blob/master/conf/app.ini) nachgesehen werden. Wenn du etwas siehst wie `%(X)s`: Das ist ein Feature von [ini](https://github.com/go-ini/ini/tree/v1#recursive-values) um Werte rekursiv einzulesen.

Jede Konfiguration, die mit :exclamation: markiert ist, solltest du auf dem Standard-Wert lassen. bis du **wirklich** verstehst was sie tut.

## Generell

- `APP_NAME`: Name der Applikation, ändere es zu was immer du haben willst
- `RUN_USER`: Der Benutzer, unter dem Gogs läuft, wir empfehlen `git`; wie dem auch sei, ändere das zu was immer dein Benutzername ist, wenn du Gogs auf deinem Privatrechner ausführst. Gogs stürzt möglicherweise ab, wenn dieser Wert falsch gesetzt ist.
- `RUN_MODE`: Aufgrund von Performance- und anderen Gründen ändere diesen Wert zu `prod` wenn du Gogs in einer Produktions-Umgebung verwendest. Der Installer wird diesen Wert automatisch auf `prod` setzen.

## Repository (`repository`)

- `ROOT`: Wurzelpfad, in dem die Repositorys aller Benutzer gespeichert werden. Das muss ein absoluter Pfad sein, Standard ist `~/<user name>/gogs-repositories`.
- `SCRIPT_TYPE`: Die Skript-Sprache, die dein Server unterstützt. Normalerweise ist das `bash`, aber einige Benutzer haben gemeldet, sie haben bloß `sh`.
- `ANSI_CHARSET`: Das Standard-Charset für unbekannte Charsets.
- `FORCE_PRIVATE`: Jedes neue Projekt als private erzwingen.
- `MAX_CREATION_LIMIT`: Maximale Anzahl an Repositorys pro User, `-1` bedeutet keine Begrenzung.
- `PULL_REQUEST_QUEUE_LENGTH`:exclamation:: Test-Länge bei Pull-Requests. Mach es so lang wie möglich.

## UI (`ui`)

- `EXPLORE_PAGING_NUM`: Anzahl der Repositorys, die in einer Explore-Seite angezeigt werden.
- `ISSUE_PAGING_NUM`: Anzahl an Issues, die auf einer Seite angezeigt werden (für alle Seiten, auf denen Issues angezeigt werden)
- `FEED_MAX_COMMIT_NUM`: Anzahl an maximalen Commits. die im Aktivitäts-Feed angezeigt werden.

### UI - Admin (`ui.admin`)

- `USER_PAGING_NUM`: Anzahl an Usern, die auf einer Seite angezeigt werden.
- `REPO_PAGING_NUM`: Anzahl an Repos, die auf einer Seite angezeigt werden.
- `NOTICE_PAGING_NUM`: Anzahl an Benachrichtigungen, die auf einer Seite angezeigt werden.
- `ORG_PAGING_NUM`: Anzahl an Organisationen, die auf einer Seite angezeigt werden.

## Markdown (`markdown`)

- `ENABLE_HARD_LINE_BREAK`: Entscheidet, ob harte Zeilenumbrüche aktiviert sind oder nicht

## Server (`server`)

- `PROTOCOL`: Entweder `http` oder `https`.
- `DOMAIN`: Domain-Name deines Servers
- `ROOT_URL`: Die komplette öffentliche URL deines Gogs Servers.
- `HTTP_ADDR`: HTTP Adresse, auf der Gogs lauscht.
- `HTTP_PORT`: HTTP Port, auf dem Gogs lauscht.
- `DISABLE_SSH`: Schaltet das SSH Feature aus, wenn es nicht verfügbar ist.
- `START_SSH_SERVER`: Aktivieren, um den eingebauten SSH-Server zu starten.
- `SSH_PORT`: Der SSH-Port, falls es nicht `22` ist.
- `OFFLINE_MODE`: Schaltet CDN und Gravatar aus.
- `DISABLE_ROUTER_LOG`: Anschalten, um keine Router-Logs auszugeben
- `CERT_FILE`: Pfad zur Zertifikats-Datei für HTTPS
- `KEY_FILE`: Pfad zum Zertifikats-Key für HTTPS
- `STATIC_ROOT_PATH`: Pfad, unter dem die Templates und statischen Dateien liegen. Standardmäßig ist das der Pfad, unter dem Gogs liegt.
- `ENABLE_GZIP`: Anschalten um GZip-Support auf Programm-Ebene zu haben.
- `LANDING_PAGE`: Startseite für nicht eingeloggte Benutzer: Entweder `home` oder `explore`.

## Datenbank (`database`)

- `DB_TYPE`: Der Datenbanktyp, den du wählst, entweder `mysql`, `postgres` oder `sqlite3`.
- `HOST`: Adresse und Port des Datenbank-Servers
- `NAME`: Datenbank-Name
- `USER`: Datenbank-Benutzer
- `PASSWD`: Datenbank-Passwort
- `SSL_MODE`: Nur für PostgreSQL.
- `PATH`: Nur für SQLite3, Pfad zur Datenbank-Datei

## Sicherheit (`security`)

- `INSTALL_LOCK`: Entscheidet, ob man die Installations-Seite aufrufen kann. (Das Setzen eines Administrator-Accounts ist Teil davon, es ist also ein sehr wichtiger Wert)
- `SECRET_KEY`: Globaler geheimer Schlüssel für die Server-Sicherheit, **ändere ihn besser** (Es wird jedes mal, wenn du installierst ein zufälliger Schlüssel generiert)
- `LOGIN_REMEMBER_DAYS`: Cookie-Lebenszeit in Tagen
- `COOKIE_USERNAME`: Cookie-Name zur Speicherung des Benutzernamens
- `COOKIE_REMEMBER_NAME`: Cookie-Name zur Speicherung von Auto-Login-Informationen
- `REVERSE_PROXY_AUTHENTICATION_USER`: Header-Name für Reverse-Proxy-Authentifizierung Benutzername

## Service (`service`)

- `ACTIVE_CODE_LIVE_MINUTES`: Lebensdauer des Aktivierungs-Codes (in Minuten)
- `RESET_PASSWD_CODE_LIVE_MINUTES`: Lebensdauer des Passwort-Reset-Codes (in Minuten)
- `REGISTER_EMAIL_CONFIRM`: Aktivieren, um bei der Registrierung eine e-Mail-Bestätigung zu erfragen. `Mailer` muss dafür aktiviert sein.
- `DISABLE_REGISTRATION`: Deaktiviert die Registrierung, wodurch nur noch Administratoren Accounts anlegen dürfen.
- `SHOW_REGISTRATION_BUTTON`: Entscheidet, ob ein Registrieren-Button angezeigt wird.
- `REQUIRE_SIGNIN_VIEW`: Aktiviere das, um Nutzer zu zwingen sich einzuloggen um andere Seiten zu sehen.
- `ENABLE_CACHE_AVATAR`: Aktivieren, um Gravatars lokal zwischenzuspeichern.
- `ENABLE_NOTIFY_MAIL`: Aktivieren, um bei Ereignissen e-Mails an die Nutzer zu schicken (z.B. beim Issue schließen). `Mailer` muss dafür aktiviert sein.
- `ENABLE_REVERSE_PROXY_AUTHENTICATION`: Aktivieren, um Reverse Proxy Authentication zu erlauben. Details: https://github.com/gogits/gogs/issues/165
- `ENABLE_REVERSE_PROXY_AUTO_REGISTRATION`: Aktivieren, um Auto-Registrierung für Reverse Authentication zu erlauben.
- `DISABLE_MINIMUM_KEY_SIZE_CHECK`: Überprüfe nicht die minimale Schlüssellänge für den Schlüsseltyp.
- `ENABLE_CAPTCHA`: Aktivieren, um ein Captcha bei der Registrierung einzublenden.

## Webhook (`webhook`)

- `QUEUE_LENGTH`:exclamation:: Warteschlangenlänge für Hook Aufträge
- `DELIVER_TIMEOUT`: Auslieferungs-Timeout in Sekunden für das Absenden von Webhooks
- `SKIP_TLS_VERIFY`: Entscheidet ob unsichere Zertifikate erlaubt sind oder nicht.
- `PAGING_NUM`: Anzahl der Webhook-Historie, die auf einer Seite angezeigt wird.

## Mailer (`mailer`)

- `ENABLED`: Aktivieren, um den Mail-Service zu benutzen.
- `DISABLE_HELO`: HELO-Operation ausschalten.
- `HELO_HOSTNAME`: Eigener Hostname für die HELO-Operation.
- `HOST`: SMTP Server-Adresse und -Port (Beispiel: smtp.gogs.io:587).
- `FROM`: Absender-Adresse, RFC 5322. Es kann eine einfache Adresse sein oder das "Name" <email@example.com> Format.
- `USER`: Benutzername für den Mailer (Normalerweise deine e-Mail-Adresse).
- `PASSWD`: Passwort für den Mailer.
- `SKIP_VERIFY`: Selbstsignierte Zertifikate nicht überprüfen.

Hinweis: Gogs unterstützt nur SMTP mit STARTTLS.

## Cache (`cache`)

- `ADAPTER`: Cache-Engine-Adapter, entweder `memory`, `redis`, oder `memcache`. Wenn du `redis` oder `memcache` nutzen willst, stelle sicher, dass Gogs mit den Build-Tags `redis` oder `memcache` erstellt wurde (z.B. : `go build -tags='redis'`).
- `INTERVAL`: Nur für Memory-Cache, Speicherbereinigungs-Intervall in Sekunden
- `HOST`: Nur für redis und memcache, die Server-Adresse und Port.
    - Redis: `network=tcp,addr=127.0.0.1:6379,password=macaron,db=0,pool_size=100,idle_timeout=180`
    - Memache: `127.0.0.1:9090;127.0.0.1:9091`

## Sitzungs (`session`)

- `PROVIDER`: Sitzungs-Engine-Provider, entweder `memory`, `file`, `redis`, oder `mysql`.
- `PROVIDER_CONFIG`: Für `file` der Pfad, für andere Server-Adresse und -Port.
- `COOKIE_SECURE`: Aktivieren, um HTTPS für alle Sitzungs-Zugriffe zu erzwingen.
- `GC_INTERVAL_TIME`: Speicherbereinigungs-Intervall in Sekunden.

## Bilder (`picture`)

- `GRAVATAR_SOURCE`: Kann `gravatar`, `duoshuo` oder etwas wie `http://cn.gravatar.com/avatar/` sein.
- `DISABLE_GRAVATAR`: Aktivieren, um nur lokale Gravatars zu benutzen.
- `ENABLE_FEDERATED_AVATAR`: Aktivieren, um die Unterstüzung von "federated avatars" zu aktivieren(siehe http://www.libravatar.org)

## Anhänge (`attachment`)

- `ENABLED`: Aktivieren, um Usern Uploads zu erlauben.
- `PATH`: Pfad, unter dem Anhänge gespeichert werden.
- `ALLOWED_TYPES`: erlaubte MIME-Types (z.B. `image/jpeg|image/png`.
- `MAX_SIZE`: Maximale Größe in MB (z.B. `4`)
- `MAX_FILES`: Maximale Anzahl an Dateien, die gleichzeitig hochgeladen werden kann.

## Log (`log`)

- `ROOT_PATH`: Wurzelpfad zum Log-Pfad
- `MODE`: Logging-Methode. Standard ist `console`. Für mehrere Methoden liste sie kommasepariert auf.
- `LEVEL`: Generelles Log-Level, Standard ist `Trace`.

## Git (`git`)

- `MAX_GIT_DIFF_LINES`: Maximale Anzahl an Zeilen, die in einem Diff angezeigt werden.
