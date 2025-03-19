---
name: Config and run
---

# Configuration and run

## Configuration

### Default configuration

The default configuration is saved in `conf/app.ini`, you do **NOT** need to edit it at all. Since `v0.6.0`, this file is embedded into the binary.

### Custom configuration

So how do you create a custom configuration if you are not allowed to edit `conf/app.ini`? Well, create `custom/conf/app.ini` then! Corresponding keys in corresponding sections in `custom/conf/app.ini` will overwrite the values set in `conf/app.ini`.

For example, to change the root path of where raw repository data is being stored, add something like follows:

```
[repository]
ROOT = /home/jiahuachen/gogs-repositories
```

Of course, you want to change the database setting as well:

```
[database]
PASSWORD = `root`
```

Note: please quote passwords using `` ` ``

### Set up a reverse proxy configuration

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

### Why are we doing this?

Yes, why don't you just edit `conf/app.ini`? The reason is to keep your custom configuration safe:

- For people who install from binary, every time after you ship the program, you can just simply copy and paste without re-configuring anything.
- For people who install from source, we've ruled out the `custom/conf/app.ini` in `.gitignore`, so it will not cause changes in version control as a result of re-applying old configurations to the new version.

## Run Gogs server

### For Developers

- You need to set key `security -> INSTALL_LOCK` to be `true` in the file `custom/conf/app.ini` in order to run from source.
- You can use the famous `make` command:

```sh
$ make
$ ./gogs web
```

### For Deployment

**Scripts are in the `scripts` directory, but execute them at the root of the repository**

- There are many ways to start:
	- Plain: just use `./gogs web`
	- Daemons: see [scripts](https://github.com/gogs/gogs/tree/main/scripts) folder
- Go to `/install` to do your first-time run configuration.

### Running as daemon via init (eg. openrc)

- Create a file named `/etc/init.d/gogs` as follows, assuming gogs is installed in the `/home/git` user:

```
#!/sbin/openrc-run

SVCNAME=gogs
GOGS_PIDFILE=/var/run/gogs.pid
GOGS_USER=git
GOGS_HOME=/home/$GOGS_USER
GOGS_PATH=$GOGS_HOME/go/src/github.com/gogs/gogs
COMMAND="${GOGS_PATH}/gogs"
ARGS="web"

depend() {
    need net
    use dns logger mysql
}

checkconfig() {
    if [ ! -d "$GOGS_PATH" ] ; then
        eerror "gogs not installed" || return 1
    fi
    return 0
}

start() {
    checkconfig || return 1

    ebegin "Starting ${SVCNAME}"
    start-stop-daemon --start --quiet --background \
        --make-pidfile --pidfile "${GOGS_PIDFILE}" \
        --user "${GOGS_USER}" \
        -d ${GOGS_PATH} \
        --exec "${COMMAND}" "${ARGS}"
    eend $?
}

stop() {
    ebegin "Stopping ${SVCNAME}"
    start-stop-daemon --stop --quiet --pidfile $GOGS_PIDFILE
    eend $?
}
```
