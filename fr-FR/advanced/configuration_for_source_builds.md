---
name: Configuration détaillée des sources
sort: 4
---

# Configuration détaillée pour créer à partir des sources

Après l'instruction de la construction [des sources](/docs/installation/install_from_source.md), vous devriez maintenant avoir un utilisateur local `git` et une configuration de travail de `go` et [Gogs](http://gogs.io/).
Nous allons installer avec Gogs avec **Nginx**. De cette façon, nous pouvons profiter de Nginx. Ceci est utile pour les serveurs qui ont déjà un Nginx en cours d'exécution.

Pour le reste de ce document, nous supposerons que ce qui suit :

- Vous voulez utiliser 'Gogs' sur le domaine `example.com`
- Nginx est votre serveur web
- `postgresql` est votre serveur de base de données
- et vous voulez que votre dépôt ressemblent à URL git `git.example.com`

Comme indiqué dans [Configuration and run](/docs/installation/configuration_and_run.md), vous devez créer votre propre fichier de configuration dans `$GOPATH/src/github.com/gogits/gogs/custom/conf/app.ini`

De la première installation des dossiers comme :

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

pour l'exemple :

```bash
vi $GOPATH/src/github.com/gogits/gogs/custom/conf/app.ini
```

## Configurer un serveur

À partir du haut, changer les clés suivantes dans différentes sections :

### Section par défault

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

Maintenant, la configuration de la base de données pour que l'utilisateur 'git' y accéde :

Première connexion à psql :

```bash
# Login to PostgreSQL
sudo -u postgres psql -d template1
```

Ensuite, au sein de l'invite de psql, entrez :

```sql
# Create a user for git
# The following are typed in postgresql prompt
CREATE USER git CREATEDB;

# Set up a password for git
# Remember this password for the next step
\password git

# Create the Gogs database & grant all privileges on database
CREATE DATABASE gogs_production OWNER git;

# Quit the database session
\q

# Try connecting to the new database with the new user
sudo -u git -H psql -d gogs_production

# Quit the database session
gogs_production> \q
```

Maintenant, nous pouvons mettre à jour `app.ini`, nouveau ouvert `$GOPATH/src/github.com/gogits/gogs/custom/conf/app.ini` dans votre éditeur et de changer ce qui suit (assurez-vous que vous êtes l'utilisateur `git`, sinon enter `sudo su - git`):

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

Maintenant, nous allons créer un fichier de configuration Nginx pour notre Gogs :

```bash
sudo su - git
# Use your editor to create a temp file:
vi /tmp/gogs
```
Et ajouter ce qui suit à elle :

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
et puis :

```bash
sudo su - git
cd $GOPATH/src/github.com/gogits/gogs
./gogs web
```

Grâce à votre navigateur, vous devriez être en mesure de visiter `git.example.com`.

Bien sûr, si vous ne l'avez pas déjà fait dans la configuration initiale, vous serez présenté avec un écran comme celui-ci :

![installation page screenshot](/docs/images/installation_page_screenshot.png)

Changer le **Database Type** à *PostgreSQL* si elle est pas déjà sélectionné. Après avoir vérifié que les autres paramètres correspondent à ce que vous avez saisi dans votre cas dans le fichier `app.ini`, cliquez installer et profiter de votre nouvelle application git !

Vous avez en principe fait ici, l'étape suivante pour intégré Gogs dans `debian`/`ubuntu` est redémarré.

## Ajout de Gogs à `init.d`

Cette section décrit comment démarrer *Gogs* correctement lorsque votre système Linux redémarre. Pour les autres plateformes, consultez la documentation pour voir comment vous pouvez faire cela. Pour Mac OSX voir [ce document](/docs/installation/install_gogs_on_mac.md#run-gogs-server) pour contrôler les application aux démarrages.

Si vous avez suivi les étapes précédentes, vous pouvez maintenant activer le démarrage automatique de Gogs. Sous `debian`/`ubuntu`, nous allons utiliser le script à partir de `$GOPATH/src/github.com/gogits/gogs/scripts/init/debian/gogs`.

Copions ce script et le modifier :

```bash
# change to 'git' user
sudo su - git
cd ~
cp $GOPATH/src/github.com/gogits/gogs/scripts/init/debian/gogs ./gogs.init
```

En utilisant votre éditeur préféré, ouvrir `~/gogs.init` et de le modifier comme :

- Changer ces deux lignes en haut du fichier :

```ini
# Required-Start:    $syslog $network
# Required-Stop:     $syslog
```

par ça :

```ini
# Required-Start:    $syslog $network $local_fs nginx postgresql
# Required-Stop:     $syslog $local_fs
```

Plus bas dans le même fichier, définir l'emplacement de sorte `init.d` peut trouver notre installation `gogs` en modifiant `WORKING_DIR` ligne à :

```ini
WORKINGDIR=/home/git/go/src/github.com/gogits/gogs
```

Déplacez le fichier vers `/etc/init.d` et mettre à jour :

```bash
# firt change user to normal account if you haven't already
exit
# move the files and update the system
sudo mv /home/git/gogs.init /etc/init.d/gogs
sudo chmod ug+x /etc/init.d/gogs
sudo update-rc.d gogs defaults 30 70
```

Testez votre configuration en exécutant

```sudo service gogs start```

et la visite de l'URL de votre site (ex. `git.example.com`)

Si vous voulez démarrer automatiquement Gogs a l'aide de `systemd`, voir [la section de la FAQ](/docs/intro/faqs.md#systemd-service).
