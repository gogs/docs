---
name: Sous Windows
sort: 6
---

## Binaires installation Gogs sur Windows 7

> Contribution par [@victorsegall](https://github.com/victorsegall)

### Conditions préalables

Vérifiez la principale [page d'installation](http://gogs.io/docs/installation/) pour confirmer avant de vous y rendre. Vous avez besoin [git pour Windows](http://git-scm.com/download/win).

Un serveur SSH n'est pas nécessaire sur votre machine Windows si cette instance Gogs est pour vous seulement, ou si vous avez seulement besoin du service HTTP(S), qui fournit des Gogs.

Pour exécuter Gogs comme un service, vous aurez besoin de l'un d'eux :

* Iain Patterson's [nssm.exe](http://nssm.cc/)
* Nick Rozanski's [SRVSTART.EXE](http://rozanski.org.uk/software)
* Microsoft's [Srvany.exe](https://support.microsoft.com/kb/137890)

Ce guide couvre nssm.exe, qui est [open source](https://git.nssm.cc/?p=nssm.git) et [public domain](https://git.nssm.cc/?p=nssm.git;a=blob_plain;f=README.txt;hb=HEAD).

Pendant l'installation, vous allez exécuter Gogs comme utilisateur local actuel, puis reconfigurer afin de fonctionner comme un service.

Lors de la configuration via l'interface utilisateur Gogs App.ini et web, utilisezséparateurs de répertoires  UNIX (slash `/`) lorsque c'est possible. Si vous êtes besoin d'utiliser un chemin UNC vers un partage réseau, essayez [the Cygwin way](https://cygwin.com/cygwin-ug-net/using.html#unc-paths), ou [map the path as a local drive](http://www.sevenforums.com/tutorials/49517-map-network-drive.html).

### Exécuter en tant que utilisateur local actuel

Gogs est capable de fonctionner comme utilisateur local immédiatement, sans aucune configuration. Il suffit de décompresser le [binaire Windows](http://gogs.io/docs/installation/install_from_binary.html) fichier zip quelque part, aller à la ligne de commande, et de faire :

```
C:>cd C:\path\to\gogs

C:\path\to\gogs>gogs web
```

Nous supposerons que vous avez choisi `C:\gogs`

À ce stade, Gogs devrait être disponible sur `http://127.0.0.1:3000`, et l'installateur de première exécution vous guidera à travers la création d'une configuration de base et fonctionnel.

### Première exécution

Par défaut, Gogs sera utilisé à la fois `C:\Users\your_username` et `C:\gogs` pour les opérations de fichiers.

Dans `C:\gogs`, Gogs devront avoir accès en écriture à :

```
C:\gogs\custom\conf
C:\gogs\data
C:\gogs\log
```

Cela sont réalisés au cours de sa première exécution, dont il assume ensuite eu accès en écriture `C:\gogs`. Créez-les avant la première exécution si cela est pas fait.

Voir [Configuration et exécution](http://gogs.io/docs/installation/configuration_and_run.html) en apprendre davantage dans `C:\gogs\custom\conf\app.ini`. Il sera écrit lors de la première exécution.

Gogs va créer `C:\Users\your_username\.gitconfig` par le texte suivant :

```
[user]
	name = Gogs
	email = gogitservice@gmail.com
```

Ça [peut être modifié à tous moment](http://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup), et il devrait l'être. Il est l'utilisateur à laquelle l'ensemble de vos opérations git y être attribuée. Il peut également être remplacée par un dépôt, à travers `C:\path\to\repo\.git\config`.

### Base de donnée

Si vous utilisez un serveur de base de données distante, le guide pour [Ubuntu](http://gogs.io/docs/installation/install_gogs_on_ubuntu.html) et [Mac OS](http://gogs.io/docs/installation/install_gogs_on_mac.html) couvrent le nécessaires pour créer vos tables pour SQL.

Pour une instance locale un seul utilisateur Gogs, vous pouvez simplement permettre Gogs pour créer une base de données SQLite, en configurant rien d'autre avant de faire première manche. Il en résulte que `C:\Gogs\custom\conf\app.ini` ressemblera à ceci :

```
[database]
DB_TYPE = sqlite3
HOST = 127.0.0.1:3306
NAME = gogs
USER = root
PASSWD =
SSL_MODE = disable
PATH = data/gogs.db
```

Il s'agit de toutes les données qui seront stockées sur Gogs, mais aucune donnée git. Les données git (fichiers de dépôt, l'histoire, et autres) vit à l'extérieur de Gogs, sur le système de fichiers, tandis que Gogs fournit une couche de middleware pour la création d'une file d'attente de question, la visualisation de l'historique, de la configuration du dépôt, etc.

Par conséquent, l'authentification de l'utilisateur et l'autorisation que vous configurez dans Gogs auront aucun effet sur les opérations de git fait à travers le système de fichiers.

### Utilisation en local

Par défaut, Gogs gére les dépôts dans `C:\Users\your_username\gogs-repositories`

Il est défini dans `C:\Gogs\custom\conf\app.ini` avec :

```
[repository]
ROOT = C:/path/to/repositories
```

Ils seront dans un dépôt vide, sans répertoire de travail. Vous pouvez les cloner localement par le système de fichiers, avec git.exe (qui a été nécessaire dans l'[installation](http://gogs.io/docs/installation/), ou avec [TortoiseGit](https://code.google.com/p/tortoisegit/) si vous préférez travailler via l'Explorateur Windows.

Sur la ligne de commande, vous pourriez faire :

```
C:>cd C:\Users\your_username\Documents\repos

C:\Users\your_username\Documents\repos>md repo_name

C:\Users\your_username\Documents\repos>cd repo_name

C:\Users\your_username\Documents\repos\repo_name>git.exe clone --progress -v "C:\Users\your_username\gogs-repositories\your_gogs_username\repo_name.git" "C:\Users\your_username\Documents\repos\repo_name"

Cloning into 'C:\Users\your_username\Documents\repos\repo_name'...

done.
```

Lorsque vous travaillez localement, il est pas nécessaire de passer des opérations de git à travers le service Gogs. Gogs mettra à jour lorsque vous ferai `git push` sur votre répertoire de travail de clone `C:\Users\your_username\Documents\repos\repo_name` à son origine vers `C:\Users\your_username\gogs-repositories`. Ne cloner le dépôt quand vous avez besoin d'un répertoire de travail, même quand vous voler en solo. Il vous permet de déplacer très facilement Gogs et vos dépôts d'origine plus tard, sans que les processus de toucher vos répertoires de travail.

### Exécutez Gogs comme un service

À ce stade, vous pouvez choisir de verrouiller les autorisations de fichiers et de répertoires. Il suffit de garder à l'esprit les chemins à laquelle Gogs nécessite un accès en écriture, qui comprend le dépôt Gogs `ROOT`.

Les modifications suivantes sont à apportées dans `C:\Gogs\custom\conf\app.ini`:

```
RUN_USER = COMPUTERNAME$
```

Définit Gogs afin de fonctionner tant que l'utilisateur du système local.

`COMPUTERNAME` est ce que la réponse est de `echo %COMPUTERNAME%` sur la ligne de commande. Si la réponse est `USER-PC` alors `RUN_USER = USER-PC$`

```
[server]
DOMAIN = gogs
PROTOCOL = http
HTTP_ADDR = 127.0.1.1
HTTP_PORT = 80
OFFLINE_MODE = true
ROOT_URL = http://gogs/
```

Moves Gogs' sur le port d'écoute 80 sur le sous-réseau de l'interface locale, et appel Gogs HTTPd que son hôte virtuel est le domaine "Gogs". Cela vous permet de renoncer, y compris un numéro de port lors de la navigation, et empêche la collision avec d'autres services localhost. L'adresse IP peut être quelque chose dans la plage 127.0.0.2 - 127.254.254.254, tant qu'elle est unique à Gogs.

De compléter cette route de réseau, ouvert Notepad.exe en tant qu'administrateur et inclure les éléments suivants dans `C:\Windows\System32\drivers\etc\hosts`:

```
# Go Git Service local HTTPd
127.0.1.1        gogs
```

L'entrée du fichier hosts garantir que toutes les demandes vers le domaine "Gogs" sont capturées par votre interface localhost dans un navigateur web, en général, `gogs/` dans la barre d'adresse est suffisante pour déclencher cette route.

Accéder à [nssm.exe](http://nssm.cc/download), nécessaires pour votre machine (32 ou 64 bits; ils sont emballés ensemble dans le fichier zip principal), et le placer dans un répertoire qui est (ou sera ajoutée à) votre variable d'environnement %PATH%.

Ouvrez une ligne de commande en tant qu'administrateur et à faire `nssm install gogs` pour configurer Gogs comme un service.

```
C:\>nssm install gogs
```

"NSSM service installer" apparaîtra. Configurez de la manière suivante :

Onglet application :

* Chemin : C:\gogs\gogs.exe
* Répertoire de démarrage : C:\gogs
* Arguments : web

![](/docs/images/install_gogs_on_windows_nssm_1.png)

Onglet détails:

* Nom complet : Go Gits Service
* Description : Gogs (Go Git Service) est un service Git sans douleur auto-hébergé écrit en Go.
* Type de démmarage : Automatique (Démarrage différé)

Notez que nous avons choisi le [démarrage différé](http://stackoverflow.com/a/11015576), de sorte que le service n'aura pas d'impact sur le temps du démarrage. Gogs commencera deux minutes après les services non différée.

![](/docs/images/install_gogs_on_windows_nssm_2.png)

Onglet entrer/sorti (I/O):

* Sortie (stdout): C:\gogs\log\gogs-nssm.txt
* Erreur (stderr): C:\gogs\log\gogs-nssm.txt

Qui permettra de capturer tout le texte que vous auriez normalement du recevoir de Gogs sur la console de ligne de commande, et connectez-vous à ce fichier à la place.

![](/docs/images/install_gogs_on_windows_nssm_3.png)

Onglet de rotation des dossiers

* Vérifier : Rotation des dossiers
* Limiter la rotation de fichiers de plus de : 1000000 octets

![](/docs/images/install_gogs_on_windows_nssm_4.png)

Onglet environnement :

* Variables d'environnement : PATH=%PATH%;C:\gogs;C:\Program Files (x86)\Git\bin

Cela est une garantie qu'aussi bien gogs.exe et git.exe seront sur la variable de chemin de service Gogs lors de l'exécution.

![](/docs/images/install_gogs_on_windows_nssm_5.png)

Cliquez sur "Installer le service", et vous devriez être confirmé qu'il a réussi. Si elle a échoué, reportez-vous à la console de ligne de commande que vous avez commencé, pour le message d'erreur. Lorsqu'il a réussit, allez à la ligne de commande et faite :

```
nssm start gogs
```

Vous devriez voir :

```
gogs: START: The operation completed successfully.
```

Vérifiez que cela est vrai en ouvrant `C:\gogs\log\gogs-nssm.txt`. Vous devriez voir les procédures de démarrage jusqu'à ce que Gogs se terminant par :

```
timestamp [I] SQLite3 Enabled
timestamp [I] Run Mode: Production
timestamp [I] Listen: http://127.0.1.1:80
```

Maintenant, pointez votre navigateur web à l'adresse `http://gogs/` et connectez-vous.

Gogs fonctionne comme un service, et ne devrai pas être exécuté manuellement, à moins que quelque chose va mal. NSSM va tenter de redémarrer le service pour vous, si le serveur Gogs se bloque.

Lorsque vous avez besoin de le relancer après des changements dans `app.ini`, aller en ligne de commande en tant qu'administrateur après les changements, et de faire:

```
nssm restart gogs
```

Voir la [fiche de configuration de triche](http://gogs.io/docs/advanced/configuration_cheat_sheet.html) pour la référence de la configuration `custom\conf\app.ini`.

Un exemple de journalisation et la gestion des erreurs en action :

```
[log]
ROOT_PATH = C:\gogs\log
```

Au moment de la rédaction de cette ligne, pour Go Git Service 0.5.13.0212 Beta, il écrira la suivante dans `C:\gogs\log\gogs-nssm.txt`:

```
timestamp [T] Custom path: C:/gogs/custom
timestamp [T] Log path: C:\gogs\log
timestamp [I] Gogs: Go Git Service 0.5.13.0212 Beta
timestamp [log.go:294 Error()] [E] Fail to set logger(file): invalid character 'g' in string escape code
```

Ceci est ce qui a été prévu dans `C:\custom\conf\app.ini`:

```
ROOT_PATH = C:/gogs/log
```

Et ce fut l'interaction avec `nssm` qui le résous :

```
C:\>nssm restart gogs
gogs: STOP: The operation completed successfully.
gogs: Unexpected status SERVICE_PAUSED in response to START control.

C:\>nssm start gogs
gogs: START: An instance of the service is already running.

C:\>nssm stop gogs
gogs: STOP: The operation completed successfully.

C:\>nssm start gogs
gogs: Unexpected status SERVICE_PAUSED in response to START control.

C:\>nssm restart gogs
gogs: STOP: The operation completed successfully.
gogs: START: The operation completed successfully.
```
