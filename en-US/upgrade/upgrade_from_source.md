---
name: From source
sort: 1
---

# Upgrade from source

### Check and Set Up the Environment

Check if path is defined in your system

```bash
sudo su - git
echo GOROOT
echo GOPATH
echo PATH
```

If isn't defined, set the paths that correspond to your system:

```bash
cd ~
echo 'export GOROOT=$HOME/local/go' >> $HOME/.bashrc
echo 'export GOPATH=$HOME/go' >> $HOME/.bashrc
echo 'export PATH=$PATH:$GOROOT/bin:$GOPATH/bin' >> $HOME/.bashrc
source $HOME/.bashrc
```

## Upgrade Gogs

The general way to upgrade Gogs:

```bash
# Upgrade source and install dependencies
$ go get -u github.com/gogits/gogs

# Remove or move old build and build new main program
$ cd $GOPATH/src/github.com/gogits/gogs
$ rm gogs # mv gogs gogs.old
$ go build
```

### Test Installation

To make sure Gogs is working:

```bash
cd $GOPATH/src/github.com/gogits/gogs
./gogs web
```

If you do not see error messages, hit `Ctrl-C` to stop Gogs.

### Build with SQLite3/Redis/Memcache

If you need to enable SQLite3/Redis/Memcache, please delete directory `$GOPATH/pkg/{GOOS_GOARCH}/github.com/gogits/gogs` and do:

```bash
# Upgrade source and install dependencies
$ go get -u -tags "sqlite redis memcache" github.com/gogits/gogs

# Remove or move old build and build new main program
$ cd $GOPATH/src/github.com/gogits/gogs
$ rm gogs # mv gogs gogs.old
$ go build -tags "sqlite redis memcache"
```

Then, run Gogs again and access from your browser.