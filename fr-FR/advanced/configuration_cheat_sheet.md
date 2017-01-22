---
name: Fiche de configuration de triche
sort: 1
---

# Fiche de configuration de triche

Ceci est une feuille de triche pour le fichier de configuration Gogs, il aidera si vous voulez comprendre comment Gogs fonctionne.

Avant de commencer, assurez-vous que tout changement de configuration doit être faite dans `custom/conf/app.ini` ou n'importe quel endroit correspondant.

Tous les paramètres par défaut peuvent être trouvés dans [app.ini](https://github.com/gogits/gogs/blob/master/conf/app.ini). Si vous voyez quelque chose comme `%(X)s`, il est propulsé par la fonctionnalité [ini](https://github.com/go-ini/ini/tree/v1#recursive-values) pour la lecture de la valeur de manière récursive.

## Globalement

- `APP_NAME`: Nom de l'application, modifié comme vous le souhaitez.
- `RUN_USER`: L'utilisateur du système nécessite de fonctionner, nous vous recommandons d'être sous l'utilisateur `git`; cependant, changer pour quel que soit votre nom d'utilisateur est si vous exécutez Gogs dans votre ordinateur personnel. Le serveur peut crasher si cette valeur n'est pas réglée correctement.
- `RUN_MODE`: Pour des performances et autres finalités, changer pour `prod` quand déployer dans l'environnement de production. Le processus d'installation va définir ce `prod` automatiquement.

## Dépôts

- `ROOT`: Chemin d'accès racine pour stocker des données dépôts de tous les utilisateurs, il doit être un chemin absolu, par défaut : `~/<user name>/gogs-repositories`.
- `SCRIPT_TYPE`: Le script entré charger par votre serveur, est généralement `bash`, mais certains clients déclarent qu'ils ont seulement `sh`.

## Serveur

- `PROTOCOL`: Pour `http` ou `https`.
- `DOMAIN`: Le nom de domaine de votre serveur.
- `ROOT_URL`: URL complète du serveur Gogs dans le domaine public.
- `HTTP_ADDR`: Adresse d'écoute HTTP.
- `HTTP_PORT`: Port d'écoute HTTP.
- `DISABLE_SSH`: Désactiver la fonction SSH quand elle n'est pas disponible.
- `SSH_PORT`: Le port SSH, si dans votre cas ce n'est pas `22`.
- `OFFLINE_MODE`: Activez cette option pour ne pas utiliser des CDN pour les fichiers statiques, Gravatar sera également désactivé automatiquement.
- `DISABLE_ROUTER_LOG`: Activez cette option pour ne pas écrire les logs routeur.
- `CERT_FILE`: Chemin du fichier Cert utilisé pour le protocole HTTPS.
- `KEY_FILE`: Chemin du fichier clé utilisée pour le protocole HTTPS.
- `STATIC_ROOT_PATH`: Niveau supérieur de modèle et fichiers statiques chemin par défaut est le chemin où se trouve Gogs.
- `ENABLE_GZIP`: Activez cette option pour avoir un niveau de demande de soutien GZIP.
- `LANDING_PAGE`: Non-connecté la page de destination des utilisateurs, soit `home` ou `explore`.

## Base de donnée

- `DB_TYPE`: Le type de base de données que vous avez choisi, soit `mysql`, `postgres` ou `sqlite3`.
- `HOST`: Adresse de l'hôte de base de données et du port.
- `NAME`: Nom de la base.
- `USER`: Utilisateur de la base.
- `PASSWD`:  Mot de passe de l'utilisateur.
- `SSL_MODE`: Pour PostgreSQL seulement.
- `PATH`: Pour SQLite3 seulement, le chemin du fichier de base de données.

## Securité

- `INSTALL_LOCK`: Pour indiquer si il faut ouvrir la page d'installation (création du compte admin impliqué c'est donc une valeur très importante).
- `SECRET_KEY`: Clé secrète globale pour la sécurité de votre serveur, ** vous feriez mieux de changer ** (va générer une chaîne aléatoire à chaque fois que vous installez).
- `LOGIN_REMEMBER_DAYS`: Les jours de temps de vie des cookies.
- `COOKIE_USERNAME`: Le nom de cookie pour enregistrer le nom d'utilisateur.
- `COOKIE_REMEMBER_NAME`: Le nom de cookie pour sauvegarder les informations de connexion automatique.
- `REVERSE_PROXY_AUTHENTICATION_USER`: Nom d'en-tête pour proxy inverse authentification nom d'utilisateur.

## Service

- `ACTIVE_CODE_LIVE_MINUTES`: Les minutes de durée de vie actif du code.
- `RESET_PASSWD_CODE_LIVE_MINUTES`: Réinitialisation du mot de passe en minutes du temps de la vie du code.
- `REGISTER_EMAIL_CONFIRM`: Activez cette option pour demander un email de confirmation d'inscription, il faut activer `Mailer`.
- `DISABLE_REGISTRATION`: Désactiver les inscriptions, seul l'administrateur peut créer des comptes pour les utilisateurs.
- `SHOW_REGISTRATION_BUTTON`: Indiquez si vous souhaitez afficher le bouton d'inscription ou non.
- `REQUIRE_SIGNIN_VIEW`: Activez cette option pour forcer les utilisateurs à ce connecter pour visualiser une page spécifique.
- `ENABLE_CACHE_AVATAR`: Activez cette option pour mettre en cache avatar à partir Gravatar.
- `ENABLE_NOTIFY_MAIL`: Activez cette option pour envoyer des e-mail aux observateurs de dépôt quand quelque chose se passe comme créer des tickets/problème, exige d'activer `Mailer`.
- `ENABLE_REVERSE_PROXY_AUTHENTICATION`: Activez cette option pour permettre l'authentification de proxy inverse, plus en détail : https://github.com/gogits/gogs/issues/165
- `ENABLE_REVERSE_PROXY_AUTO_REGISTRATION`: Activez cette option pour permettre l'auto-inscriptions pour l'authentification inverse.
- `DISABLE_MINIMUM_KEY_SIZE_CHECK`: Ne pas vérifier la taille de clé minimale avec le type correspondant.
- `ENABLE_GIT_HOOKS`: Activez cette option pour permettre l'exécution des git hook commandes qui sont situé sous `ROOT/[user name]/[repo name].git/hooks`

## Webhook

- `TASK_INTERVAL`: Temps intercalé en minute entre les webhooks.
- `DELIVER_TIMEOUT`: Délai de livraison en secondes de prise de vue webhooks.
- `SKIP_TLS_VERIFY`: Indiquez si la certification est non-sécuriser ou non.

## Serveur de messagerie

- `ENABLED`: Activez cette option pour utiliser tous le service de messagerie.
- `DISABLE_HELO`: Désactiver le fonctionnalité HELO.
- `HELO_HOSTNAME`: Le nom d'hôte personnalisée pour le fonctionnement de HELO.
- `HOST`: Adresse email SMTP hôte.
- `FROM`: Adresse email, la RFC 5322. Cela peut être juste une adresse e-mail, ou le "Nom" sous le format <email@example.com>.
- `USER`: Nom d'utilisateur du logiciel de messagerie du système (habituellement juste votre adresse e-mail).
- `PASSWD`: Mot de passe entre vous et le programme de messagerie.
- `SKIP_VERIFY`: Ne pas vérifier les certificats auto-signés.

## OAuth

- `ENABLED`: Switch général pour OAuth, la valeur par défaut est "false"

## Cache

- `ADAPTER`: Adaptateur de moteur de cache, soit `memory`, `redis`, ou `memcache`. Si vous souhaitez utiliser `redis` ou `memcache`, assurez-vous de tout reconstruire avec des tags de construction `redis` ou `memcache`: `go build -tags='redis'`.
- `INTERVAL`: pour le cache de mémoire seulement, GC intervalle en secondes.
- `HOST`: Pour redis et memcache, l'adresse de l'hôte et le numéro de port.

## Session

- `PROVIDER`: Fournisseur de moteur de session, soit `memory`, `file`, `redis`, ou `mysql`.
- `PROVIDER_CONFIG`: Pour les dossiers, c'est le chemin racine; pour les autres, c'est l'adresse de l'hôte et numéro de port.
- `COOKIE_SECURE`: Activez cette option pour forcer l'utilisation de HTTPS pour tous les accès de la session.
- `GC_INTERVAL_TIME`: Intervalle de GC en secondes.

## Picture

- `GRAVATAR_SOURCE`: peut être modifié à `duoshuo` tant que Gravatar est bloqué en Chine.
- `DISABLE_GRAVATAR`: Activer cette option pour utiliser les avatars local uniquement.

## Log

- `ROOT_PATH`: Chemin d'accès racine pour les fichiers logs.
- `MODE`: Le mode de journalisation, par défaut est à `console`. Pour de multiples modes, utilisation de la virgule pour les séparer.
- `LEVEL`: Niveau de journal général, par défaut est à `Trace`.

### log.console

- `LEVEL`: Niveau de log pour la sortie de la console. Lorsque aucune valeur est définie, elle est le niveau de journal général.

### log.file

- `LEVEL`: Niveau de log pour la sortie de fichier. Lorsque aucune valeur est définie, elle est le niveau de journal général.

### log.conn

- `LEVEL`: Niveau de log pour la sortie de connexion. Lorsque aucune valeur est définie, elle est le niveau de journal général.

### log.smtp

- `LEVEL`: Niveau de log pour la sortie de smtp. Lorsque aucune valeur est définie, elle est le niveau de journal général.

## Git

- `MAX_GITDIFF_LINES`: Limite de lignes de maximum dans la page de diff.
