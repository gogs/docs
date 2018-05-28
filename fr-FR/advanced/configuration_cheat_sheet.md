---
name: Détails de configuration
sort: 1
---

# Aide mémoire pour la configuration

Ceci est un aide-mémoire relatif au fichier de configuration de Gogs, il vous aider à mieux comprendre le fonctionnement de Gogs.

Avant de commencer, sachez que tout changement de configuration doit être fait dans `custom/conf/app.ini` ou n'importe quel fichier similaire.

Tous les **paramètres par défaut** peuvent être trouvés dans [app.ini](https://github.com/gogs/gogs/blob/master/conf/app.ini). Si vous voyez quelque chose comme `%(X)s`, c'est une fonctionnalité qui est au format [ini](https://github.com/go-ini/ini/tree/v1#recursive-values) pour la lecture recursive de la valeur.

## Global (`DEFAULT`)

Nom |Description
----|-----------
`APP_NAME`|Nom de l'application, à modifier comme vous le souhaitez.
`RUN_USER`|Le nom de l'utilisateur système qui fait tourner Gogs. La recommandation est d'utiliser 'git'; cepandant vous pouvez le changer pour n'importe quel utilisateur faisant tourner Gogs sur votre ordinateur. Si cette valeur n'est pas bien renseignée, cela peut provoquer des crashs de Gogs.
`RUN_MODE`|Pour des questions de performances et autres, changez ceci en `prod` quand Gogs est déployé dans un environnement de production. Le processus d'installation le passe à `prod` automatiquement.


## Serveur (`server`)

Nom|Description
----|-----------
`PROTOCOL`|`http` ou `https`.
`DOMAIN`|Le nom de domaine de votre serveur.
`ROOT_URL`|URL publiques complète du serveur Gogs.
`HTTP_ADDR`|Adresse d'écoute HTTP.
`HTTP_PORT`|Port d'écoute HTTP.
`DISABLE_SSH`|Désactiver la fonction SSH quand elle n'est pas disponible.
`SSH_PORT`|Le numéro de port à exposer dans l'URL de clonage SSH des dépôts. Le port public du serveur SSH externe, habituellement `22`.
`OFFLINE_MODE`|Activez cette option pour ne pas utiliser des CDN pour les fichiers statiques, Gravatar sera également désactivé automatiquement.
`DISABLE_ROUTER_LOG`|Activez cette option pour ne pas écrire les logs routeur.
`CERT_FILE`|Chemin du fichier Cert utilisé pour le protocole HTTPS.
`KEY_FILE`|Chemin du fichier clé utilisée pour le protocole HTTPS.
`STATIC_ROOT_PATH`|Racine pour les modèles et les fichiers statiques, par défaut c'est le répertoire racine Gogs.
`ENABLE_GZIP`|Activez cette option pour activer la compression GZIP dans l'application.
`LANDING_PAGE`|Page de destination des utilisateurs non-connectés, `home` ou `explore`.

## Dépôts (`repository`)

Nom |Description
----|-----------
`ROOT`|Chemin pour stocker les dépôts de tous les utilisateurs, c'est un chemin absolu, par défaut : `~/<user name>/gogs-repositories`.
`SCRIPT_TYPE`|Le shell supporté par le serveur, généralement `bash`, mais certains clients déclarent qu'ils ont seulement `sh`.

## Base de donnée (`database`)

Nom |Description
----|-----------
`DB_TYPE`|Le type de base de données que vous avez choisi, soit `mysql`, `postgres` ou `sqlite3`.
`HOST`|Adresse de la base de données et port.
`NAME`|Nom de la base.
`USER`|Utilisateur de la base.
`PASSWD`|Mot de passe de l'utilisateur.
`SSL_MODE`|Pour PostgreSQL seulement.
`PATH`|Pour SQLite3 seulement, le chemin du fichier de base de données.

## Securité (`security`)

Nom |Description
----|-----------
`INSTALL_LOCK`|Indique si il faut charger la page d'installation (implique la création du compte administrateur, donc valeur critique).
`SECRET_KEY`|Clé secrète globale pour la sécurité de votre serveur, ** à changer ** (une chaîne aléatoire est générée à chaque fois que vous installez).
`LOGIN_REMEMBER_DAYS`|Durée de vie des cookies.
`COOKIE_USERNAME`|Le nom du cookie pour enregistrer le nom d'utilisateur.
`COOKIE_REMEMBER_NAME`|Le nom du cookie pour sauvegarder les informations de connexion automatique.
`REVERSE_PROXY_AUTHENTICATION_USER`|En-tête utilisé pour l'authentification par nom d'utilisateur en cas de reverse-proxy.

## Service ( `service` )

Nom |Description
----|-----------
`ACTIVE_CODE_LIVE_MINUTES`|Nombre de minutes pendant lequel le code d'activation est actif.
`RESET_PASSWD_CODE_LIVE_MINUTES`|Nombre de minutes pendant lequel la remise à zéro du password est active.
`REGISTER_EMAIL_CONFIRM`|Activez cette option pour forcer un email de confirmation d'inscription, il faut activer `Mailer`.
`DISABLE_REGISTRATION`|Désactiver les inscriptions, seul l'administrateur peut créer des comptes pour les utilisateurs.
`SHOW_REGISTRATION_BUTTON`|Indiquez si vous souhaitez afficher le bouton d'inscription ou non.
`REQUIRE_SIGNIN_VIEW`|Activez cette option pour forcer les utilisateurs à se connecter pour visualiser une page spécifique.
`ENABLE_CACHE_AVATAR`|Activez cette option pour mettre en cache l'avatar à partir Gravatar.
`ENABLE_NOTIFY_MAIL`|Activez cette option pour envoyer des e-mail aux observateurs de dépôt lors d'évènements comme ticket/problème, exige d'activer `Mailer`.
`ENABLE_REVERSE_PROXY_AUTHENTICATION`|Activez cette option pour permettre l'authentification avec reverse proxy, plus de détail sur [Github](https://github.com/gogs/gogs/issues/165)
`ENABLE_REVERSE_PROXY_AUTO_REGISTRATION`|Activez cette option pour permettre l'auto-inscription dans le cas de l'authentification avec reverse-proxy.
`DISABLE_MINIMUM_KEY_SIZE_CHECK`|Ne pas vérifier la taille de clé minimale pour le type correspondant.
`ENABLE_GIT_HOOKS`|Activez cette option pour permettre l'exécution des git hooks, commandes qui sont situé dans `ROOT/[user name]/[repo name].git/hooks`

## Webhook ( `webhook` )

Nom |Description
----|-----------
`TYPES`|Types autorisés , options possibles `gogs`, `slack` ou `discord`.
`DELIVER_TIMEOUT`|Délai entre la mise à jour du dépôt et le lancement des webhooks.
`SKIP_TLS_VERIFY`|Indique si un certificat non-sécurisé est autorisé ou pas.
`PAGING_NUM`|Nombre de webhook affiché sur une page d'historique.

## Serveur de messagerie ( `mailer` )

Nom |Description
----|-----------
`ENABLED`|Active le service de messagerie.
`DISABLE_HELO`|Désactive la fonctionnalité HELO.
`HELO_HOSTNAME`|Le nom d'hôte personnalisé utilisé par HELO.
`HOST`|Adresse email du serveur SMTP.
`FROM`|Adresse email, la RFC 5322. Cela peut être juste une adresse e-mail, ou une chaîne du type `"Nom" <email@example.com>`.
`USER`|Nom d'utilisateur pour le serveur de messagerie (habituellement juste votre adresse e-mail).
`PASSWD`|Mot de passe pour le serveur de messagerie.
`SKIP_VERIFY`|Ne pas vérifier les certificats auto-signés.

## OAuth

Nom |Description
----|-----------
`ENABLED`|Switch général pour OAuth, la valeur par défaut est "false"

## Cache ( `cache` )

Nom |Description
----|-----------
`ADAPTER`|Adaptateur de moteur de cache, soit `memory`, `redis`, ou `memcache`. Si vous souhaitez utiliser `redis` ou `memcache`, assurez-vous de tout reconstruire avec des tags de construction `redis` ou `memcache`: `go build -tags='redis'`. Voir [ici](https://gogs.io/docs/installation/install_from_source#construisez-avec-sqlite3%2Fredis%2Fmemcache)
`INTERVAL`|pour le cache de mémoire seulement, l'intervalle en secondes du passage du ramasse-miettes (gc).
`HOST`|Pour redis et memcache, l'adresse de l'hôte et le numéro de port.

## Session ( `session` )

Nom |Description
----|-----------
`PROVIDER`|Fournisseur de moteur de session, soit `memory`, `file`, `redis`, ou `mysql`.
`PROVIDER_CONFIG`|Pour les fichiers, c'est le chemin ; pour les autres, c'est l'adresse du serveur et le numéro de port.
`COOKIE_SECURE`|Activez cette option pour forcer l'utilisation de HTTPS pour tous les accès de la session.
`GC_INTERVAL_TIME`|Intervalle du passage du ramasse-miettes (gc) en secondes.

## Picture ( `picture` )

Nom |Description
----|-----------
`GRAVATAR_SOURCE`|peut être modifié à `duoshuo` car Gravatar est bloqué en Chine.
`DISABLE_GRAVATAR`|Activer cette option pour utiliser les avatars locaux uniquement.

## Log ( `log` )

Nom |Description
----|-----------
`ROOT_PATH`|Chemin du dossier pour les fichiers logs.
`MODE`|Le mode de journalisation, par défaut `console`. Pour utiliser plusieurs modes, ajoutez des virgules pour les séparer.
`LEVEL`|Niveau de journalisation, par défaut est à `Trace`.

### log.console ( `log.console` )

Nom |Description
----|-----------
`LEVEL`|Niveau de log pour la sortie console. Lorsqu'aucune valeur n'est définie, elle a le même niveau que le log général.

### log.file ( `log.file` )

Nom |Description
----|-----------
`LEVEL`|Niveau de log pour la sortie fichier. Lorsqu'aucune valeur n'est définie, elle a le même niveau que le log général.

### log.conn ( `log.conn` )

Nom |Description
----|-----------
`LEVEL`|Niveau de log pour la sortie de connexion. Lorsqu'aucune valeur n'est définie, elle a le même niveau que le log général.

### log.smtp ( `log.smtp` )

Nom |Description
----|-----------
`LEVEL`|Niveau de log pour la sortie smtp. Lorsqu'aucune valeur n'est définie, elle a le même niveau que le log général.

## Git ( `git` )

Nom |Description
----|-----------
`MAX_GITDIFF_LINES`|Nombre de lignes maximal affiché par diff.
