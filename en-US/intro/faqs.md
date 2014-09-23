---
name: FAQs
sort: 3
---

# FAQs

### Deployment

#### How use Nginx with Reverse Proxy?

Add following `server` section inside `http` section in `nginx.conf` and reload configuration:

```
server {
    listen 80;
    server_name git.crystalnetwork.us;

    location / {
        proxy_pass http://localhost:3000;
    }
}
```

#### How to setup HTTPS?

Change following configuration options in `custom/conf/app.ini` file(this is a sample):

```
[server]
PROTOCOL = https
ROOT_URL = https://try.gogs.io/
CERT_FILE = custom/https/unified.cert
KEY_FILE = custom/https/decryped-private.key
```

If you want to use self-signed HTTPS, you can execute following commands to generate cert and key files:

	$ ./gogs cert -ca=true -duration=8760h0m0s -host=myhost.example.com

#### How to enable offline mode?

To run Gogs in an intranet, change configuration option `server -> OFFLINE_MODE` to be `true` in file `custom/conf/app.ini`.

#### How to enable custom robots.txt?

Create a file called `robots.txt` under `custom` directory.

### Administration

#### How to become an administrator?

1. You're the first registered user with `ID = 1`, and no e-mail confirmation required(if enabled).
2. Default administrator log into `Admin -> Users` and authorize someone. 
3. Register in the install page.

### Systemd Service

In the GitHub repository of Gogs is a [systemd service template file](https://github.com/gogits/gogs/blob/master/scripts/systemd/gogs.service) for Gogs. It needs some modifications for a working version for your installation. OK, start the editors.

1. Replace the `start.sh` path of `ExecStart` with the path of your Gogs installation. 
2. Also replace the path of `WorkingDirectory` with the path of your Gogs installation.
3. [optional] If you are would like to use Gogs with `MySQL/MariaDB`, `PostgreSQL`, `Redis` or `memcached`, uncomment the corresponding line of `After`.

When you are complete with your modification of the systemd file, save it in the `/etc/systemd` and start it with `sudo systemd restart gogs`.

You can check the status of the Gogs systemd service with `sudo systemd status gogs -l` or display directly the journald entries with `sudo journalctl -b -u gogs.service`.

### Others

#### How to get current Gogs version?

The plain text format of Gogs version is in the file `templates/VERSION`.
