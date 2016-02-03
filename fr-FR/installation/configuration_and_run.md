---
name: Configuration et lancement
---

# Configuration et lancement

## Configuration

### Configuration par défaut

La configuration par défaut est sauvegardée dans `conf/app.ini` : vous n'avez **AUCUN** besoin de l'éditer . Depuis la version `v0.6.0`, ce fichier est inclus avec le bianire.

### Configuration personalisée

Alors, comment créer une configuration personalisée si on ne peut pas modifier `conf/app.ini`? En bien en créant `custom/conf/app.ini` ! Les balises placées dans les différentes sections de `custom/conf/app.ini` vont remplacer les valeurs correspondantes de `conf/app.ini`.

Par exemple, pour changer l'emplacement racine de tous les dépôts git, il suffit d'ajouter quelque chose comme ça :

```
[repository]
ROOT = /home/dupond/gogs-repositories
```

Bien sûr, on peut également changer les paramètres de la base de données :

```
[database]
PASSWD = root
```

### Pourquoi tout ça ?

Oui, pourquoi ne pas simplement éditer `conf/app.ini`? Tout simplement pour garder votre config perso en sécurité.

- Pour ceux qui utilisent l'installation binaire, après avoir lancer le programme, il suffit de faire un copier-coller sans rien d'autre à reconfigurer
- Pour ceux qui installent depuis les sources, nous avons exclus `custom/conf/app.ini` dans `.gitignore`, donc les modifications apportées ne créent pas de changements tracés par Git et n'obligent pas à gérer des branches ou des patches avant de faire une mise à jour.

## Lancer Gogs server

### Pour les développeurs

- Vous devez mettre l'entrée `security -> INSTALL_LOCK` à `true` dans le fichier `custom/conf/app.ini` pour pouvoir lancer depuis les sources.
- Vous pouvez utilisez l'excellente commande `make` :

	```sh
$ make
$ ./gogs web
	```
	
- Vous pouvez faire une compilation live en exécutant `bra run` dans de dossier source Gogs
	- Pour installer [bra](https://github.com/Unknwon/bra): `go get -u github.com/Unknwon/bra`

### Déploiement

** Les scripts sont dans le dossier `scripts` mais doivent être exécutés depuis la racine du dossier **

- Il y a plusieurs manières de démarrer Gogs :
	- Direct: simplement `./gogs web`
	- Daemons: voir le dossier [scripts](https://github.com/gogits/gogs/tree/master/scripts)
- Aller sur la page `/install` pour effectuer la configuration lors du premier lancement
