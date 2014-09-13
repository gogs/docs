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