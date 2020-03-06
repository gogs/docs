---
name: 下载安装
---

## 环境要求

- 数据库（选择以下一项）：
    - [MySQL](http://dev.mysql.com)：版本 >= 5.7
    - [PostgreSQL](http://www.postgresql.org/)
    - [TiDB](https://github.com/pingcap/tidb)（实验性支持，使用 MySQL 协议连接）
    - 或者 **什么都不安装** 直接使用 SQLite3
- [git](http://git-scm.com/)（bash）：
    - 服务端和客户端均需版本 >= 1.8.3
    - Windows 系统建议使用最新版
- SSH 服务器：
    - **如果您只使用 HTTP/HTTPS 的话请忽略此项**
    - 如果您选择在 Windows 系统使用内置 SSH 服务器，请确保添加 `ssh-keygen` 到您的 `%PATH%` 环境变量中
    - 推荐 Windows 系统使用 [Cygwin OpenSSH](http://docs.oracle.com/cd/E24628_01/install.121/e22624/preinstall_req_cygwin_ssh.htm) 或 [Copssh](https://www.itefix.net/copssh)
    - Windows 系统 请确保 Bash 是默认的 Shell 程序，而不是 PowerShell

### 安装数据库

请根据您的选择进行安装：

- [MySQL](http://dev.mysql.com/downloads/mysql/)（引擎：INNODB）
- [PostgreSQL](http://www.postgresql.org/download/)

**注意事项** 您可以使用 `etc/mysql.sql` 来自动创建名为 `gogs` 的数据库。如果您选择手动创建，请务必将编码设置为 `utf8mb4`。

### 安装其它要求

#### Mac OS X

假设您已经安装 [Homebrew](http://brew.sh/)：

```sh
$ brew update
$ brew install git
```

#### Debian/Ubuntu

```sh
$ sudo apt-get update
$ sudo apt-get install git
```

#### Windows

[下载并安装 Git](http://git-scm.com/downloads)

## 安装 Gogs

- [二进制安装](http://gogs.io/docs/installation/install_from_binary.html)
- [源码安装](http://gogs.io/docs/installation/install_from_source.html)
