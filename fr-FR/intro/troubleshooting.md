---
name: Dépannage
sort: 2
---

# Dépannage

## Installation

- Erreur : `../gosrc/src/github.com/gogits/gogs/cmd/cert.go:79: undefined: elliptic.P224`
- Causes : Le paquet golang dans RHEL/CentOS ne supporte pas la cryptographie à courbe elliptique (car il est breveté), cette fonctionnalité est retirée spécifiquement du build CentOS/RHEL.
- Solution : Télécharger et installer Go à partir de [golang.org/dl](http://golang.org/dl).

## Git

- Erreur : `bash /path/to/gogs: no such file or directory`
- Causes : Vous avez modifié l'emplacement du serveur Gogs mais l'ancien chemin a été codé en dur dans le fichier `~/.ssh/authorized_keys`.
- Solution : Exécuter `./gogs fix location <old Gogs path>` depuis le nouveau répertoire Gogs.

-----

- Erreur :
	- `fatal: 'XX/XX.git' does not appear to be a git repository`
	- Commits pushed mais présente toujours comme un dépôt vide
- Causes : Il y a des clés SSH dupliquées dans le fichier `~/.ssh/authorized_keys`, peut-être utilisez vous (ou avez utilisé) GitLab avec le même utilisateur système.
- Solution : Supprimer l'ancien fichier `~/.ssh/authorized_keys` et garder seulement la version ajoutée par Gogs.

-----

- Erreur : `repo.NewRepoContext(fail to set git user.emil):`
- Causes : Cela arrive quand les utilisateurs de Windows installent Git Bash sans activer l'option `cmd`.
- Solution : Réinstaller et activer l'option `cmd`.

## Validation de formulaire

- Erreur : `Repository/User name contains illegal characters`
- Causes : Afin d'éviter les exceptions, votre utilisateur / nom du dépôt sera considéré comme illégal si il correspond à l'une des règles suivantes :
	- Nom parmi `"raw", "install", "api", "avatar", "user", "org", "help", "stars", "issues", "pulls", "commits", "repo", "template", "admin", "new"`.
	- Nom ayant le suffix `".git"`.

## Cache

- Erreur : `cache: unknown adaptername "memcache" (importation oublié?)`
- Causes : Pour empêcher l'importation inutiles du paquet, nous des tags à la construction pour spécifier si c'est nécessaire.
- Solution :
	- Téléchargement : `go get -tags memcache github.com/gogits.gogs`
	- Construction : `go build -tags memcache`
	- Suivre les mêmes étapes pour `redis` quand vous voulez qu'il soit l'adaptateur de cache.

## MySQL

- Erreur : `Error 1071: Specified key was too long; max key length is 1000 bytes`
- Causes : Elle est causée par MyISAM.
- Solution : Une fois fichier `config/mysql.sql` importé connectez-vous à MySQL et lancer :

	```sql
	use gogs;
	set global storage_engine=INNODB;
	```

Après cela, allez à [http://localhost:3000/install](http://localhost:3000/install) et tout devrait fonctionner correctement (merci à [@linc01n](https://github.com/linc01n)).

-----

- Erreur : `Database setting is not correct: This server only supports the insecure old password authentication. If you still want to use it, please add 'allowOldPasswords=1' to your DSN. See also https://github.com/go-sql-driver/mysql/wiki/old_passwords`
- Causes : Le mot de passe a été mis à jour seulement pour l'utilisateur @localhost -- il y a une seconde entrée de la table d'utilisateur @% pour laquelle le mot de passe est encore l'ancien.
- Solution : [Un commentaire GitHub](https://github.com/gogits/gogs/issues/385#issuecomment-54357073)

## Logiciel de messagerie

- Erreur : Gmail avec erreur 534: `Please log in via your web browser and then try again`
- Causes : Cela est parce que Google ne fait pas confiance à votre serveur.
- Solution :
	- Visitez https://accounts.google.com et connectez-vous.
	- Allez sur https://accounts.google.com/DisplayUnlockCaptcha cliquez sur `continue`.
	- Maintenant copier le lien qui ressemble à ceci (l'invite du journal du serveur Gogs) : https://accounts.google.com/ContinueSignIn?sarp=1&scc=1&plt=AKgnsbvPPN_E_25__nyS*******f18O9uuLNtz0Imw et connectez-vous à nouveau.
	- Les choses devraient maintenant fonctionner. Enfin, vérifiez votre boîte `spam` dans le cas où votre fournisseur de service de messagerie penserait que gmail est un spammeur.

## Windows

- Erreur :

```
2014/09/18 15:04:40 [repo.go:115 CreatePost()] [E] CreatePost: initRepository: initRepository(git clone): cygwin warning:
MS-DOS style path detected: C:\Users\user\gogs-repositories\unos\test3.git/.git
Preferred POSIX equivalent is: /cygdrive/c/Users/user/gogs-repositories/unos/test3.git/.git
CYGWIN environment variable option "nodosfilewarning" turns off this warning.
Consult the user's guide for more details about POSIX paths:
http://cygwin.com/cygwin-ug-net/using.html#using-pathnames
Cloning into 'C:\Users\user\AppData\Local\Temp\484264900'...
fatal: '/cygdrive/d/svnroot/research/gogs/C:\Users\user\gogs-repositories\unos\test3.git' does not appear to be a git repository
fatal: Could not read from remote repository.
```

- Causes : Vous installez le système dans un shell qui a une arborescence différente de celle par défaut.
- Solution : Démarrez Gogs avec les options par défaut de CMD.

## Autre

- Erreur : Les pages répondent extrêment lentement, mais le temps indiqué au bas de de l'écran est normal (sous les 100ms)
- Causes : elle peut être causée par Nginx qui tente de résoudre l'adresse IPv4 comme une adresse IPv6.
- Solution : Utiliser un hostname explicite `127.0.0.1` au lieu de `localhost` par exemple.

-----

- Erreur : `Error 1062: Duplicate entry 'Unknown-Mac' pour la clé 'UQE_public_key_name'`
- Causes : Cette erreur est provoquée par du code ancien, la table `public_key` avait `UQE_public_key_name` comme règle unique pour le nom de la clef SSH dans les premières versions.
- Solution : Vous pouvez supprimer cette règle manuellement pour résoudre ce problème.

-----

- Erreur : `GLIBC_2.14 not found`
- Solution : Exécuter `sudo apt-get -t testing install libc6-dev`.

-----

- Erreur : `could not parse line: ; App name that shows on every page title`
- Causes : Le fichier est enregistré comme `UTF8 with BOM`(ce qui arrive dans Windows).
- Solution : Changez pour `UTF8`.
