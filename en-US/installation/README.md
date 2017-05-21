---
name: Installation
---

## Prerequisites

- Database (choose one of following):
    - [MySQL](http://dev.mysql.com): Version >= 5.5.3
    - [PostgreSQL](http://www.postgresql.org/)
    - [MSSQL](https://en.wikipedia.org/wiki/Microsoft_SQL_Server)
    - [TiDB](https://github.com/pingcap/tidb) (experimental, connect by MySQL protocol)
    - or **NOTHING** with SQLite3
- [Git](http://git-scm.com/) (bash):
    - Version >= 1.7.2 for both server and client sides
    - Best to use latest version for Windows
- A functioning SSH server:
    - **Ignore this if you're only going to use HTTP/HTTPS or use builtin SSH server**
    - Recommend [Cygwin OpenSSH](http://docs.oracle.com/cd/E24628_01/install.121/e22624/preinstall_req_cygwin_ssh.htm) or [Copssh](https://www.itefix.net/copssh) for Windows.

### Install database

Based on your choice, install one of supported databases or skip this step:

- [MySQL](http://dev.mysql.com/downloads/mysql/) (Engine: INNODB)
- [PostgreSQL](http://www.postgresql.org/download/)

**REMEMBER** Please use `scripts/mysql.sql` to create a database called `gogs` (default). If you create it manually, make sure the encoding is `utf8mb4`.

### Install other requirements

#### Mac OS X

Assume you've installed [Homebrew](http://brew.sh/) already:

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

[Download and install Git](http://git-scm.com/downloads)

## Install Gogs

- [Install from binary](/docs/installation/install_from_binary)
- [Install from source](/docs/installation/install_from_source)
