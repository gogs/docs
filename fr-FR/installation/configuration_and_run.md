---
name: configuration et lancement
---

# Configuration et lancement

## Configuration

### Configuration par défaut

La configuration par défaut est sauvegardée dans `conf/app.ini` : il ne faut **absolument** pas l'éditer . Depuis la version `v0.6.0`, ce fichier est inclus avec le binaire.

### Configuration personalisée

Alors, comment créer une configuration personalisée si on ne peut pas modifier `conf/app.ini`? En bien en créant `custom/conf/app.ini` ! Les entrées et les valeurs des différentes sections de `custom/conf/app.ini` vont remplacer les valeurs correspondantes de `conf/app.ini`.

Par exemple, pour changer l'emplacement racine des dépôts `git`, il suffit d'ajouter quelque chose comme ça :

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

Oui, pourquoi ne pas simplement éditer `conf/app.ini`? Tout simplement pour garder votre personnalisation en sécurité.

- Pour ceux qui utilisent l'installation binaire, après avoir lancé le programme, il suffit de faire un copier-coller sans rien d'autre à reconfigurer
- Pour ceux qui installent depuis les sources, nous avons exclu `custom/conf/app.ini` en l'indiquant dans `.gitignore`, donc les modifications apportées ne créent pas de changements tracés par `git` et n'obligent pas à gérer des branches ou des patches avant de faire une mise à jour.

## Lancer Gogs server

### Pour les développeurs

- Vous devez mettre l'entrée `security -> INSTALL_LOCK` à `true` dans le fichier `custom/conf/app.ini` pour pouvoir lancer Gogs depuis les sources.
- Vous pouvez utilisez l'excellente commande `make` :

	```sh
$ make
$ ./gogs web
	```
	
- Vous pouvez faire une compilation live en exécutant `bra run` dans de dossier source Gogs
	- Pour installer [bra](https://github.com/Unknwon/bra): `go get -u github.com/Unknwon/bra`

### Déploiement

**Les scripts sont dans le dossier `scripts` mais doivent être exécutés depuis la racine du dossier**

- Il y a plusieurs manières de démarrer Gogs :
	- Directiement : simplement `./gogs web`
	- Daemon : voir le dossier [scripts](https://github.com/gogits/gogs/tree/master/scripts)
- Aller sur la page `/install` pour effectuer la configuration lors du premier lancement
