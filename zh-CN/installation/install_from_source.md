---
name: 源码安装
sort: 2
---

# 源码安装

## 安装依赖

### 基本依赖

- [Go 语言](http://golang.org)：版本 >= 1.2
- [Git](http://git-scm.com)：版本 >= 1.7.1

### 第三方包

请通过 [gopmfile](https://github.com/gogits/gogs/blob/master/.gopmfile) 查看完整的第三方包依赖列表。一般情况下只有在您为 Gogs 制作构建包的时候才会用到。

## 安装 Go 语言

### 下载

如果您的系统已经安装要求版本的 Go 语言，可以跳过此小节。

您可以通过以下方式安装 Go 语言到 `/home/git/local/go` 目录：

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

### 设置环境

请设置和您系统环境对应的路径：

```bash
sudo su - git
cd ~
echo 'export GOROOT=$HOME/local/go' >> $HOME/.bashrc
echo 'export GOPATH=$HOME/go' >> $HOME/.bashrc
echo 'export PATH=$PATH:$GOROOT/bin:$GOPATH/bin' >> $HOME/.bashrc
source $HOME/.bashrc
```

## 安装 Gogs

常用的安装方式：

```
# 下载并安装依赖
$ go get -u github.com/gogits/gogs

# 构建主程序
$ cd $GOPATH/src/github.com/gogits/gogs
$ go build
```

如果您已经安装 gopm，则可以尝试使用以下方式安装：

```
# 检查更新 Gopm
$ gopm update -v

# 下载并构建二进制
$ gopm bin -u -v gogs -d path/to/anywhere
```

### 构建 `develop` 分支版本

如果您想要安装 `develop` 分支版本，则可以通过以下命令：

```
$ mkdir -p $GOPATH/src/github.com/gogits
$ cd $GOPATH/src/github.com/gogits
$ git clone -b develop https://github.com/gogits/gogs.git
$ cd gogs
$ go get ./...
$ go build
```

### 测试安装

您可以通过以下方式检查 Gogs 是否可以正常工作：

```
cd $GOPATH/src/github.com/gogits/gogs
./gogs web
```

如果您没有发现任何错误信息，则可以使用 `Ctrl-C` 来终止运行。

### 构建 SQLite3/Redis/Memcache 集成版

如果您想要启动 SQLite3/Redis/Memcache 请先删除 `$GOPATH/pkg/{GOOS_GOARCH}/github.com/gogits/gogs` 目录，然后：

```
$ go get -u -tags "sqlite redis memecache" github.com/gogits/gogs
$ cd $GOPATH/src/github.com/gogits/gogs
$ go build -tags "sqlite redis memecache"
```

安装完成后可继续参照 [配置与运行](configuration_and_run.md)。
