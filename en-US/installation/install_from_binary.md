---
name: From binary
---

# Install from binary

**Downloads are only available for latest 5 releases, older downloads can be found at [releases](https://github.com/gogits/gogs/releases?after=v0.7.19).**

All downloads come with **MySQL** and **PostgreSQL** support, and build **with tags `cert`**. Keep in mind that support status may be different from older releases, please follow the instructions on older Gogs instances.

**Note**: `mws` means builtin Windows service support. Please use the other one if you're using NSSM.

## How to use downloads?

1. Extract the archive.
2. `cd` into the directory just created.
3. Execute `./gogs web` and you're done.

### v0.8.10 @ 2015-12-18

|System|Type|SQLite|TiDB|PAM|Download ([GitHub](https://github.com/gogits/gogs/releases/tag/v0.8.10))|
|------|----|------|----|---|--------|
|Linux|386|✅|❌|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.8.10_linux_386.zip) \| [TAR.GZ](https://dl.gogs.io/gogs_v0.8.10_linux_386.tar.gz) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.10_linux_386.zip) \| [TAR.GZ](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.10_linux_386.tar.gz)|
|Linux|amd64|✅|❌|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.8.10_linux_amd64.zip) \| [TAR.GZ](https://dl.gogs.io/gogs_v0.8.10_linux_amd64.tar.gz) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.10_linux_amd64.zip) \| [TAR.GZ](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.10_linux_amd64.tar.gz)|
|Linux|arm|❌|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.8.10_linux_arm.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.10_linux_arm.zip)|
|Raspberry Pi|v2|✅|❌|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.8.10_raspi2.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.10_raspi2.zip)|
|Windows|386|❌|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.8.10_windows_386.zip) \| [ZIP w/ mws](https://dl.gogs.io/gogs_v0.8.10_windows_386_mws.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.10_windows_386.zip) \| [ZIP w/mws](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.10_windows_386_mws.zip)|
|Windows|amd64|✅|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.8.10_windows_amd64.zip) \| [ZIP w/ mws](https://dl.gogs.io/gogs_v0.8.10_windows_amd64_mws.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.10_windows_amd64.zip) \| [ZIP w/ mws](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.10_windows_amd64_mws.zip)|
|Mac OS|amd64|✅|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.8.10_darwin_amd64.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.10_darwin_amd64.zip)|

### v0.8.0 @ 2015-12-13

|System|Type|SQLite|TiDB|PAM|Download|
|------|----|------|----|---|--------|
|Linux|386|✅|❌|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.8.0_linux_386.zip) \| [TAR.GZ](https://dl.gogs.io/gogs_v0.8.0_linux_386.tar.gz) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.0_linux_386.zip) \| [TAR.GZ](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.0_linux_386.tar.gz)|
|Linux|amd64|✅|❌|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.8.0_linux_amd64.zip) \| [TAR.GZ](https://dl.gogs.io/gogs_v0.8.0_linux_amd64.tar.gz) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.0_linux_amd64.zip) \| [TAR.GZ](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.0_linux_amd64.tar.gz)|
|Linux|arm|❌|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.8.0_linux_arm.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.0_linux_arm.zip)|
|Raspberry Pi|v2|✅|❌|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.8.0_raspi2.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.0_raspi2.zip)|
|Windows|386|❌|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.8.0_windows_386.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.0_windows_386.zip)|
|Windows|amd64|✅|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.8.0_windows_amd64.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.0_windows_amd64.zip)|
|Mac OS|amd64|✅|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.8.0_darwin_amd64.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.8.0_darwin_amd64.zip)|

### v0.7.33 @ 2015-12-06

|System|Type|SQLite|TiDB|PAM|Download|
|------|----|------|----|---|--------|
|Linux|386|✅|✅|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.7.33_linux_386.zip) \| [TAR.GZ](https://dl.gogs.io/gogs_v0.7.33_linux_386.tar.gz) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.33_linux_386.zip) \| [TAR.GZ](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.33_linux_386.tar.gz)|
|Linux|amd64|✅|✅|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.7.33_linux_amd64.zip) \| [TAR.GZ](https://dl.gogs.io/gogs_v0.7.33_linux_amd64.tar.gz) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.33_linux_amd64.zip) \| [TAR.GZ](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.33_linux_amd64.tar.gz)|
|Linux|arm|❌|✅|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.7.33_linux_arm.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.33_linux_arm.zip)|
|Raspberry Pi|v2|✅|❌|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.7.33_raspi2.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.33_raspi2.zip)|
|Windows|386|❌|✅|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.7.33_windows_386.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.33_windows_386.zip)|
|Windows|amd64|✅|✅|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.7.33_windows_amd64.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.33_windows_amd64.zip)|
|Mac OS|amd64|✅|✅|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.7.33_darwin_amd64.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.33_darwin_amd64.zip)|

### v0.7.22 @ 2015-11-25

|System|Type|SQLite|TiDB|PAM|Download|
|------|----|------|----|---|--------|
|Linux|386|✅|✅|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.7.22_linux_386.zip) \| [TAR.GZ](https://dl.gogs.io/gogs_v0.7.22_linux_386.tar.gz) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.22_linux_386.zip) \| [TAR.GZ](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.22_linux_386.tar.gz)|
|Linux|amd64|✅|✅|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.7.22_linux_amd64.zip) \| [TAR.GZ](https://dl.gogs.io/gogs_v0.7.22_linux_amd64.tar.gz) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.22_linux_amd64.zip) \| [TAR.GZ](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.22_linux_amd64.tar.gz)|
|Linux|arm|❌|✅|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.7.22_linux_arm.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.22_linux_arm.zip)|
|Raspberry Pi|v2|✅|❌|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.7.22_raspi2.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.22_raspi2.zip)|
|Windows|386|❌|✅|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.7.22_windows_386.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.22_windows_386.zip)|
|Windows|amd64|✅|✅|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.7.22_windows_amd64.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.22_windows_amd64.zip)|
|Mac OS|amd64|✅|✅|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.7.22_darwin_amd64.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.22_darwin_amd64.zip)|

### v0.7.19 @ 2015-11-21

|System|Type|SQLite|TiDB|PAM|Download|
|------|----|------|----|---|--------|
|Linux|386|✅|✅|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.7.19_linux_386.zip) \| [TAR.GZ](https://dl.gogs.io/gogs_v0.7.19_linux_386.tar.gz) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.19_linux_386.zip) \| [TAR.GZ](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.19_linux_386.tar.gz)|
|Linux|amd64|✅|✅|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.7.19_linux_amd64.zip) \| [TAR.GZ](https://dl.gogs.io/gogs_v0.7.19_linux_amd64.tar.gz) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.19_linux_amd64.zip) \| [TAR.GZ](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.19_linux_amd64.tar.gz)|
|Linux|arm|❌|✅|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.7.19_linux_arm.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.19_linux_arm.zip)|
|Raspberry Pi|v2|✅|✅|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.7.19_raspi2.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.19_raspi2.zip)|
|Windows|386|❌|✅|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.7.19_windows_386.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.19_windows_386.zip)|
|Windows|amd64|✅|✅|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.7.19_windows_amd64.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.19_windows_amd64.zip)|
|Mac OS|amd64|✅|✅|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.7.19_darwin_amd64.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.7.19_darwin_amd64.zip)|

See [Configuration and run](/docs/installation/configuration_and_run) to go further.