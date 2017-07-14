---
name: Configuration détaillée des sources
sort: 4
---

# Configuration détaillée pour construire Gogs à partir des sources

Après l'instruction de la construction [des sources](/docs/installation/install_from_source), vous devriez maintenant avoir un utilisateur local `git` et une configuration de travail de `go` et [Gogs](http://gogs.io/).
Nous allons installer Gogs avec **Nginx**. De cette façon, nous pouvons profiter de Nginx. Ceci est utile pour les serveurs qui ont déjà un Nginx en cours d'exécution.

Pour le reste de ce document, nous posons les hypothèses suivantes :

- Vous voulez utiliser 'Gogs' sur le domaine `example.com`
- Nginx est votre serveur web
- `postgresql` est votre serveur de base de données
- et vous voulez que votre dépôt ressemblent à URL git `git.example.com`

Comme indiqué dans [Configuration and run](/docs/installation/configuration_and_run), vous devez créer votre propre fichier de configuration dans `$GOPATH/src/github.com/gogits/gogs/custom/conf/app.ini`

Ensuite suivez les commandes suivantes :

```bash
sudo mkdir -p /var/log/gogs
sudo chown git:git /var/log/gogs
sudo su - git
cd ~
mkdir -p $GOPATH/src/github.com/gogits/gogs/custom/conf
mkdir -p ~/gogs-repositories
```

Maintenant, copiez le fichier de configuration de base afin que nous puissions le modifier :

```bash
cd $GOPATH/src/github.com/gogits/gogs
cp conf/app.ini custom/conf/
```

En utilisant votre éditeur préféré, ouvrez le fichier de configuration :

`$GOPATH/src/github.com/gogits/gogs/custom/conf/app.ini`

par exemple :

```bash
vi $GOPATH/src/github.com/gogits/gogs/custom/conf/app.ini
```

## Configurer un serveur

À partir du haut, changer les clés suivantes dans différentes sections :

### Section par défaut

```bash
RUN_USER=git
```

### Section `[repository]`

```bash
ROOT=/home/git/gogs-repositories
```

### Section `[server]`

```ini
DOMAIN = example.com
ROOT_URL = %(PROTOCOL)s://git.%(DOMAIN)s/
HTTP_ADDR = localhost
HTTP_PORT = 3000
```

## Mise en place du serveur `postgresql`

Sous `debian`/`ubuntu` vous pouvez l'installer à l'aide de :

```bash
sudo apt-get install -y postgresql postgresql-client libpq-dev
```

Pour OSX utiliser `brew`:

```bash
brew install postgresql
```

Maintenant, la configuration de la base de données pour que l'utilisateur 'git' y accède :

Première connexion à psql :

```bash
# Login to PostgreSQL
sudo -u postgres psql -d template1
```

Ensuite, au sein de l'invite de psql, entrez :

```sql
CREATE USER git CREATEDB;

\password git

CREATE DATABASE gogs_production OWNER git;

\q

sudo -u git -H psql -d gogs_production

gogs_production> \q
```

Maintenant, nous pouvons mettre à jour `app.ini`, ouvrez à nouveau `$GOPATH/src/github.com/gogits/gogs/custom/conf/app.ini` dans votre éditeur et changez ce qui suit (assurez-vous que vous êtes l'utilisateur `git`, sinon faites `sudo su - git`):

### Section `[database]`

```ini
DB_TYPE = postgres
HOST = 127.0.0.1:5432
NAME = gogs_production
USER = git
PASSWD =__postgresql_password_used_in_previous_step__
PATH = data/gogs.db
```

## Mise en place du serveur Nginx

Sous `debian`/`ubuntu` vous pouvez l'installer à l'aide de:

```bash
sudo apt-get install -y nginx
```

Maintenant, nous allons créer un fichier de configuration Nginx pour Gogs :

```bash
sudo su - git
vi /tmp/gogs
```
Et y ajouter ce qui suit :

```python
server {
    listen 80;
    server_name git.example.com;

    location / {
        proxy_pass http://localhost:3000;
    }
}
```

Maintenant, ajoutez ce fichier à Nginx et redémarrez-le :

```bash
sudo mv /tmp/gogs /etc/nginx/sites-available/
sudo ln -s /etc/nginx/sites-available/gogs /etc/nginx/sites-enabled/gogs
sudo service nginx restart
```

```bash
sudo su - git
cd $GOPATH/src/github.com/gogits/gogs
./gogs web
```

Grâce à votre navigateur, vous devriez être en mesure de visiter `git.example.com`. Vous devez avoir un enregistrement DNS déclaré ou à défaut avoir mis à jour votre fichier /etc/hosts.

Bien sûr, si vous ne l'avez pas déjà fait dans la configuration initiale, un écran comme celui-ci va s'afficher:

![installation page screenshot](/docs/images/installation_page_screenshot.png)

Changez le **Database Type** à *PostgreSQL* si ce n'est pas déjà indiqué. Après avoir vérifié que les autres paramètres correspondent à ce que vous avez saisi dans le fichier `app.ini`, cliquez installer et profitez de votre nouvelles instance Gogs !

L'étape suivante pour intégré Gogs dans `debian`/`ubuntu` est de le lancer comme un service au démarrage du serveur.

Si vous voulez démarrer automatiquement Gogs a l'aide de `systemd`, voir [la section de la FAQ](/docs/intro/faqs.md#systemd-service).
