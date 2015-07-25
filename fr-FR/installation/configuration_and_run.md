---
name: Configuration et fonctionnement
sort: 7
---

# Configuration et fonctionnement

## Configuration

### Configuration par défault

La configuration par défaut est enregistré dans `conf/app.ini`, vous **n'**avez **pas** besoin de modifier la totalité. depuis `v0.6.0`, ce fichier est incorporé en binaire.

### Configuration personnalisé

Alors, comment faire la configuration personnalisée si vous n'êtes pas autorisé à modifier `conf/app.ini` ? Et bien, créer `custom/conf/app.ini` ! Remplacer les clefs correspondantes dans la section correspondante dans `custom/conf/app.ini`.

Par exemple, pour modifier le chemin de la racine de l'endroit où les données brutes dépôt étant stockées, ajouter quelque chose comme :

```
[repository]
ROOT = /home/jiahuachen/gogs-repositories
```

Bien sûr, vous pouvez changer le réglage de base de données ainsi :

```
[database]
PASSWD = root
```

### Pourquoi faisons-nous ça ?

Oui, pourquoi ne pas simplement éditer `conf/app.ini` ? La raison en est que pour garder votre configuration personnalisée en sécurité :

- Pour les personnes qui installent le binaire, chaque fois après vous arrêter le programme, peut tout simplement copier et coller sans que rien ne re-configure.
- Pour les personnes qui installent de la source, nous avons exclu le `custom/conf/app.ini` dans `.gitignore` afin de ne pas causer des changements dans le contrôle de version que vous avez à faire autres choses avant la mise à jour.

## Exécuter le serveur Gogs

### Pour développer

- Vous devez définir la clé dans `security -> INSTALL_LOCK` et être à `true` dans le fichier `custom/conf/app.ini` afin d'exécuter la source.
- Vous pouvez activer en temps réel la compilation en exécutant `bra run` dans le dossier source de Gogs
	- Installer [bra](https://github.com/Unknwon/bra): `go get -u github.com/Unknwon/bra`

### Pour déploiement

**Les scripts sont dans le dossier `scripts`, mais il faut les exécuter à la racine du dépôt**

- Il y a 3 façons de démarrer par défaut :
	- Plain: suffit d'utiliser `./gogs web`
	- Supervisor:
		- Start: `./scripts/gogs_supervisord.sh start`
		- Stop: `./scripts/gogs_supervisord.sh stop`
		- Restart: `./scripts/gogs_supervisord.sh restart`
- Allez dans `/install` pour faire votre configuration d'exécution pour la première fois.
