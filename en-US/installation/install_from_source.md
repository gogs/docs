---
name: From source
sort: 2
---

# Install from source

## Dependencies

### Overall

- [Go Programming Language](http://golang.org): Version >= 1.2
- [Git](http://git-scm.com): Version >= 1.8

We are going to create a new user called `git` and install/setup everything under that user:

`sudo adduser --disabled-login --gecos 'Gogs' git`

## Installing Go
If your system's Go matches the requirements skip this section.

Install go in `/home/git/local/go` so it wouldn't interfer with future updates of your system's package manager:

```bash
sudo su - git
cd ~
# create a folder to install 'go'
mkdir local
# Download go (change go$VERSION.$OS-$ARCH.tar.gz to the latest realse)
wget https://storage.googleapis.com/golang/go$VERSION.$OS-$ARCH.tar.gz
# expand it to ~/local
tar -C /home/git/local -xzf go$VERSION.$OS-$ARCH.tar.gz
```

Set the paths:

```bash
sudo su - git
cd ~
echo 'export GOROOT=$HOME/local/go' >> $HOME/.bashrc
echo 'export GOPATH=$HOME/go' >> $HOME/.bashrc
echo 'export PATH=$PATH:$GOROOT/bin:$GOPATH/bin' >> $HOME/.bashrc
source $HOME/.bashrc
```


### Third-party packages

You can install `gopm` by issuing:

```
sudo su - git
cd ~
go get -u github.com/gpmgo/gopm
```

See [gopmfile](https://github.com/gogits/gogs/blob/master/.gopmfile) for complete list of third-party packages.

### Install

```
# Check update of gopm
$ gopm update -v

# Download and build binary
$ gopm bin -u -v gogs path/to/anywhere
```

Or

```
# Download and install dependencies
$ go get -u github.com/gogits/gogs

# Build main program
$ cd $GOPATH/src/github.com/gogits/gogs
$ go build
```

#### Build from `dev` branch

```
$ mkdir -p $GOPATH/src/github.com/gogits
$ cd $GOPATH/src/github.com/gogits
$ git clone -b dev https://github.com/gogits/gogs.git
$ cd gogs
$ go get ./...
$ go build
```

#### Test
To make sure 'gogs' is working:

```
cd $GOPATH/src/github.com/gogits/gogs
./gogs web
```
If you do not see error messages, hit `Ctrl-C` to stop the 'gogs'

#### Build with SQLite3/Redis/Memcache

If you need to enable SQLite3/Redis/Memcache, please delete directory `$GOPATH/pkg/{GOOS_GOARCH}/github.com/gogits/gogs` and do:

```
$ go get -u -tags "sqlite redis memcache" github.com/gogits/gogs
$ cd $GOPATH/src/github.com/gogits/gogs
$ go build -tags "sqlite redis memcache"
```

## Next steps

- See [Configuration and run](configuration_and_run.md) to go further.
- For more detailed instructions including setting webserver and database see [the detailed steps](/docs/advanced/configuration_for_source_builds.md).
