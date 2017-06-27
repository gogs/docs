---
name: Configuration et fonctionnement
sort: 7
---

# Configuration et fonctionnement

## Configuration

### Configuration par défault

La configuration par défaut est enregistrée dans `conf/app.ini`, vous **n'avez pas** besoin de modifier la totalité. depuis `v0.6.0`, ce fichier est incorporé au binaire.

### Configuration personnalisé

Comment personnaliser la configuration si vous n'êtes pas autorisé à modifier `conf/app.ini` ? Et bien, créez `custom/conf/app.ini` ! Remplacez ensuite les clefs correspondantes dans `custom/conf/app.ini`.

Par exemple, pour modifier le chemin du dépôt, ajouter quelque chose comme :

```
[repository]
ROOT = /home/jiahuachen/gogs-repositories
```

Vous pouvez également changer le mot de passe de la base de données comme ceci :

```
[database]
PASSWD = root
```

### Pourquoi faisons-nous ça ?

Oui, pourquoi ne pas simplement éditer `conf/app.ini` ? C'est pour vous permettre de garder votre configuration personnalisée en sécurité :

- Pour les personnes qui installent le binaire, chaque fois que vous arrêter le programme, vous pouvez tout simplement copier et coller le fichier de configuration sans rien à re-configurer.
- Pour les personnes qui installent depuis les sources, nous avons exclu le `custom/conf/app.ini` dans `.gitignore`, ainsi les modifications de ce fichier ne sont pas prises en compte lors de la mise à jour.

## Exécuter le serveur Gogs

### Pour développer

- Vous devez définir la clé dans `security -> INSTALL_LOCK` à `true` dans le fichier `custom/conf/app.ini` afin d'exécuter depuis les sources.
- Vous pouvez activer la compilation en temps réel en exécutant `bra run` dans le dossier source de Gogs
	- Installer [bra](https://github.com/Unknwon/bra): `go get -u github.com/Unknwon/bra`

### En production

**Les scripts sont dans le dossier `scripts`, mais il faut les exécuter depuis la racine du dépôt**

- Il y a 3 façons de démarrer par défaut :
	- Simple: il suffit d'exécuter `./gogs web`
	- Supervisord:
		- Start: `./scripts/gogs_supervisord.sh start`
		- Stop: `./scripts/gogs_supervisord.sh stop`
		- Restart: `./scripts/gogs_supervisord.sh restart`
- Ouvrez l'URL `/install` pour faire votre créer votre configuration la première fois.
