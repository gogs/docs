---
name: A partir des sources
sort: 2
---

# Installez à partir des sources

## Dépendances

### Global

- [Go Programming Language](http://golang.org): Version >= 1.4
- [Git](http://git-scm.com): Version >= 1.7.1

Nous allons créer un nouvel utilisateur appelé `git` et installer / configurer tout sous cet utilisateur:

`sudo adduser --disabled-login --gecos 'Gogs' git`

### Paquets tierces

Si vous êtes intéressé dans lequel une tierce partie paquets que nous utilisons, voir [gopmfile](https://github.com/gogits/gogs/blob/master/.gopmfile). Vous pouvez en avoir besoin quand vous faites une construction du paquet pour Gogs.

## Installation de Go

### Téléchargement

Si Go de votre système correspond aux exigences sauter cette section.

Installez Go dans `/home/git/local/go` de sorte qu'il ne serait pas interférer avec les mises à jour futures du paquet le gestionnaire de votre système :

```bash
sudo su - git
cd ~
# create a folder to install 'go'
mkdir local
# Download go (change go$VERSION.$OS-$ARCH.tar.gz to the latest release)
wget https://storage.googleapis.com/golang/go$VERSION.$OS-$ARCH.tar.gz
# expand it to ~/local
tar -C /home/git/local -xzf go$VERSION.$OS-$ARCH.tar.gz
```

### Configuration de l'environnement

Définissez les chemins qui correspondent à votre système :

```bash
sudo su - git
cd ~
echo 'export GOROOT=$HOME/local/go' >> $HOME/.bashrc
echo 'export GOPATH=$HOME/go' >> $HOME/.bashrc
echo 'export PATH=$PATH:$GOROOT/bin:$GOPATH/bin' >> $HOME/.bashrc
source $HOME/.bashrc
```

## Installation Gogs

La façon générale d'installer Gogs, 

```
# Download and install dependencies
$ go get -u github.com/gogits/gogs

# Build main program
$ cd $GOPATH/src/github.com/gogits/gogs
$ go build
```

Si vous avez gopm disponible, vous pouvez essayer de la manière suivante pour installer Gogs :

```
# Check update of gopm
$ gopm update -v

# Download and build binary
$ gopm bin -u -v gogs -d path/to/anywhere
```

### Construit depuis la branche `develop`

Dans le cas où vous voulez essayer la branche `develop` :

```
$ mkdir -p $GOPATH/src/github.com/gogits
$ cd $GOPATH/src/github.com/gogits
$ git clone --depth=1 -b develop https://github.com/gogits/gogs.git
$ cd gogs
$ go get ./...
$ go build
```

### Test d'installation

Pour vous assurer que fonctionne Gogs :

```
cd $GOPATH/src/github.com/gogits/gogs
./gogs web
```

Si vous ne voyez pas les messages d'erreur, appuyez sur `Ctrl-C` pour arrêter Gogs.

### Construisez avec SQLite3/Redis/Memcache

Si vous devez activer SQLite3/Redis/Memcache, s'il vous plaît supprimer le répertoire `$GOPATH/pkg/{GOOS_GOARCH}/github.com/gogits/gogs` et fait :

```
$ go get -u -tags "sqlite redis memcache" github.com/gogits/gogs
$ cd $GOPATH/src/github.com/gogits/gogs
$ go build -tags "sqlite redis memcache"
```

## Prochaines étapes

- Voir [Configuration and run](configuration_and_run.md) pour aller plus loin.
- Pour des instructions plus détaillées, y compris les paramètre du serveur Web et de la base de données, voir [les étapes détaillées](/docs/advanced/configuration_for_source_builds.md).
