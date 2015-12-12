---
name: From source
---

# Upgrade from source

The general way to upgrade Gogs:

```bash
# Upgrade source and install dependencies
$ go get -u github.com/gogits/gogs

$ cd $GOPATH/src/github.com/gogits/gogs

# Remove old build
$ rm gogs

# or move old build
$ mv gogs gogs.$(date +%Y-%m-%d).old

# And rebuild Gogs
$ go build
```

Other operations:

- [Build from `develop` branch](/docs/installation/install_from_source#build-from-develop-branch)
- [Test Installation](/docs/installation/install_from_source#test-installation)
- [Build with Tags](/docs/installation/install_from_source#build-with-tags)
