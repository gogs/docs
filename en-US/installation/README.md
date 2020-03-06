---
name: Installation
---

## Prerequisites

- Database (choose one of the following):
    - [MySQL](http://dev.mysql.com): Version >= 5.7
    - [PostgreSQL](http://www.postgresql.org/)
    - [TiDB](https://github.com/pingcap/tidb) (experimental, connect via the MySQL protocol)
    - or **NOTHING** with SQLite3
- [Git](http://git-scm.com/) (bash):
    - Version >= 1.8.3 for both server and client sides
    - Best to use latest version for Windows
- A functioning SSH server:
    - **Ignore this if you're only going to use HTTP/HTTPS**
    - For using builtin SSH server on Windows, make sure you added `ssh-keygen` to your `%PATH%` environment variable.
    - For using standalone SSH server, recommend [Cygwin OpenSSH](http://docs.oracle.com/cd/E24628_01/install.121/e22624/preinstall_req_cygwin_ssh.htm) or [Copssh](https://www.itefix.net/copssh) for Windows.
    - For Windows servers, please make sure Bash is the default shell not PowerShell.

### Install database

Based on your choice, install one of the supported databases (or skip this step):

- [MySQL](http://dev.mysql.com/downloads/mysql/) (Engine: INNODB)
- [PostgreSQL](http://www.postgresql.org/download/)

**REMEMBER** Please use `scripts/mysql.sql` to create a database called `gogs` (default). If you create it manually, make sure the encoding is `utf8mb4`.

### Install additional requirements

#### Mac OS X

Assuming you have [Homebrew](http://brew.sh/) already installed:

```sh
$ brew update
$ brew install git
```

#### Debian/Ubuntu

```sh
$ sudo apt-get update
$ sudo apt-get install git
```

#### Fedora

```sh
$ sudo dnf update
$ sudo dnf install git
```

#### RHEL/CentOS

```sh
$ sudo yum update
$ sudo yum install git
```


#### Windows

[Download and install Git](http://git-scm.com/downloads)

## Install Gogs

- [Install from binary](/docs/installation/install_from_binary)
- [Install from source](/docs/installation/install_from_source)
