---
name: From binary
sort: 1
---

# Upgrade from binary

**Downloads are available on [Install from binary](https://gogs.io/docs/installation/install_from_binary).**

Find the location where the current binary is.

```bash
# On default environment generaly is on git home folder
$ sudo su - git
$ cd ~
$ pwd
/home/git
$ ls
gogs gogs-repositories
```

Move gogs folder to other name, absolutely don't remove, only move.

```bash
$ mv gogs gogs_old
```

Download and unzip new binary.

```bash
# Check latest release to download based on your actual OS and ARCH running
$ wget https://dl.gogs.io/gogs_v$VERSION_$OS_$ARCH.tar.gz
$ tar -zxvf gogs_v$VERSION_$OS_$ARCH.tar.gz
$ ls
gogs gogs_old  gogs-repositories gogs_v$VERSION_$OS_$ARCH.tar.gz
```

Copy custom, data and log folder to unziped folder.

```bash
$ cp -R gogs_old/custom gogs
$ cp -R gogs_old/data gogs
$ cp -R gogs_old/log gogs
```

Then, run and test in your browser.

```bash
$ cd gogs
$ ./gogs web
```