---
name: Detailed Config From Source
sort: 4
---

# Detailed Configuration For Source Builds

Following the instruction of building [from source](/docs/installation/install_from_source.md), you should now have a local user `git` and a working setup of `go` and [Gogs](http://gogs.io/).
We are gong to setup Gogs along with **Nginx**. This way, we can take advantage of Nginx. This is useful for servers that already have an Nginx running.

For the rest fo this document, we'll assume the following:

- You want to serve 'Gogs' on `example.com` domain
- Nginx is your webserver
- `postgresql` is your database server
- and you want your git repository URLs look like `git.example.com`

As mentioned in [Configuration and run](/docs/installation/configuration_and_run.md), you should create your own configuration file in `$GOPATH/src/github.com/gogits/gogs/custom/conf/app.ini`

Let's first setup some directories:

```bash
sudo mkdir -p /var/log/gogs
sudo chown git:git /var/log/gogs
sudo su - git
cd ~
mkdir -p $GOPATH/src/github.com/gogits/gogs/custom/conf
mkdir -p ~/gogs-repositories
```

Now copy the base configuration file so we can edit it:

```bash
cd $GOPATH/src/github.com/gogits/gogs
cp conf/app.ini custom/conf/
```

Using your editor, open the configuration file:

`$GOPATH/src/github.com/gogits/gogs/custom/conf/app.ini`

for example:

```bash
vi $GOPATH/src/github.com/gogits/gogs/custom/conf/app.ini
```

## Setting up server

Starting from top, change the following keys in different sections:

### Default section

```bash
RUN_USER=git
```

### `[repository]` section

```bash
ROOT=/home/git/gogs-repositories
```

### `[server]` section

```ini
DOMAIN = example.com
ROOT_URL = %(PROTOCOL)s://git.%(DOMAIN)s/
HTTP_ADDR = localhost
HTTP_PORT = 3000
```

## Setting up `postgresql` sever

Under `debian`/`ubuntu` you can install it using:

```bash
sudo apt-get install -y postgresql postgresql-client libpq-dev
```

For OSX use `brew`:

```bash
brew install postgresql
```

Now let's setup database so our 'git' user can access it:

First login to psql:

```bash
# Login to PostgreSQL
sudo -u postgres psql -d template1
```

Then within psql prompt, enter:

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

Now we can update `app.ini`, again open `$GOPATH/src/github.com/gogits/gogs/custom/conf/app.ini` in your editor and change the following (make sure you are the user `git`, if not enter `sudo su - git`):

### `[database]` section

```ini
DB_TYPE = postgres
HOST = 127.0.0.1:5432
NAME = gogs_production
USER = git
PASSWD =__postgresql_password_used_in_previous_step__
PATH = data/gogs.db
```

## Setting up Nginx sever

Under `debian`/`ubuntu` you can install it using:

```bash
sudo apt-get install -y nginx
```

Now let's create an Nginx config file for our Gogs:

```bash
sudo su - git
# Use your editor to create a temp file:
vi /tmp/gogs
```
And add the following to it:

```python
server {
    listen 80;
    server_name git.example.com;

    location / {
        proxy_pass http://localhost:3000;
    }
}
```

Now add this file to Nginx and restart it:

```bash
sudo mv /tmp/gogs /etc/nginx/sites-available/
sudo ln -s /etc/nginx/sites-available/gogs /etc/nginx/sites-enabled/gogs
sudo service nginx restart
```
and then:

```bash
sudo su - git
cd $GOPATH/src/github.com/gogits/gogs
./gogs web
```

Using your browser, you should be able to visit `git.example.com`.

Of course if you have not already done the initial setup, you will be presented with a screen like this:

![installation page screenshot](/docs/images/installation_page_screenshot.png)

Change the **Database Type** to *PostgreSQL* if it's not already selected. After verifying that other settings match to what you have entered in your custom `app.ini` file, click install and enjoy your new git web app!

You are basically done here, the next step outlines how to make Gogs start when `debian`/`ubuntu` is restarted.

## Adding Gogs to `init.d`

This section describes how to properly start *Gogs* when your linux system reboots. For other platforms, consult the documentation to see how you can do this. For Mac OSX see [this document](/docs/installation/install_gogs_on_mac.md#run-gogs-server) to control app start-ups.

If you followed previous steps, you can now enable automatic start of gogs. Under `debian`/`ubuntu`, we will use the script from `$GOPATH/src/github.com/gogits/gogs/scripts/init/debian/gogs`.

Let's copy the script and modify it:

```bash
# change to 'git' user
sudo su - git
cd ~
cp $GOPATH/src/github.com/gogits/gogs/scripts/init/debian/gogs ./gogs.init
```

Using your editor open `~/gogs.init` and modify it such as:

- Change these two lines at the top of file:

```ini
# Required-Start:    $syslog $network
# Required-Stop:     $syslog
```

to

```ini
# Required-Start:    $syslog $network $local_fs nginx postgresql
# Required-Stop:     $syslog $local_fs
```

Further down in the same file, set the location so `init.d` can find our `gogs` installation by changing `WORKING_DIR` line to:

```ini
WORKINGDIR=/home/git/go/src/github.com/gogits/gogs
```

Move the file to `/etc/init.d` and update it:

```bash
# firt change user to normal account if you haven't already
exit
# move the files and update the system
sudo mv /home/git/gogs.init /etc/init.d/gogs
sudo chmod ug+x /etc/init.d/gogs
sudo update-rc.d gogs defaults 30 70
```

Test your setup by running

```sudo service gogs start```

and visiting the URL for your site (ex. `git.example.com`)

If you want to autostart gogs using `systemd`, check out [the related FAQ](/docs/intro/faqs.md#systemd-service).
