---
name: FAQs
sort: 3
---

# FAQs

### Déploiement

#### Que faire quand un autre service est déjà en écoute sur le port 3000 ?

Pour changer le port d'écoute de Gogs lorsque vous devez l'exécuter une première fois :

    ./gogs web -port 3001

Cet argument modifie également le numéro du port dans la page d'installation pour vous.

#### Comment utiliser Nginx avec Reverse Proxy ?

Ajouter la section `server` suivante dans la section `http` du fichier `nginx.conf` et recharger la configuration :

```
server {
    listen 80;
    server_name git.crystalnetwork.us;

    location / {
        proxy_pass http://localhost:3000;
    }
}
```

##### Mise en place avec une sous url avec Nginx

Dans le cas où vous avez besoin d'utiliser un sous-chemin pour votre instance Gogs, vous pouvez changer votre configuration Nginx comme suit (attention au `/` de fin):

```
server {
    listen 80;
    server_name git.crystalnetwork.us;

    location /gogs/ {
        proxy_pass http://localhost:3000/;
    }
}
```

Ensuite, configurez `[server] ROOT_URL = http://git.crystalnetwork.us/gogs/`.

##### Pourquoi y-t-il des erreurs lorsque j'upload de gros fichiers ?

Pour voir comment faire pour que Nginx gère l'upload de gros fichiers, voyez [ici](http://stackoverflow.com/a/15021750). L'erreur `413` est une erreur Nginx courante, ajoutez la ligne suivante au bloc server pour la régler :

```
client_max_body_size 50m;
```

##### Comment configurer Apache 2 en tant que reverse proxy ?

Ne pas oublier d'activer les modules : proxy et proxy_http.

`custom/conf/app.ini`:
```
[server]
ROOT_URL = http://git.domain.tld/
...
```
`/etc/apache2/vhost.d/<yourconfig>.conf`:
```
<VirtualHost *:80>
    ...
    ProxyPreserveHost On
    ProxyRequests off
    ProxyPass / http://127.0.0.1:3000
    ProxyPassReverse / http://127.0.0.1:3000
</VirtualHost>
```

##### Comment configurer une sous-URL avec Apache 2 ?

Essayez de suivre le modèle de configuration :

`custom/conf/app.ini`:
```
[server]
ROOT_URL = http://domain.tld/git
```
`etc/apache2/vhost.d/<yourconfig>.conf`:
```
<VirtualHost *:80>
        ...
        <Proxy *>
                 Order allow,deny
                 Allow from all
        </Proxy>

        ProxyPass /git http://127.0.0.1:3000
        ProxyPassReverse /git http://127.0.0.1:3000
</VirtualHost>
```

Il est important de ne pas ajouter de / de fin après le port.

##### Comment configurer lighttpd en tant que reverse proxy ?

```
server.modules  += ( "mod_proxy" )
$HTTP["host"] == "git.example.com" {
    proxy.server = ( "" => ( ( "host" => "127.0.0.1", "port" => "3000" ) ) )
}
```

##### Comment configurer une sous-URL avec lighttpd?

```
# requires lighttpd 1.4.46 or later
server.modules  += ( "mod_proxy" )
$HTTP["url"] =~ "^/gogs/" {
    proxy.server = ( "" => ( ( "host" => "localhost", "port" => "3000" ) ) )
    proxy.header = ( "map-urlpath" => ( "/gogs/" => "/" ) )
}
```

#### Comment utiliser Caddy en tant que reverse-proxy ?

Ajouter le bloc de code suivant à votre configuration Caddy et recharger la configuration :

```
git.example.com {
    proxy / http://localhost:3000
}
```

##### Comment configurer une sous-URL avec Caddy ?

Utilisez le bloc de code suivant (à noter le `/` de fin):

```
git.example.com {
    proxy /gogs/ http://localhost:3000
}
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

Si vous voulez utiliser le protocole HTTPS auto-signé, vous pouvez exécuter les commandes qui suivent pour générer le certificat et la clé :

	$ ./gogs cert -ca=true -duration=8760h0m0s -host=myhost.example.com

Si vous comptez utilisez HTTPS avec un reverse proxy, configurer le reverse proxy pour être en HTTPS et Gogs pour être en HTTP

#### Comment activer le mode déconnecté ?

Pour exécuter Gogs dans un intranet, l'option de configuration `server -> OFFLINE_MODE` est à valoriser à `true` dans le fichier `custom/conf/app.ini`.

#### Comment faire pour activer un robots.txt personnalisé ?

Créer un fichier `robots.txt` dans le dossier `custom`.

#### Comment faire pour exécuter Gogs en tant que démon ?

Gogs fourni quelques scripts tiers pour supporter l'exécution en tant que démon :

- [init.d/centos](https://github.com/gogs/gogs/blob/master/scripts/init/centos/gogs)
- [init.d/debian](https://github.com/gogs/gogs/blob/master/scripts/init/debian/gogs)
- Systemd dans la section suivante.

#### Lancer Gogs au démarrage avec systemd 

Dans le dépôt de Gogs sur GitHub est présent un [modèle de service systemd](https://github.com/gogs/gogs/blob/master/scripts/systemd/gogs.service). Il a besoin d'être adapté à votre installation.

1. Mettre à jour `User`, `Group`, `WorkingDirectory`, `ExecStart`, et `Environment` pour correspondre à votre installation.
2. (Optionnel) Si vous utilisez Gogs avec `MySQL/MariaDB`, `PostgreSQL`, `Redis`, or `memcached`, décommentez les lignes `After` concernées.

Lorsque vous avez fini vos modifications du service systemd, enregistrez le dans `/etc/systemd/system/gogs.service`, rechargez la configuration systemd avec `systemctl daemon-reload` et démarrez le avec `sudo systemctl restart gogs`.

Vous pouvez vérifier l'état du service du Gogs avec `sudo systemctl status gogs -l` ou afficher directement les entrées avec journald `sudo journalctl -b -u gogs.service`.

### Administration

#### Comment devenir administrateur ?

1. Vous êtes le premier utilisateur enregistré avec `ID = 1`, dans ce cas aucune confirmation par e-mail n'est requise (si activé).
2. L'administrateur se connecte par défaut `Admin -> Users` et modifie un des autres utilisateurs.
3. Inscrivez-vous depuis la page d'installation.

### Gestion des dépôts

#### Comment donner des permissions sur des webhooks aux utilisateurs ?

C'est **une autorisation de haut-niveau qui peut endommager votre système** que vous devez activer/désactiver dans le panneau de gestion des utilisateurs (`/admin/users/:userid`) pour les utilisateurs en qui vous avez vraiment confiance.

### Autres

#### Comment obtenir la dernière version de Gogs ?

La version est inscrite dans le fichier texte `templates/VERSION`.

#### Que fait la commande `gogs serv` ?

Vous n'avez aucune raison d'exécuter cette commande manuellement, elle sera appelée par Git lors de chaque appel à un webhook.
