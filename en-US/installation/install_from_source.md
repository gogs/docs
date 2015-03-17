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

### Third-party Packages

If you're interested in which third-part packages we are using, see [gopmfile](https://github.com/gogits/gogs/blob/master/.gopmfile). You may need this when you are making build package for Gogs.

## Installing Go

### Download

If your system's Go matches the requirements skip this section.

Install Go in `/home/git/local/go` so it wouldn't interfere with future updates of your system's package manager:

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

### Set Up the Environment

Set the paths that are corresponding to your system:

```bash
sudo su - git
cd ~
echo 'export GOROOT=$HOME/local/go' >> $HOME/.bashrc
echo 'export GOPATH=$HOME/go' >> $HOME/.bashrc
echo 'export PATH=$PATH:$GOROOT/bin:$GOPATH/bin' >> $HOME/.bashrc
source $HOME/.bashrc
```

### Install Gogs

The general way to install Gogs, 

```
# Download and install dependencies
$ go get -u github.com/gogits/gogs

# Build main program
$ cd $GOPATH/src/github.com/gogits/gogs
$ go build
```

If you have gopm available, you can try the following way to install Gogs:

```
# Check update of gopm
$ gopm update -v

# Download and build binary
$ gopm bin -u -v gogs -d path/to/anywhere
```

#### Build from `develop` branch

```
$ mkdir -p $GOPATH/src/github.com/gogits
$ cd $GOPATH/src/github.com/gogits
$ git clone -b develop https://github.com/gogits/gogs.git
$ cd gogs
$ go get ./...
$ go build
```

#### Test Installation

To make sure Gogs is working:

```
cd $GOPATH/src/github.com/gogits/gogs
./gogs web
```

If you do not see error messages, hit `Ctrl-C` to stop Gogs.

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
