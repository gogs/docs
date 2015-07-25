---
name: Dépannage
sort: 2
---

# Dépannage

## Installation

- Erreur : `../gosrc/src/github.com/gogits/gogs/cmd/cert.go:79: undefined: elliptic.P224`
- Causes : Le paquet golang dans RHEL/CentOS ne supporte pas la cryptographie à courbe elliptique (car il est breveté) et il est spécifiquement retiré CentOS/RHEL.
- Solution : Télécharger et installer Go à partir de [golang.org/dl](http://golang.org/dl).

## Git

- Erreur : `bash /path/to/gogs: no such file or directory`
- Causes : Vous avez modifié l'emplacement du serveur Gogs après un certain temps et de l'ancien chemin a été codé en dur dans le fichier `~/.ssh/authorized_keys`.
- Solution : Executer `./gogs fix location <old Gogs path>` sous un nouveau répertoire Gogs.

-----

- Erreur :
	- `fatal: 'XX/XX.git' does not appear to be a git repository`
	- Commits pushed mais présente toujours comme un dépôt vide
- Causes : Il y a des clés SSH dupliqué dans le fichier `~/.ssh/authorized_keys`, peut-être vous utilisez / avez utilisé GitLab pour le même utilisateur du système.
- Solution : Supprimer l'ancienne et de garder celui qui a été ajoutée par Gogs seulement.

-----

- Erreur : `repo.NewRepoContext(fail to set git user.emil):`
- Causes : cela arrive quand les utilisateurs de Windows installent Git Bash sans activer l'option `cmd`.
- Solution : Réinstaller et activé l'option `cmd`.

## Validation de formulaire

- Erreur : `Repository/User name contains illegal characters`
- Causes : Afin d'éviter les exceptions inattendues, votre utilisateur / nom du dépôt sera considérée comme illégale si elles correspondent à l'une des règles suivantes :
	- Nom est égal à aucun mot de `"raw", "install", "api", "avatar", "user", "org", "help", "stars", "issues", "pulls", "commits", "repo", "template", "admin", "new"`.
	- Nom a suffixe `".git"`.

## Cache

- Erreur : `cache: unknown adaptername "memcache" (importation oublié?)`
- Causes : Pour empêcher l'importation inutiles du paquet, nous utilisons la construction balises pour spécifier si nécessaire.
- Solution :
	- Téléchargement : `go get -tags memcache github.com/gogits.gogs`
	- Construction : `go build -tags memcache`
	- Mêmes étapes pour `redis` quand vous voulez qu'il soit l'adaptateur de cache.

## MySQL

- Erreur : `Error 1071: Specified key was too long; max key length is 1000 bytes`
- Causes : Elle est causée par MyISAM.
- Solution : Une fois que vous importez le fichier `config/mysql.sql` puis connectez-vous à MySQL et lancer :

	```sql
	use gogs;
	set global storage_engine=INNODB;
	```

Après cela, allez à [http://localhost:3000/install](http://localhost:3000/install) et tout devrait fonctionner correctement (merci à [@linc01n](https://github.com/linc01n)).

-----

- Erreur : `Database setting is not correct: This server only supports the insecure old password authentication. If you still want to use it, please add 'allowOldPasswords=1' to your DSN. See also https://github.com/go-sql-driver/mysql/wiki/old_passwords`
- Causes : Seulement mettre à jour le mot de passe @localhost -- il y avait une seconde entrée de la table d'utilisateur où @% encore eu l'ancien mot de passe.
- Solution : [Un commentaire GitHub](https://github.com/gogits/gogs/issues/385#issuecomment-54357073)

## Logiciel de messagerie

- Erreur : Gmail avec erreur 534: `Please log in via your web browser and then try again`
- Causes : Cela est parce que Google ne fait pas confiance à votre serveur.
- Solution :
	- Visitez https://accounts.google.com et connectez-vous.
	- Allez sur https://accounts.google.com/DisplayUnlockCaptcha cliquez sur `continue`.
	- Maintenant copier le lien qui ressemble à ceci (l'invite du journal du serveur Gogs) : https://accounts.google.com/ContinueSignIn?sarp=1&scc=1&plt=AKgnsbvPPN_E_25__nyS*******f18O9uuLNtz0Imw et connectez-vous à nouveau.
	- Les choses devraient maintenant fonctionner. La dernière mais non le moindre, vérifiez votre boîte `spam` dans le cas où votre fournisseur de service de messagerie pense que votre gmail est un spammeur.

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

- Causes : Vous installez le système dans un autre shell, et a le style de chemin différent.
- Solution : S'il vous plaît essayer de démarrer par défaut Gogs CMD.

## Autre

- Erreur : Réponse de page extrêmement lente, mais montrent de temps sur le fond semble normal (sous 100ms)
- Causes : elle peut être causée par Nginx qui tente de résoudre l'adresse IPv4 par IPv6.
- Solution : Utiliser un hostname explicite `127.0.0.1` au lieu de `localhost`.

-----

- Erreur : `Error 1062: Duplicate entry 'Unknown-Mac' pour la clé 'UQE_public_key_name'`
- Causes : Il est dirigé par le code existant, `public_key` table utilisée pour avoir `UQE_public_key_name` règle unique pour nom de clé SSH dans la dernière version.
- Solution : Vous pouvez supprimer cette unique règle manuellement pour résoudre ce problème.

-----

- Erreur : `GLIBC_2.14 not found`
- Solution : Exécuter `sudo apt-get -t testing install libc6-dev`.

-----

- Erreur : `could not parse line: ; App name that shows on every page title`
- Causes : Il ce peut que vous enregistrez le fichier comme `UTF8 with BOM`(qui passe normalement dans Windows).
- Solution : Changer pour `UTF8`.
