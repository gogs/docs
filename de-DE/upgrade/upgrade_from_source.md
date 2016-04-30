---
name: von Quelldateien
---

# Upgrade von Quelldateien

Der allgemeine Weg um Gogs zu aktualisieren:

```bash
# Upgrade source and install dependencies
$ go get -u github.com/gogits/gogs

$ cd $GOPATH/src/github.com/gogits/gogs

# Remove old build
$ rm gogs

# or move old build
$ mv gogs gogs-$(./gogs -v | awk '{print $3}')

# And rebuild Gogs
$ go build
```

Andere Operationen:

- [Build aus dem `develop`-Branch](/docs/installation/install_from_source#build-aus-dem-develop-branch)
- [Testen der Installation](/docs/installation/install_from_source#testen-der-installation)
- [Build mit Tags](/docs/installation/install_from_source#build-mit-tags)
