---
name: Ubuntu 安装
sort: 3
---

## 在 Ubuntu 14.04 LTS 上二进制安装

### 创建用户及安装依赖

- sudo adduser git
- sudo apt-get update
- sudo apt-get upgrade
- sudo apt-get install git
- sudo apt-get install mysql-server

### 创建数据库

- $mysql -u root -p
- mysql> SET GLOBAL storage_engine = 'InnoDB';
- mysql> CREATE DATABASE gogs CHARACTER SET utf8 COLLATE utf8_bin;
- mysql> GRANT ALL PRIVILEGES ON gogs.* TO 'root'@'localhost' IDENTIFIED BY 'password';
- mysql> FLUSH PRIVILEGES;
- mysql> QUIT

### 安装 Gogs

- mkdir gogs
- cd gogs
- curl -L http://gobuild.io/github.com/gogits/gogs/v0.3.0/linux/amd64 -o v0.3.0.zip
- unzip v0.3.0.zip
- ./start.sh

> 最新版二进制可以在该链接获取：
> http://gobuild.io/download/github.com/gogits/gogs

## 在 Ubuntu 14.04 LTS 32bit 上从源码安装

### 环境要求

- Go 语言：版本 >= 1.2
- Git（bash）：版本 >= 1.6.6（服务端和客户端均需）
- MySQL：版本 >= 5.1 或者 PostgreSQL 或者 **什么都不需要**。

### 创建用户 git

- sudo adduser git
- su git

### 安装 Git 与 Mysql-server

- sudo apt-get install git
- sudo apt-get install mysql-server

### 创建数据库

- $ mysql -u root -p
- mysql> SET GLOBAL storage_engine = 'InnoDB';
- mysql> CREATE DATABASE gogs CHARACTER SET utf8 COLLATE utf8_bin;
- mysql> GRANT ALL PRIVILEGES ON gogs.* TO 'root'@'localhost' IDENTIFIED BY 'pasword';
- mysql> FLUSH PRIVILEGES;
- mysql> QUIT

### 从源码安装 Go 语言

- sudo apt-get install build-essential 
- sudo apt-get install mercurial
- hg clone -r release https://go.googlecode.com/hg/ /home/git/golang/
 

- echo export GOROOT=/home/git/golang >>.bashrc
- echo export GOARCH=386   >>.bashrc 
- echo export GOOS=linux  >>.bashrc 
- echo export GOBIN= /home/git/golang/bin  >>.bashrc 
- echo export GOPATH=$HOME/app/Go   >>.bashrc 
- echo  PATH=${PATH}: /$HOME/golang/bin  >>.bashrc
- cd $GOROOT/src
- ./make.bash

### 下载安装依赖

- $ go get -u github.com/gogits/gogs

### 构建主程序

- $ cd $GOPATH/src/github.com/gogits/gogs
- $ go build
- $ ./start.sh

#### 现在，您可以访问 http://localhost:3000 来使用 Gogs 了

