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
CERT_FILE = custom/https/cert.pem
KEY_FILE = custom/https/key.pem
```

If you want to use self-signed HTTPS and installed Go, you can execute following commands to generate cert and key files:

	go run $GOROOT/src/pkg/crypto/tls/generate_cert.go -ca=true -duration=8760h0m0s -host=myhost.example.com

#### How get current Gogs version?

The plain text format of Gogs version is in the file `templates/VERSION`.

### Administration

#### How to become an administrator?

1. You're the first registered user with `ID = 1`, and no e-mail confirmation required(if enabled).
2. Default administrator log into `Admin -> Users` and authorize someone. 
3. Register in the install page.

### Systemd service

In the github repository of gogs is a [systemd service template file](https://github.com/gogits/gogs/blob/master/scripts/systemd/gogs.service) for gogs. It need some modification for a working version for your installation. Ok, start the editors.

1. Replace the `start.sh` path of `ExecStart` with the path of your gogs installation. 
2. Also replace the path of `WorkingDirectory` with the path of your gogs installation.
3. [optional] If you are would like to use gogs with `MySQL/MariaDB`, `PostgreSQL`, `Redis` or `memcached`, uncomment the corresponding line of `After`.

When you are complete with your modification of the systemd file, save it in the `/etc/systemd` and start it with `sudo systemd restart gogs`.

You can check the status of the gogs systemd service with `sudo systemd status gogs -l` or display directly the journald entries with `sudo journalctl -b -u gogs.service`.
