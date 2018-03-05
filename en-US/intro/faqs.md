---
name: FAQs
---

# FAQs

### Deployment

#### What do I do if I'm running another service on port 3000?

Change the listening port of Gogs the first time you run it with:

    ./gogs web -port 3001

This flag also changes the port number in the install page for you, so pick a number you want to assign for Gogs.

#### How do I use NGINX with Reverse Proxy?

Add the following `server` section inside the `http` section of `nginx.conf` and reload the configuration:

```
server {
    listen 80;
    server_name git.crystalnetwork.us;

    location / {
        proxy_pass http://localhost:3000;
    }
}
```

##### How do I set up a sub-path with NGINX?

In case you need to use a sub-path for your Gogs instance, you can change your NGINX configuration to the following
(note _both_ of the `/` suffixes after **location** and **proxy_pass**):

```
server {
    listen 80;
    server_name git.crystalnetwork.us;

    location /gogs/ {
        proxy_pass http://localhost:3000/;
    }
}
```

Then set `[server] ROOT_URL = http://git.crystalnetwork.us/gogs/` in your configuration.

##### Why am I getting errors when uploading large files?

To allow NGINX to handle large file uploads in repositories, please see a relevant discussion [here](http://stackoverflow.com/a/15021750). `413` is a common NGINX error; append the following line to your server block to fix this:

```
client_max_body_size 50m;
```

#### How do I use Apache 2 with Reverse Proxy?

Don't forget to enable apache mods: proxy, proxy_http

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
    ProxyPass / http://127.0.0.1:3000/
    ProxyPassReverse / http://127.0.0.1:3000/
</VirtualHost>
```

##### How do I set up a sub-URL with Apache 2?

Use the following configuration templates:

`custom/conf/app.ini`:
```
[server]
ROOT_URL = http://domain.tld/git
...
```
`/etc/apache2/vhost.d/<yourconfig>.conf`:
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

It's important to omit a trailing slash after the port number.

##### How do I set up a sub-URL with lighttpd?

Use the following configuration template:

```
server.modules  += ( "mod_proxy_backend_http" )
$HTTP["url"] =~ "^/gogs" {
    proxy-core.protocol = "http"
    proxy-core.backends = ( "localhost:3000" )
    proxy-core.rewrite-request = (
      "_uri" => ( "^/gogs/?(.*)" => "/$1" ),
      "Host" => ( ".*" => "localhost:3000" ),
    )
}
```
#### How do I use Caddy with Reverse Proxy?

Add the following server block to your Caddyfile and reload the configuration:

```
git.example.com {
    proxy / http://localhost:3000
}
```

##### How do I set up a sub-path with Caddy?

In case you need to use a sub-path for your Gogs instance, you can change your Caddy configuration to the following
(note the `/` suffix):

```
git.example.com {
    proxy /gogs/ http://localhost:3000
}
```

#### How do I set up HTTPS?

Change the following configuration options in `custom/conf/app.ini` in the section that looks like this sample:

```
[server]
PROTOCOL = https
ROOT_URL = https://try.gogs.io/
CERT_FILE = custom/https/unified.cert
KEY_FILE = custom/https/decryped-private.key
```

If you want to use self-signed HTTPS, you can execute the following command to generate a certificate and key files (make sure you use `cert` build tag or download the official binary):

	$ ./gogs cert -ca=true -duration=8760h0m0s -host=myhost.example.com

If you want to use SSL with an Apache 2 proxy configuration, configure gogs to use http and Apache 2 for SSL.

#### How do I run Gogs in offline mode/on an intranet?

To run Gogs on an intranet, change the configuration option `server -> OFFLINE_MODE` to `true` in the file `custom/conf/app.ini`.

#### How do I make a custom robots.txt?

Create a file called `robots.txt` in the `custom` directory.

#### How do I run Gogs as a daemon?

Gogs has some third-party scripts that support running it as a daemon:

- [init.d/centos](https://github.com/gogits/gogs/blob/master/scripts/init/centos/gogs)
- [init.d/debian](https://github.com/gogits/gogs/blob/master/scripts/init/debian/gogs)
- Systemd in the following section.

#### How do I run Gogs at startup with Systemd?

There's a [systemd service template file](https://github.com/gogits/gogs/blob/master/scripts/systemd/gogs.service) in the Gogs GitHub repository and in the installed files at `./scripts/systemd/gogs.service`. You will likely need to modify it for your installation:

1. Update `User`, `Group`, `WorkingDirectory`, `ExecStart`, and
   `Environment` with values appropriate to your Gogs installation.
2. (Optional) If you would like to use Gogs with `MySQL/MariaDB`, `PostgreSQL`, `Redis`, or `memcached` then uncomment the appropriate `After` lines.

Save your modified service file at `/etc/systemd/system/gogs.service`, enable it with `sudo systemctl enable gogs`, and start it with `sudo systemctl start gogs`.

You can check the status of the Gogs service with `sudo systemctl status gogs -l`, or display the journal entries with `sudo journalctl -b -u gogs`.

### Administration

#### How can I become an administrator?

The first registered user with `ID = 1` is an administrator. No e-mail confirmation is required for this (if enabled). The default administrator can log into `Admin` > `Users` and authorize another user. A user will also be an administrator if they register in the install page.

#### Is there a simple way to reset forgotten administrator password?

It's assumed that you're real server admin and you have shell access (local or remote) to your server with appropriate priviledges.
In such a case, you can do the following steps:

- In shell
  - log in to the shell of your server
  - stop gogs
  - create new temporary user with administrator rights from command line (see below)
  - start gogs
- In web browser
  - log in as new user (using web browser)
  - set new password to your old administrator account by clicking `Edit` in the `Admin Panel` > `Users`
  - log out
  - log in as old administration (with new password)
  - delete temporary user in the `Admin Panel` > `Users`

Just for example, let's assume that `gogs` is run as user `git` and is installed to `/home/git/gogs` directory.

To create new temporary user from command line you should execute something like that:

```
$ su git
$ cd /home/git/gogs
$ ./gogs admin create-user --name tmpuser --password tmppassword --admin --email email@example.com
```

Those commands create new admin user `tmpuser` with `tmppassword` password. 

*Remark: I don't really know, is it necessary to keep gogs stopped while creating new user or not. 
I suppose that it's safer to stop gogs before doing that.*

### Repository Management

#### How do I give Git Hooks permission to users?

This is a **high-level permission which can damage your system** which you must enable/disable in the admin user management panel (`/admin/users/:userid`). Only grant this permission to users who you really trust.

### Other

#### How do I find the current version of Gogs?

The current version of Gogs is written in plain text in the file `templates/.VERSION`.

#### Why Gogs isn't collaborating on its own?

When was your last pull request to Gogs?
