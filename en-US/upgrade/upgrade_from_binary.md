---
name: From binary
---

# Upgrade from binary

**Downloads are available on [Install from binary](/docs/installation/install_from_binary).**

**Note** If you plan to do copy-paste upgrade, make sure you delete old `templates` directory first!

Find the location where the current installation is:

```bash
# On default environment generally is on git home folder
$ sudo su - git
$ cd ~
$ pwd
/home/git
$ ls
gogs gogs-repositories
```

Move Gogs folder to other name, absolutely don't remove, only move.

```bash
$ mv gogs gogs_old
```

Download and unzip new binary:

```bash
# Check latest release to download based on your actual OS and ARCH running
$ wget wget https://dl.gogs.io/$VERSION/$OS_$ARCH.tar.gz
$ tar -zxvf $OS_$ARCH.tar.gz
$ ls
gogs gogs_old  gogs-repositories $OS_$ARCH.tar.gz
```

Copy `custom`, `data` and `log` directories to unzipped directory:

```bash
$ cp -R gogs_old/custom gogs
$ cp -R gogs_old/data gogs
$ cp -R gogs_old/log gogs
```

Then, run and test in your browser:

```bash
$ cd gogs
$ ./gogs web
```

Well done!
