---
name: von Downloads
---

# Upgrade von Downloads

**Die Downloads findest du unter [Installation von Downloads](/docs/installation/install_from_binary).**

Wechsle zum Installationsordner deiner Gogs Version (Standardmäßig unter `/home/git/`):

```bash
# Benutzer und Verzeichnis wechseln
$ sudo su - git
$ cd ~
# Verzeichnisinhalt anzeigen
$ ls
gogs gogs-repositories
```

Nun wie folgt den Ordner `gogs` umbenennen. **Nicht löschen!**

```bash
$ mv gogs gogs_old
```

Neuste Version herunterladen und entpacken. Siehe hierzu [Installation von Downloads](/docs/installation/install_from_binary).

Nun die Ordner `custom`, `data` und `log` aus der alten Installation übernehmen:

```bash
$ cp -R gogs_old/custom gogs
$ cp -R gogs_old/data gogs
$ cp -R gogs_old/log gogs
```

Anschließend gogs Starten und im Browser testen:

```bash
$ cd gogs
$ ./gogs web
```

Fertig!
