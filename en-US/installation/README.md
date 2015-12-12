---
name: Installation
---

## Prerequisites

- Database (choose one of following):
    - [MySQL](http://dev.mysql.com): Version >= 5.1
    - [PostgreSQL](http://www.postgresql.org/)
    - or **NOTHING** with SQLite3 or TiDB (experimental)
- [Git](http://git-scm.com/) (bash):
    - Version >= 1.7.1 for both server and client sides
    - Best to use latest version for Windows
- A functioning SSH server:
    - **Ignore this if you're only going to use HTTP/HTTPS or use builtin SSH server**
    - Recommend [Cygwin OpenSSH](http://docs.oracle.com/cd/E24628_01/install.121/e22624/preinstall_req_cygwin_ssh.htm) or [Copssh](https://www.itefix.net/copssh) for Windows.

### Install Database

Gogs supports MySQL, PostgreSQL, SQLite3 and TiDB. Based on your choice, install either one of them or skip this step:

- [MySQL](http://dev.mysql.com/downloads/mysql/) (Engine: INNODB)
- [PostgreSQL](http://www.postgresql.org/download/)

**REMEMBER** Please use `etc/mysql.sql` to create a database called `gogs` (default). If you create it manually, make sure the encoding is `utf8`.

### Install other requirements

#### Max OS X

Assume you've installed [Homebrew](http://brew.sh/) already:

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

[Download and install Git](http://git-scm.com/downloads)

## Install Gogs

- [Install from binary](/docs/installation/install_from_binary)
- [Install from source](/docs/installation/install_from_source)
