---
name: Configuration et fonctionnement
sort: 7
---

# Configuration et fonctionnement

## Configuration

### Configuration par défault

La configuration par défaut est enregistrée dans `conf/app.ini`, vous **n'avez pas** besoin de modifier la totalité. depuis `v0.6.0`, ce fichier est incorporé au binaire.

### Configuration personnalisée

Comment personnaliser la configuration si vous n'êtes pas autorisé à modifier `conf/app.ini` ? Et bien, créez `custom/conf/app.ini` ! Remplacez ensuite les clefs correspondantes dans `custom/conf/app.ini`.

Par exemple, pour modifier le chemin du dépôt, ajouter quelque chose comme :

```
[repository]
ROOT = /home/jiahuachen/gogs-repositories
```

Vous pouvez également changer le mot de passe de la base de données comme ceci :

```
[database]
PASSWORD = root
```

### Mettre en place une configuration de proxy inverse

#### Nginx

```nginx
server {
	listen 80;
	server_name your-domain.com;
	return 301 https://$host$request_uri;
}

server {
		listen 443 ssl;
		server_name your-domain.com;

		ssl_certificate full_chain.pem;
		ssl_certificate_key private.key;

		location / {
			client_max_body_size 1024M;
			proxy_pass http://127.0.0.1:3000;
			proxy_set_header Host $host;
			proxy_set_header X-Real-IP $remote_addr;
			proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
			proxy_set_header X-Forwarded-Proto $scheme;
			add_header X-Cache $upstream_cache_status;
			proxy_set_header Upgrade $http_upgrade;
		}
}
```

#### Apache

```apache
<VirtualHost *:80>
    ServerName your-domain.com
    Redirect permanent / https://your-domain.com/
</VirtualHost>

<VirtualHost *:443>
    ServerName your-domain.com

    SSLEngine on
    SSLCertificateFile /path/to/full_chain.pem
    SSLCertificateKeyFile /path/to/private.key

    ProxyPreserveHost On
    ProxyPass / http://127.0.0.1:3000/
    ProxyPassReverse / http://127.0.0.1:3000/

    RequestHeader set X-Real-IP %{REMOTE_ADDR}s
    RequestHeader set X-Forwarded-For %{REMOTE_ADDR}s
    RequestHeader set X-Forwarded-Proto "https"

    LimitRequestBody 1073741824  # 1024M

    RewriteEngine On
    RewriteCond %{HTTP:Upgrade} websocket [NC]
    RewriteCond %{HTTP:Connection} upgrade [NC]
    RewriteRule ^/?(.*) "ws://127.0.0.1:3000/$1" [P,L]
</VirtualHost>
```

### Pourquoi faisons-nous ça ?

Oui, pourquoi ne pas simplement éditer `conf/app.ini` ? C'est pour vous permettre de garder votre configuration personnalisée en sécurité :

- Pour les personnes qui installent le binaire, chaque fois que vous arrêtez le programme, vous pouvez tout simplement copier et coller le fichier de configuration sans rien à re-configurer.
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
- Ouvrez l'URL `/install` pour créer votre configuration la première fois.
