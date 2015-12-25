---
name: 下载安装
---

## 环境要求

- 数据库（选择以下一项）：
    - [MySQL](http://dev.mysql.com)：版本 >= 5.5.3
    - [PostgreSQL](http://www.postgresql.org/)
    - 或者 **什么都不安装** 直接使用 SQLite3 或 TiDB
- [git](http://git-scm.com/)（bash）：
    - 服务端和客户端均需版本 >= 1.7.1
    - Windows 系统建议使用最新版
- SSH 服务器：
    - **如果您只使用 HTTP/HTTPS 或者内置 SSH 服务器的话请忽略此项**
    - 推荐 Windows 系统使用 [Cygwin OpenSSH](http://docs.oracle.com/cd/E24628_01/install.121/e22624/preinstall_req_cygwin_ssh.htm) 或 [Copssh](https://www.itefix.net/copssh)

### 安装数据库

Gogs 支持 MySQL、PostgreSQL、SQLite3 和 TiDB（实验性支持），请根据您的选择进行安装：

- [MySQL](http://dev.mysql.com/downloads/mysql/)（引擎：INNODB）
- [PostgreSQL](http://www.postgresql.org/download/)

**注意事项** 您可以使用 `etc/mysql.sql` 来自动创建名为 `gogs` 的数据库。如果您选择手动创建，请务必将编码设置为 `utf8mb4`。

### 安装其它要求

#### Max OS X

假设您已经安装 [Homebrew](http://brew.sh/)：

```
$ brew update
$ brew install git
```

#### Debian/Ubuntu

```
$ sudo apt-get update
$ sudo apt-get install git
```

#### Windows

[下载并安装 Git](http://git-scm.com/downloads)

## 安装 Gogs

- [二进制安装](http://gogs.io/docs/installation/install_from_binary.html)
- [源码安装](http://gogs.io/docs/installation/install_from_source.html)
