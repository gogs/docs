---
name: A partir des sources
---

# Installer à partir des sources

## Dépendances

### Global

- [Go Programming Language](http://golang.org): Version >= 1.8

Nous allons créer un nouvel utilisateur appelé `git` et installer / configurer tout sous cet utilisateur:

```sh
$ sudo adduser --disabled-login --gecos 'Gogs' git
```

## Installation de Go

Si la distribution de Go incluse dans votre système correspond aux exigences, veuillez ignorer cette section.

### Téléchargement

Installez Go dans `/home/git/local/go` de sorte qu'il n'interfère pas avec les mises à jour futures de la version gérée par votre système d'exploitation :

```sh
$ sudo su - git
$ cd ~
# Créer un dossier pour installer 'go'
$ mkdir local
# Télécharger Go (changer go$VERSION.$OS-$ARCH.tar.gz par la dernière version)
$ wget https://storage.googleapis.com/golang/go$VERSION.$OS-$ARCH.tar.gz
# expand it to ~/local
$ tar -C /home/git/local -xzf go$VERSION.$OS-$ARCH.tar.gz
```

### Configurer l'environnement

Définissez les chemins qui correspondent à votre système :

```sh
$ sudo su - git
$ cd ~
$ echo 'export GOROOT=$HOME/local/go' >> $HOME/.bashrc
$ echo 'export GOPATH=$HOME/go' >> $HOME/.bashrc
$ echo 'export PATH=$PATH:$GOROOT/bin:$GOPATH/bin' >> $HOME/.bashrc
$ source $HOME/.bashrc
```

## Installer Gogs

La façon générale d'installer Gogs :

```sh
# Télécharger et installer les dépendances
$ go get -u github.com/gogs/gogs

# Compiler le programme principal
$ cd $GOPATH/src/github.com/gogs/gogs
$ go build
```

### Compiler depuis la branche `develop`

Dans le cas où vous voulez essayer la branche `develop` :

```sh
$ mkdir -p $GOPATH/src/github.com/gogs
$ cd $GOPATH/src/github.com/gogs

# Assurez vous de ne pas utiliser "https://github.com/gogs/gogs.git"
$ git clone --depth=1 -b develop https://github.com/gogs/gogs
$ cd gogs
$ go build
```

### Tester l'installation

Pour vous assurer que Gogs fonctionne correctement :

```sh
$ cd $GOPATH/src/github.com/gogs/gogs
$ ./gogs web
```

Si vous ne voyez pas de messages d'erreur, appuyez sur `Ctrl-C` pour arrêter Gogs.

### Compiler avec des Tags

Gogs ne fournit pas par défaut certains supports, vous devez compiler Gogs avec le support que vous souhaitez ajouter [build tags](https://golang.org/pkg/go/build/#hdr-Build_Constraints).

Liste des tags disponibles :

- `sqlite3`: Support de la base de données SQLite3
- `pam`: Support de l'authentification PAM
- `cert`: Support de la génération des certificats auto-signés
- `miniwinsvc`: Support des services pour Windows (Vous pouvez aussi utiliser NSSM pour créer un service)

Par exemple, si vous voulez activer tous les tags de la liste, vous devez commencer par supprimer le repertoire `$GOPATH/pkg/${GOOS}_${GOARCH}/github.com/gogs/gogs` et exécuter les commandes suivantes :

```sh
$ go get -u -tags "sqlite pam cert" github.com/gogs/gogs
$ cd $GOPATH/src/github.com/gogs/gogs
$ go build -tags "sqlite pam cert"
```

Si vous avez l'erreur: `fatal error: security/pam_appl.h: No such file or directory`, installez les paquets en exécutant cette commande : `sudo apt-get install libpam0g-dev`.

## Prochaines étapes

- Voir [Configuration and run](configuration_and_run) pour aller plus loin.
- Pour des instructions plus détaillées, y compris sur les paramètres du serveur Web et de la base de données, voir [les étapes détaillées](/docs/advanced/configuration_for_source_builds).
