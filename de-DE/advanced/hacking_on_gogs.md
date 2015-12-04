---
name: Bei Gogs mitwirken
---

# Bei Gogs mitwirken

Wenn du zu Gogs etwas beitragen willst, solltest du das Projekt forken und auf dem dev Branch arbeiten.
Es gibt eine kleine Stolperfalle: einige interne Pakete sind über ihre Github URL eingebunden.
Du musst also das Go tool austricksen, sodass es denkt, du hättest einen Klon des offiziellen Repositories.

Starte mit dem Download des Quellcodes, wie du es normalerweise tun würdest:

    $ go get github.com/gogits/gogs

Forke jetzt das Projekt auf Github und gehe dann in das Oberverzeichnis deines gogs Quellcode-Verzeichnisses:
    $ cd $GOPATH/src/github.com/gogits

Lösche das gogs Repository und klone deinen Fork anstelle:

    $ rm -rf gogs
    $ git clone git@github.com:<USERNAME>/gogs.git gogs

Gehe jetzt in das gogs-Verzeichnis, checke den dev Branch aus und nutze `go get` nochmal, um neue Abhängigkeiten zu holen:

    $ cd gogs
    $ git checkout develop
    $ go get

Das ist alles! Jetzt kannst du Gogs umprogrammieren. Teste deine Änderungen, pushe sie in dein Repository und öffne einen Pull-Request.
