---
name: 源码安装
---

# 源码安装

## 安装依赖

### 基本依赖

- [Go 语言](http://golang.org)：版本 >= 1.7

## 安装 Go 语言

如果您的系统已经安装要求版本的 Go 语言，可以跳过此小节。

### 下载

您可以通过以下方式安装 Go 语言到 `/home/git/local/go` 目录：

```sh
sudo su - git
cd ~
# create a folder to install 'go'
mkdir local
# Download go (change go$VERSION.$OS-$ARCH.tar.gz to the latest release)
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
$ go get -u github.com/gogs/gogs

# 构建主程序
$ cd $GOPATH/src/github.com/gogs/gogs
$ go build
```

### 构建 `develop` 分支版本

如果您想要安装 `develop`（或其它）分支版本，则可以通过以下命令：

```sh
$ mkdir -p $GOPATH/src/github.com/gogs
$ cd $GOPATH/src/github.com/gogs

# 请确保没有使用 “https://github.com/gogs/gogs.git”
$ git clone --depth=1 -b develop https://github.com/gogs/gogs
$ cd gogs
$ go build
```

### 测试安装

您可以通过以下方式检查 Gogs 是否可以正常工作：

```sh
cd $GOPATH/src/github.com/gogs/gogs
./gogs web
```

如果您没有发现任何错误信息，则可以使用 `Ctrl-C` 来终止运行。

### 使用标签构建

Gogs 默认并没有支持一些功能，这些功能需要在构建时明确使用构建标签（[build tags](https://golang.org/pkg/go/build/#hdr-Build_Constraints)）来支持。

目前使用标签构建的功能如下：

- `sqlite3`：SQLite3 数据库支持
- `pam`：PAM 授权认证支持
- `cert`：生成自定义证书支持
- `miniwinsvc`：Windows 服务内置支持（或者您可以使用 NSSM 来创建服务）

例如，您需要支持以上所有功能，则需要先删除 `$GOPATH/pkg/{GOOS_GOARCH}/github.com/gogs/gogs` 目录，然后执行以下命令：

```sh
$ go get -u -tags "sqlite pam cert" github.com/gogs/gogs
$ cd $GOPATH/src/github.com/gogs/gogs
$ go build -tags "sqlite pam cert"
```

安装完成后可继续参照 [配置与运行](configuration_and_run.html)。
