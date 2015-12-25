---
root: true
name: Installation
sort: 1
---

## Exigences

- [MySQL](http://dev.mysql.com): Version >= 5.5.3 ou [PostgreSQL](http://www.postgresql.org/) ou **RIEN**
- [git](http://git-scm.com/)(bash): Version >= 1.7.1 (à la fois serveur et client)
- Un serveur SSH en fonctionnement (**ignorer si vous ne utilisez que HTTP / HTTPS**)
    - Recommandé [Cygwin OpenSSH](http://docs.oracle.com/cd/E24628_01/install.121/e22624/preinstall_req_cygwin_ssh.htm) sous Windows.

### Installation de la base de donnée

Gogs supporte MySQL, PostgreSQL et SQLite3, en fonction de votre choix, installer l'un d'eux ou sauter cette étape :

- [MySQL](http://dev.mysql.com/downloads/mysql/) (Engine: INNODB)
- [PostgreSQL](http://www.postgresql.org/download/)

**RAPPELEZ-VOUS** utilisez `etc/mysql.sql` pour créer une base de données appelée `gogs`(defaut). Si vous la créez manuellement, assurez-vous que l'encodage est `utf8mb4`.

### Installation de d'autres besoin
#### Max OS X

Supposons que vous avez déjà installé [Homebrew](http://brew.sh/) :

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

[Télécharger et installer Git](http://git-scm.com/downloads)

## Installer Gogs

- [Installer le binaire](http://gogs.io/docs/installation/install_from_binary.html)
- [Installer avec les sources](http://gogs.io/docs/installation/install_from_source.html)
