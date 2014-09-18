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