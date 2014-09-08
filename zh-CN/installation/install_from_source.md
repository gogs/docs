---
name: 源码安装
sort: 2
---

# 源码安装

## 安装依赖

### 基本依赖

- [Go 语言](http://golang.org)：版本 >= 1.2
- [Git](http://git-scm.com)：版本 >= 1.8

### 第三方包

- [github.com/Unknwon/cae/zip](https://github.com/Unknwon/cae)
- [github.com/Unknwon/com](https://github.com/Unknwon/com)
- [github.com/Unknwon/goconfig](https://github.com/Unknwon/goconfig)
- [github.com/Unknwon/i18n](https://github.com/Unknwon/i18n)
- [github.com/Unknwon/macaron](https://github.com/Unknwon/macaron)
- [github.com/codegangsta/cli](https://github.com/codegangsta/cli)
- [github.com/codegangsta/inject](https://github.com/codegangsta/inject)
- [github.com/go-martini/martini](https://github.com/go-martini/martini)
- [github.com/go-xorm/core](http://github.com/go-xorm/core)
- [github.com/go-xorm/xorm](http://github.com/go-xorm/xorm)
- [github.com/macaron-contrib/cache](https://github.com/macaron-contrib/cache)
- [github.com/macaron-contrib/captcha](https://github.com/macaron-contrib/captcha)
- [github.com/macaron-contrib/csrf](https://github.com/macaron-contrib/csrf)
- [github.com/macaron-contrib/i18n](https://github.com/macaron-contrib/i18n)
- [github.com/macaron-contrib/session](https://github.com/macaron-contrib/session)
- [github.com/macaron-contrib/toolbox](https://github.com/macaron-contrib/toolbox)
- [github.com/nfnt/resize](https://github.com/nfnt/resize)
- [github.com/saintfish/chardet](https://github.com/saintfish/chardet)
- [github.com/go-sql-driver/mysql](https://github.com/go-sql-driver/mysql) or [github.com/lib/pq](https://github.com/lib/pq) or [github.com/mattn/go-sqlite3](https://github.com/mattn/go-sqlite3)
- [github.com/beego/redigo/redis](https://github.com/beego/redigo/redis) or [github.com/beego/memcache](https://github.com/beego/memcache)

### 安装

```
# 检查更新 Gopm

$ gopm update -v

# 下载并构建二进制

$ gopm bin -u -v gogs path/to/anywhere
```

Or

```
# 下载并安装依赖

$ go get -u github.com/gogits/gogs

# 构建主程序

$ cd $GOPATH/src/github.com/gogits/gogs
$ go build
```

如果您想要启动 SQLite3 请先删除在 `$GOPATH/pkg` 中所有与 Gogs 有关的文件：

```
$ go get -u -tags sqlite github.com/gogits/gogs
$ cd $GOPATH/src/github.com/gogits/gogs
$ go build -tags sqlite
```

安装完成后可继续参照 [配置与运行](configuration_and_run.md)。
