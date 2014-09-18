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
