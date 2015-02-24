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

请通过 [gopmfile](https://github.com/gogits/gogs/blob/master/.gopmfile) 查看完整的第三方包依赖列表。

### 安装

```
# 检查更新 Gopm
$ gopm update -v

# 下载并构建二进制
$ gopm bin -u -v gogs -d path/to/anywhere
```

Or

```
# 下载并安装依赖
$ go get -u github.com/gogits/gogs

# 构建主程序
$ cd $GOPATH/src/github.com/gogits/gogs
$ go build
```

#### 构建 `dev` 分支版本

```
$ mkdir -p $GOPATH/src/github.com/gogits
$ cd $GOPATH/src/github.com/gogits
$ git clone -b dev https://github.com/gogits/gogs.git
$ cd gogs
$ go get ./...
$ go build
```

#### 构建 SQLite3/Redis/Memcache 集成版

如果您想要启动 SQLite3/Redis/Memcache 请先删除 `$GOPATH/pkg/{GOOS_GOARCH}/github.com/gogits/gogs` 目录，然后：

```
$ go get -u -tags "sqlite redis memecache" github.com/gogits/gogs
$ cd $GOPATH/src/github.com/gogits/gogs
$ go build -tags "sqlite redis memecache"
```

安装完成后可继续参照 [配置与运行](configuration_and_run.md)。
