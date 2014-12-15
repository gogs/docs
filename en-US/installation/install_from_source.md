---
name: From source
sort: 2
---

# Install from source

## Dependencies

### Overall

- [Go Programming Language](http://golang.org): Version >= 1.2
- [Git](http://git-scm.com): Version >= 1.8


### Third-party packages

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

#### Build with SQLite3/Redis/Memcache

If you need to enable SQLite3/Redis/Memcache, please delete directory `$GOPATH/pkg/{GOOS_GOARCH}/github.com/gogits/gogs` and do:

```
$ go get -u -tags "sqlite redis memcache" github.com/gogits/gogs
$ cd $GOPATH/src/github.com/gogits/gogs
$ go build -tags "sqlite redis memcache"
```

See [Configuration and run](configuration_and_run.md) to go further.
