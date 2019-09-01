# Downloading Gogs via commandline

Requirements: [curl](https://wikipedia.org/wiki/CURL), [wget](https://wikipedia.org/wiki/Wget)

Simply copy & Paste the command to your terminal.
If any errors accure please file an issue so we can fix it.

* darwin_amd64.zip

```bash
curl -s https://api.github.com/repos/gogs/gogs/releases/latest \
| grep "darwin_amd64.zip" \
| cut -d : -f 2,3 \
| tr -d \" \
| wget -i -
```
* linux_386.tar.gz

```bash
curl -s https://api.github.com/repos/gogs/gogs/releases/latest \
| grep "linux_386.tar.gz" \
| cut -d : -f 2,3 \
| tr -d \" \
| wget -i -
```

* linux_386.zip

```bash
curl -s https://api.github.com/repos/gogs/gogs/releases/latest \
| grep "linux_386.zip" \
| cut -d : -f 2,3 \
| tr -d \" \
| wget -i -
```

* linux_amd64.tar.gz

```bash
curl -s https://api.github.com/repos/gogs/gogs/releases/latest \
| grep "linux_amd64.tar.gz" \
| cut -d : -f 2,3 \
| tr -d \" \
| wget -i -
```

* linux_amd64.zip

```bash
curl -s https://api.github.com/repos/gogs/gogs/releases/latest \
| grep "linux_amd64.zip" \
| cut -d : -f 2,3 \
| tr -d \" \
| wget -i -
```

* linux_armv5.zip

```bash
curl -s https://api.github.com/repos/gogs/gogs/releases/latest \
| grep "linux_armv5.zip" \
| cut -d : -f 2,3 \
| tr -d \" \
| wget -i -
```

* linux_armv6.zip

```bash
curl -s https://api.github.com/repos/gogs/gogs/releases/latest \
| grep "linux_armv6.zip" \
| cut -d : -f 2,3 \
| tr -d \" \
| wget -i -
```

* raspi_armv7.tar.gz

```bash
curl -s https://api.github.com/repos/gogs/gogs/releases/latest \
| grep "raspi_armv7.tar.gz" \
| cut -d : -f 2,3 \
| tr -d \" \
| wget -i -
```

* raspi_armv7.zip

```bash
curl -s https://api.github.com/repos/gogs/gogs/releases/latest \
| grep "raspi_armv7.zip" \
| cut -d : -f 2,3 \
| tr -d \" \
| wget -i -
```

* windows_386.zip

```bash
curl -s https://api.github.com/repos/gogs/gogs/releases/latest \
| grep "windows_386.zip" \
| cut -d : -f 2,3 \
| tr -d \" \
| wget -i -
```

* windows_386_mws.zip

```bash
curl -s https://api.github.com/repos/gogs/gogs/releases/latest \
| grep "windows_386_mws.zip" \
| cut -d : -f 2,3 \
| tr -d \" \
| wget -i -
```

* windows_amd64.zip

```bash
curl -s https://api.github.com/repos/gogs/gogs/releases/latest \
| grep "windows_amd64.zip" \
| cut -d : -f 2,3 \
| tr -d \" \
| wget -i -
```

* windows_amd64_mws.zip

```bash
curl -s https://api.github.com/repos/gogs/gogs/releases/latest \
| grep "windows_amd64_mws.zip" \
| cut -d : -f 2,3 \
| tr -d \" \
| wget -i -
```
