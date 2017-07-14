---
name: A partir des sources
sort: 2
---

# Installez à partir des sources

## Dépendances

### Global

- [Go Programming Language](http://golang.org): Version >= 1.6
- [Git](http://git-scm.com): Version >= 1.7.1

Nous allons créer un nouvel utilisateur appelé `git` et installer / configurer tout sous cet utilisateur:

`sudo adduser --disabled-login --gecos 'Gogs' git`

### Paquets tiers

Si vous êtes intéressé par les paquets tiers que nous utilisons, voyez [gopmfile](https://github.com/gogits/gogs/blob/master/.gopmfile). Vous pouvez en avoir besoin quand vous construisez un paquet pour Gogs.

## Installation de Go

### Téléchargement

Si la distribution de Go incluse dans votre système correspond aux exigences, veuillez ignorer cette section.

Installez Go dans `/home/git/local/go` de sorte qu'il n'interfère pas avec les mises à jour futures de la version gérée par votre système d'exploitation :

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
# Télécharger et installer les dépendances
$ go get -u github.com/gogits/gogs

# Compiler le programme principal
$ cd $GOPATH/src/github.com/gogits/gogs
$ go build
```

Si vous utilisez gopm, vous pouvez essayer d'installer Gogs de la manière suivante :

```
# Vérification des mises à jour de gopm
$ gopm update -v

# Télécharger et construire le binaire
$ gopm bin -u -v gogs -d path/to/anywhere
```

### Construire depuis la branche `develop`

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

Pour vous assurer que Gogs fonctionne correctement :

```
cd $GOPATH/src/github.com/gogits/gogs
./gogs web
```

Si vous ne voyez pas de messages d'erreur, appuyez sur `Ctrl-C` pour arrêter Gogs.

### Construisez avec SQLite3/Redis/Memcache

Si vous devez activer SQLite3/Redis/Memcache, supprimez le répertoire `$GOPATH/pkg/{GOOS_GOARCH}/github.com/gogits/gogs` et exécutez :

```
$ go get -u -tags "sqlite redis memcache" github.com/gogits/gogs
$ cd $GOPATH/src/github.com/gogits/gogs
$ go build -tags "sqlite redis memcache"
```

## Prochaines étapes

- Voir [Configuration and run](configuration_and_run) pour aller plus loin.
- Pour des instructions plus détaillées, y compris sur les paramètres du serveur Web et de la base de données, voir [les étapes détaillées](/docs/advanced/configuration_for_source_builds).
