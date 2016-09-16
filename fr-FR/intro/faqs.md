---
name: FAQs
sort: 3
---

# FAQs

### Déploiement

#### Que faire quand je suis à court d'un autre service sur le port 3000 ?

Pour changer le numéro de port d'écoute du Gogs lorsque vous devez l'exécuter une première fois :

    ./gogs web -port 3001

Ce drapeau modifie également le numéro du port dans la page d'installation pour vous, afin de choisir un numéro que vous souhaitez affecter à Gogs.

#### Comment utiliser Nginx avec Reverse Proxy ?

Ajouter dans `server` section `http` interne section `nginx.conf` dans et recharger la configuration :

```
server {
    listen 80;
    server_name git.crystalnetwork.us;

    location / {
        proxy_pass http://localhost:3000;
    }
}
```

##### Mise en place avec suburl

Dans le cas où vous avez besoin d'utiliser un sous-chemin, par exemple Gogs, vous pouvez changer votre configuration Nginx comme suit (attention particulière au suffixe `/`):

```
server {
    listen 80;
    server_name git.crystalnetwork.us;

    location /gogs/ {
        proxy_pass http://localhost:3000/;
    }
}
```

Ensuite, configurez votre configuration dans `[server] ROOT_URL = http://git.crystalnetwork.us/gogs/`.

##### Que diriez-vous avec Apache 2 suburl?

Essayez de suivre le template de configuration :

```
<VirtualHost *:443>
        ...
        <Proxy *>
                 Order allow,deny
                 Allow from all
        </Proxy>

        ProxyPass /git http://127.0.0.1:3000/
        ProxyPassReverse /git http://127.0.0.1:3000/
</VirtualHost>
```

#### Comment configurer HTTPS ?

Modifier les options de configuration suivantes dans le fichier `custom/conf/app.ini` (ceci est un exemple) :

```
[server]
PROTOCOL = https
ROOT_URL = https://try.gogs.io/
CERT_FILE = custom/https/unified.cert
KEY_FILE = custom/https/decryped-private.key
```

Si vous voulez utiliser le protocole HTTPS auto-signés, vous pouvez exécuter des commandes qui suivent pour générer des fichiers de certificat et de clé :

	$ ./gogs cert -ca=true -duration=8760h0m0s -host=myhost.example.com

#### Comment activer le mode déconnecté ?

Pour exécuter Gogs dans un intranet, l'option de configuration de modification `server -> OFFLINE_MODE` à être à `true` dans le fichier `custom/conf/app.ini`.

#### Comment faire pour activer un robots.txt personnalisé ?

Créer un fichier `robots.txt` dans le dossier `custom`.

#### Comment faire pour exécuter comme démon ?

Gogs a quelques scripts tiers pour supporter l'exécution en tant que démon :

- [init.d/centos](https://github.com/gogits/gogs/blob/master/scripts/init/centos/gogs)
- [init.d/debian](https://github.com/gogits/gogs/blob/master/scripts/init/debian/gogs)
- Systemd dans la section suivante.

#### Service Systemd

Dans le dépôt de Gogs sur GitHub est présent un [fichier de modèle de service systemd](https://github.com/gogits/gogs/blob/master/scripts/systemd/gogs.service). Il a besoin de quelques modifications pour une version de production pour votre installation. OK, lancer un éditeur.

1. Remplacer `start.sh` qui est le chemin de `ExecStart` par le chemin de votre installation Gogs.
2. Remplacer également `WorkingDirectory` par le chemin par le chemin de votre installation Gogs.
3. [Optionnel] Si vous souhaitez utiliser Gogs avec `MySQL/MariaDB`, `PostgreSQL`, `Redis` ou `memcached`, supprimez le "#" devant le `After`qui correspond à votre base de données.

Lorsque vous avez fini avec vos modifications du fichier systemd, enregistrer le dans `/etc/systemd` et démarrer le avec `sudo systemd restart gogs`.

Vous pouvez vérifier l'état du service du Gogs avec `sudo systemd status gogs -l` ou afficher directement les entrées avec journald `sudo journalctl -b -u gogs.service`.

### Administration

#### Comment devenir un administrateur ?

1. Vous êtes le premier utilisateur enregistré avec `ID = 1`, et aucune confirmation par e-mail requis (si activé).
2. L'administrateur se connecte par défaut `Admin -> Users` et autoriser quelqu'un.
3. Inscrivez-vous dans la page d'installation.

### Gestion des dépôts

#### Comment donner des "hameçons" d'autorisation Git aux utilisateurs ?

C'est **à haut niveau d'une autorisation qui peut endommager votre système** que vous devez activer/désactiver dans le panneau d'admin de gestion des utilisateurs (`/admin/users/:userid`) pour les utilisateurs en qui vous avez vraiment confiance.

### Autres

#### Comment obtenir la dernière version de Gogs ?

Le texte plat de la version Gogs est dans le fichier `templates/VERSION`.

#### Que fait la commande `gogs serv` ?

Vous avez aucune raison d'exécuter cette commande manuellement, il sera appelé par Git mise à jour d'"hameçon" chaque fois nouvelle poussée de SSH est à venir.
