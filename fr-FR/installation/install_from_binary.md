---
name: Installation depuis un binaire
---

# Installation depuis un binaire


** Seuls les fichiers des 5 dernières versions sont disponibles, les fichiers plus anciens étant [disponibles ici](https://github.com/gogits/gogs/releases?after=v0.7.19).**

Touts les fichiers sont fournis avec le support de **MySQL** et **PostgreSQL** support, et compilés avec le **tag `cert`**. Le support peut varier au fil du temps et être différent pour les versions antérieures : ne pas oublier de lire les instructions pour les instances Gogs anciennes.

**Note**: `mws` signifie *Windows service support*. Utilisez-en un autre si vous utilisez NSSM.

## Utilisation du fichier téléchargé

1. Extraire l'archive
2. `cd` dans le répertoire qui vient d'être créé
3. Exécuter `./gogs web` and c'est fini

### v0.8.25 @ 2016-01-30

|Système|Type|SQLite|TiDB|PAM|Téléchargement ([GitHub](https://github.com/gogits/gogs/releases/tag/v0.8.25))|
|-------|----|------|----|---|--------|
|Linux|386|✅|❌|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.8.25_linux_386.zip) \| [TAR.GZ](https://dl.gogs.io/gogs_v0.8.25_linux_386.tar.gz) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.25_linux_386.zip) \| [TAR.GZ](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.25_linux_386.tar.gz)|
|Linux|amd64|✅|❌|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.8.25_linux_amd64.zip) \| [TAR.GZ](https://dl.gogs.io/gogs_v0.8.25_linux_amd64.tar.gz) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.25_linux_amd64.zip) \| [TAR.GZ](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.25_linux_amd64.tar.gz)|
|Linux|arm|❌|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.8.25_linux_arm.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.25_linux_arm.zip)|
|Raspberry Pi|v2|✅|❌|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.8.25_raspi2.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.25_raspi2.zip)|
|Windows|386|❌|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.8.25_windows_386.zip) \| [ZIP w/ mws](https://dl.gogs.io/gogs_v0.8.25_windows_386_mws.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.25_windows_386.zip) \| [ZIP w/mws](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.25_windows_386_mws.zip)|
|Windows|amd64|✅|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.8.25_windows_amd64.zip) \| [ZIP w/ mws](https://dl.gogs.io/gogs_v0.8.25_windows_amd64_mws.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.25_windows_amd64.zip) \| [ZIP w/ mws](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.25_windows_amd64_mws.zip)|
|Mac OS|amd64|✅|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.8.25_darwin_amd64.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.25_darwin_amd64.zip)|

### v0.8.10 @ 2015-12-18

|Système|Type|SQLite|TiDB|PAM|Téléchargement ([GitHub](https://github.com/gogits/gogs/releases/tag/v0.8.10))|
|-------|----|------|----|---|--------|
|Linux|386|✅|❌|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.8.10_linux_386.zip) \| [TAR.GZ](https://dl.gogs.io/gogs_v0.8.10_linux_386.tar.gz) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.10_linux_386.zip) \| [TAR.GZ](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.10_linux_386.tar.gz)|
|Linux|amd64|✅|❌|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.8.10_linux_amd64.zip) \| [TAR.GZ](https://dl.gogs.io/gogs_v0.8.10_linux_amd64.tar.gz) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.10_linux_amd64.zip) \| [TAR.GZ](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.10_linux_amd64.tar.gz)|
|Linux|arm|❌|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.8.10_linux_arm.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.10_linux_arm.zip)|
|Raspberry Pi|v2|✅|❌|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.8.10_raspi2.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.10_raspi2.zip)|
|Windows|386|❌|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.8.10_windows_386.zip) \| [ZIP w/ mws](https://dl.gogs.io/gogs_v0.8.10_windows_386_mws.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.10_windows_386.zip) \| [ZIP w/mws](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.10_windows_386_mws.zip)|
|Windows|amd64|✅|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.8.10_windows_amd64.zip) \| [ZIP w/ mws](https://dl.gogs.io/gogs_v0.8.10_windows_amd64_mws.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.10_windows_amd64.zip) \| [ZIP w/ mws](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.10_windows_amd64_mws.zip)|
|Mac OS|amd64|✅|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.8.10_darwin_amd64.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.10_darwin_amd64.zip)|

### v0.8.0 @ 2015-12-13

|Système|Type|SQLite|TiDB|PAM|Téléchargement|
|-------|----|------|----|---|--------------|
|Linux|386|✅|❌|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.8.0_linux_386.zip) \| [TAR.GZ](https://dl.gogs.io/gogs_v0.8.0_linux_386.tar.gz) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.0_linux_386.zip) \| [TAR.GZ](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.0_linux_386.tar.gz)|
|Linux|amd64|✅|❌|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.8.0_linux_amd64.zip) \| [TAR.GZ](https://dl.gogs.io/gogs_v0.8.0_linux_amd64.tar.gz) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.0_linux_amd64.zip) \| [TAR.GZ](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.0_linux_amd64.tar.gz)|
|Linux|arm|❌|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.8.0_linux_arm.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.0_linux_arm.zip)|
|Raspberry Pi|v2|✅|❌|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.8.0_raspi2.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.0_raspi2.zip)|
|Windows|386|❌|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.8.0_windows_386.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.0_windows_386.zip)|
|Windows|amd64|✅|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.8.0_windows_amd64.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.0_windows_amd64.zip)|
|Mac OS|amd64|✅|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.8.0_darwin_amd64.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.0_darwin_amd64.zip)|

### v0.7.33 @ 2015-12-06

|Système|Type|SQLite|TiDB|PAM|Téléchargement|
|-------|----|------|----|---|--------------|
|Linux|386|✅|✅|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.7.33_linux_386.zip) \| [TAR.GZ](https://dl.gogs.io/gogs_v0.7.33_linux_386.tar.gz) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.33_linux_386.zip) \| [TAR.GZ](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.33_linux_386.tar.gz)|
|Linux|amd64|✅|✅|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.7.33_linux_amd64.zip) \| [TAR.GZ](https://dl.gogs.io/gogs_v0.7.33_linux_amd64.tar.gz) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.33_linux_amd64.zip) \| [TAR.GZ](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.33_linux_amd64.tar.gz)|
|Linux|arm|❌|✅|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.7.33_linux_arm.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.33_linux_arm.zip)|
|Raspberry Pi|v2|✅|❌|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.7.33_raspi2.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.33_raspi2.zip)|
|Windows|386|❌|✅|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.7.33_windows_386.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.33_windows_386.zip)|
|Windows|amd64|✅|✅|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.7.33_windows_amd64.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.33_windows_amd64.zip)|
|Mac OS|amd64|✅|✅|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.7.33_darwin_amd64.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.33_darwin_amd64.zip)|

### v0.7.22 @ 2015-11-25

|Système|Type|SQLite|TiDB|PAM|Téléchargement|
|-------|----|------|----|---|--------------|
|Linux|386|✅|✅|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.7.22_linux_386.zip) \| [TAR.GZ](https://dl.gogs.io/gogs_v0.7.22_linux_386.tar.gz) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.22_linux_386.zip) \| [TAR.GZ](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.22_linux_386.tar.gz)|
|Linux|amd64|✅|✅|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.7.22_linux_amd64.zip) \| [TAR.GZ](https://dl.gogs.io/gogs_v0.7.22_linux_amd64.tar.gz) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.22_linux_amd64.zip) \| [TAR.GZ](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.22_linux_amd64.tar.gz)|
|Linux|arm|❌|✅|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.7.22_linux_arm.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.22_linux_arm.zip)|
|Raspberry Pi|v2|✅|❌|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.7.22_raspi2.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.22_raspi2.zip)|
|Windows|386|❌|✅|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.7.22_windows_386.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.22_windows_386.zip)|
|Windows|amd64|✅|✅|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.7.22_windows_amd64.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.22_windows_amd64.zip)|
|Mac OS|amd64|✅|✅|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.7.22_darwin_amd64.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.22_darwin_amd64.zip)|

Voir [Configuration and run](/docs/installation/configuration_and_run) pour aller plus loin.
