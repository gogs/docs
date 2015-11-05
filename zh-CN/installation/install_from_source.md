---
name: 源码安装
---

# 源码安装

## 安装依赖

### 基本依赖

- [Go 语言](http://golang.org)：版本 >= 1.3

### 第三方包

请通过 [gopmfile](https://github.com/gogits/gogs/blob/master/.gopmfile) 查看完整的第三方包依赖列表。一般情况下只有在您为 Gogs 制作构建包的时候才会用到。

## 安装 Go 语言

如果您的系统已经安装要求版本的 Go 语言，可以跳过此小节。

### 下载

您可以通过以下方式安装 Go 语言到 `/home/git/local/go` 目录：

```sh
sudo su - git
cd ~
# create a folder to install 'go'
mkdir local
# Download go (change go$VERSION.$OS-$ARCH.tar.gz to the latest realse)
wget https://storage.googleapis.com/golang/go$VERSION.$OS-$ARCH.tar.gz
# expand it to ~/local
tar -C /home/git/local -xzf go$VERSION.$OS-$ARCH.tar.gz
```

### 设置环境

请设置和您系统环境对应的路径：

```sh
sudo su - git
cd ~
echo 'export GOROOT=$HOME/local/go' >> $HOME/.bashrc
echo 'export GOPATH=$HOME/go' >> $HOME/.bashrc
echo 'export PATH=$PATH:$GOROOT/bin:$GOPATH/bin' >> $HOME/.bashrc
source $HOME/.bashrc
```

## 安装 Gogs

常用的安装方式：

```sh
# 下载并安装依赖
$ go get -u github.com/gogits/gogs

# 构建主程序
$ cd $GOPATH/src/github.com/gogits/gogs
$ go build
```

如果您已经安装 gopm，则可以尝试使用以下方式安装：

```sh
# 检查更新 Gopm
$ gopm update -v

# 下载并构建二进制
$ gopm bin -u -v gogs -d path/to/anywhere
```

### 构建 `develop` 分支版本

如果您想要安装 `develop`（或其它）分支版本，则可以通过以下命令：

```sh
$ mkdir -p $GOPATH/src/github.com/gogits
$ cd $GOPATH/src/github.com/gogits

# 请确保没有使用 “https://github.com/gogits/gogs.git”
$ git clone --depth=1 -b develop https://github.com/gogits/gogs
$ cd gogs
$ go get -u ./...
$ go build
```

### 测试安装

您可以通过以下方式检查 Gogs 是否可以正常工作：

```sh
cd $GOPATH/src/github.com/gogits/gogs
./gogs web
```

如果您没有发现任何错误信息，则可以使用 `Ctrl-C` 来终止运行。

### 使用标签构建

Gogs 默认并没有支持一些功能，这些功能需要在构建时明确使用构建标签（[build tags](https://golang.org/pkg/go/build/#hdr-Build_Constraints)）来支持。

目前使用标签构建的功能如下：

- `sqlite3`/`tidb`：SQLite3/TiDB 数据库支持
- `redis`/`memcache`：Redis/Memcache 缓存/会话 后端支持
- `pam`：PAM 授权认证支持
- `cert`：生成自定义证书支持

例如，您需要支持以上所有功能，则需要先删除 `$GOPATH/pkg/{GOOS_GOARCH}/github.com/gogits/gogs` 目录，然后执行以下命令：

```sh
$ go get -u -tags "sqlite tidb redis memcache pam cert" github.com/gogits/gogs
$ cd $GOPATH/src/github.com/gogits/gogs
$ go build -tags "sqlite tidb redis memcache pam cert"
```

安装完成后可继续参照 [配置与运行](configuration_and_run.md)。
