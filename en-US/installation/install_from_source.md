---
name: From source
sort: 2
---

# Install from source

## Dependencies

### Overall

- [Go Programming Language](http://golang.org): Version >= 1.2

### Third-party packages

- [github.com/codegangsta/cli](https://github.com/codegangsta/cli)
- [github.com/go-martini/martini](https://github.com/go-martini/martini)
- [github.com/Unknwon/cae/zip](https://github.com/Unknwon/cae)
- [github.com/Unknwon/goconfig](https://github.com/Unknwon/goconfig)
- [github.com/nfnt/resize](https://github.com/nfnt/resize)
- [github.com/Unknwon/com](https://github.com/Unknwon/com)
- [github.com/go-sql-driver/mysql](https://github.com/go-sql-driver/mysql) or [github.com/lib/pq](https://github.com/lib/pq) or [github.com/mattn/go-sqlite3](https://github.com/mattn/go-sqlite3)
- [github.com/beego/redigo/redis](https://github.com/beego/redigo/redis) or [github.com/beego/memcache](https://github.com/beego/memcache)
- [github.com/go-xorm/core](http://github.com/go-xorm/core)
- [github.com/go-xorm/xorm](http://github.com/go-xorm/xorm)
- [github.com/juju2013/goldap](https://github.com/juju2013/goldap)

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

If you need to enable SQLite3, please delete all related files with Gogs in `$GOPATH/pkg` and do:

```
$ go get -u -tags sqlite github.com/gogits/gogs
$ cd $GOPATH/src/github.com/gogits/gogs
$ go build -tags sqlite
```

See [Configuration and run](configuration_and_run.md) to go further.
