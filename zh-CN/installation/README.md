---
root: true
name: 下载安装
sort: 1
---

## 环境要求

- [MySQL](http://dev.mysql.com)：版本 >= 5.1 或者 [PostgreSQL](http://www.postgresql.org/) 或者 **什么都不需要**。
- [git](http://git-scm.com/)（bash）：版本 >= 1.6.6（服务端和客户端均需）

### 安装数据库

Gogs 支持 MySQL、PostgreSQL 和 SQLite3，请根据您的选择进行安装：

- [MySQL](http://dev.mysql.com/downloads/mysql/)（ 引擎：INNODB）
- [PostgreSQL](http://www.postgresql.org/download/)

**注意事项** 您可以使用 `conf/mysql.sql` 来自动创建名为 `gogs` 的数据库。如果您选择手动创建，请务必将编码设置为 `utf8`。
 
### 安装其它要求

#### Max OS X

假设您已经安装 [Homebrew](http://brew.sh/)：

```
$ brew update
$ brew install git
```

#### Linux

```
$ sudo apt-get update
$ sudo apt-get install git
```

#### Windows

[下载并安装 Git](http://git-scm.com/downloads)

## 安装 Gogs

- [二进制安装](install_from_binary.md)
- [源码安装](install_from_source.md)