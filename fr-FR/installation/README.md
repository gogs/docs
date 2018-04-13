---
name: Installation
---

## Prérequis

- Base de données (choisissez en une dans cette liste) :
    - [MySQL](http://dev.mysql.com) : Version >= 5.7
    - [PostgreSQL](http://www.postgresql.org/)
    - [MSSQL](https://fr.wikipedia.org/wiki/Microsoft_SQL_Server)
    - [TiDB](https://github.com/pingcap/tidb) (expérimental, utilisez le protocole MySQL pour vous connecter)
    - ou **RIEN** avec SQLite3
- [Git](http://git-scm.com/) (bash) :
    - Version >= 1.7.1 pour le serveur et le client
    - Il est conseillé d'utiliser la dernière version pour Windows
- Un serveur SSH fonctionnel :
    - **Ignorez cette étape si vous utilisez seulement la connexion HTTP/HTTPS ou si vous utilisez un serveur SSH interne**
    - Recommandé [Cygwin OpenSSH](http://docs.oracle.com/cd/E24628_01/install.121/e22624/preinstall_req_cygwin_ssh.htm) ou [Copssh](https://www.itefix.net/copssh) pour Windows.

### Installation de la base de données

En fonction de votre choix, installez l'un d'entre eux ou passez cette étape :

- [MySQL](http://dev.mysql.com/downloads/mysql/) (Moteur de stockage : INNODB)
- [PostgreSQL](http://www.postgresql.org/download/)

**RAPPELEZ-VOUS** Utilisez le script `scripts/mysql.sql` pour créer une base de données appelée `gogs` (par défaut). Si vous la créez manuellement, assurez-vous que l'encodage utilisé est `utf8mb4`.

### Installation des autres exigences

#### Mac OS X

Supposons que vous avez déjà installé [Homebrew](http://brew.sh/) :

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

[Télécharger et installer Git](http://git-scm.com/downloads)

## Installation de Gogs

- [Installation à partir des binaires](/docs/installation/install_from_binary)
- [Installation à partir des sources](/docs/installation/install_from_source)
