---
name: 二进制安装
---

# 二进制安装

**目前只提供最近 5 次版本发布的二进制下载，更多版本下载请前往 [GitHub](https://github.com/gogits/gogs/releases?after=v0.9.71) 查看。**

所有的版本都支持 **MySQL**、**PostgreSQL** 和 **TiDB**（使用 MySQL 协议）作为数据库，并且均使用构建标签（build tags）**`cert`** 进行构建。需要注意的是，不同的版本的支持状态有所不同，请根据实际的 Gogs 提示进行操作。

## 备注

- `mws` 表示提供内置 Windows 服务支持，如果您使用 NSSM 请使用另外一个版本。

## 如何使用下载好的压缩包？

1. 解压压缩包。
2. 使用命令 `cd` 进入到刚刚创建的目录。
3. 执行命令 `./gogs web`，然后，就没有然后了。

## 如何通过二进制升级？

1. 下载最新版的压缩包。
2. 删除当前的 `templates` 目录。
3. 解压压缩包并将所有内容复制粘贴到相应（当前）的位置。

### v0.9.141 @ 2017-02-11

|系统名称|系统类型|SQLite|PAM|下载（[GitHub](https://github.com/gogits/gogs/releases/tag/v0.9.141)）|
|------|----|------|----|---|--------|
|Linux|386|✅|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.9.141_linux_386.zip) \| [TAR.GZ](https://dl.gogs.io/gogs_v0.9.141_linux_386.tar.gz) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.141_linux_386.zip) \| [TAR.GZ](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.141_linux_386.tar.gz)|
|Linux|amd64|✅|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.9.141_linux_amd64.zip) \| [TAR.GZ](https://dl.gogs.io/gogs_v0.9.141_linux_amd64.tar.gz) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.141_linux_amd64.zip) \| [TAR.GZ](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.141_linux_amd64.tar.gz)|
|Linux|armv5|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.9.141_linux_armv5.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.141_linux_armv5.zip)|
|Linux|armv6|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.9.141_linux_armv6.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.141_linux_armv6.zip)|
|Raspberry Pi|v2|✅|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.9.141_raspi2.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.141_raspi2.zip)|
|Windows|386|✅|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.9.141_windows_386.zip) \| [ZIP w/ mws](https://dl.gogs.io/gogs_v0.9.141_windows_386_mws.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.141_windows_386.zip) \| [ZIP w/mws](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.141_windows_386_mws.zip)|
|Windows|amd64|✅|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.9.141_windows_amd64.zip) \| [ZIP w/ mws](https://dl.gogs.io/gogs_v0.9.141_windows_amd64_mws.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.141_windows_amd64.zip) \| [ZIP w/ mws](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.141_windows_amd64_mws.zip)|
|Mac OS|amd64|✅|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.9.141_darwin_amd64.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.141_darwin_amd64.zip)|

### v0.9.128 @ 2017-01-31

|系统名称|系统类型|SQLite|TiDB|PAM|下载（[GitHub](https://github.com/gogits/gogs/releases/tag/v0.9.128)）|
|------|----|------|----|---|--------|
|Linux|386|✅|❌|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.9.128_linux_386.zip) \| [TAR.GZ](https://dl.gogs.io/gogs_v0.9.128_linux_386.tar.gz) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.128_linux_386.zip) \| [TAR.GZ](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.128_linux_386.tar.gz)|
|Linux|amd64|✅|❌|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.9.128_linux_amd64.zip) \| [TAR.GZ](https://dl.gogs.io/gogs_v0.9.128_linux_amd64.tar.gz) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.128_linux_amd64.zip) \| [TAR.GZ](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.128_linux_amd64.tar.gz)|
|Linux|armv5|❌|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.9.128_linux_armv5.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.128_linux_armv5.zip)|
|Linux|armv6|❌|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.9.128_linux_armv6.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.128_linux_armv6.zip)|
|Raspberry Pi|v2|✅|❌|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.9.128_raspi2.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.128_raspi2.zip)|
|Windows|386|✅|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.9.128_windows_386.zip) \| [ZIP w/ mws](https://dl.gogs.io/gogs_v0.9.128_windows_386_mws.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.128_windows_386.zip) \| [ZIP w/mws](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.128_windows_386_mws.zip)|
|Windows|amd64|✅|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.9.128_windows_amd64.zip) \| [ZIP w/ mws](https://dl.gogs.io/gogs_v0.9.128_windows_amd64_mws.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.128_windows_amd64.zip) \| [ZIP w/ mws](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.128_windows_amd64_mws.zip)|
|Mac OS|amd64|✅|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.9.128_darwin_amd64.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.128_darwin_amd64.zip)|

### v0.9.113 @ 2016-12-24

|系统名称|系统类型|SQLite|TiDB|PAM|下载（[GitHub](https://github.com/gogits/gogs/releases/tag/v0.9.113)）|
|------|----|------|----|---|--------|
|Linux|386|✅|❌|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.9.113_linux_386.zip) \| [TAR.GZ](https://dl.gogs.io/gogs_v0.9.113_linux_386.tar.gz) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.113_linux_386.zip) \| [TAR.GZ](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.113_linux_386.tar.gz)|
|Linux|amd64|✅|❌|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.9.113_linux_amd64.zip) \| [TAR.GZ](https://dl.gogs.io/gogs_v0.9.113_linux_amd64.tar.gz) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.113_linux_amd64.zip) \| [TAR.GZ](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.113_linux_amd64.tar.gz)|
|Linux|armv5|❌|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.9.113_linux_armv5.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.113_linux_armv5.zip)|
|Linux|armv6|❌|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.9.113_linux_armv6.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.113_linux_armv6.zip)|
|Raspberry Pi|v2|✅|❌|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.9.113_raspi2.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.113_raspi2.zip)|
|Windows|386|✅|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.9.113_windows_386.zip) \| [ZIP w/ mws](https://dl.gogs.io/gogs_v0.9.113_windows_386_mws.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.113_windows_386.zip) \| [ZIP w/mws](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.113_windows_386_mws.zip)|
|Windows|amd64|✅|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.9.113_windows_amd64.zip) \| [ZIP w/ mws](https://dl.gogs.io/gogs_v0.9.113_windows_amd64_mws.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.113_windows_amd64.zip) \| [ZIP w/ mws](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.113_windows_amd64_mws.zip)|
|Mac OS|amd64|✅|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.9.113_darwin_amd64.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.113_darwin_amd64.zip)|

### v0.9.97 @ 2016-09-01

|系统名称|系统类型|SQLite|TiDB|PAM|下载（[GitHub](https://github.com/gogits/gogs/releases/tag/v0.9.97)）|
|------|----|------|----|---|--------|
|Linux|386|✅|❌|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.9.97_linux_386.zip) \| [TAR.GZ](https://dl.gogs.io/gogs_v0.9.97_linux_386.tar.gz) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.97_linux_386.zip) \| [TAR.GZ](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.97_linux_386.tar.gz)|
|Linux|amd64|✅|❌|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.9.97_linux_amd64.zip) \| [TAR.GZ](https://dl.gogs.io/gogs_v0.9.97_linux_amd64.tar.gz) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.97_linux_amd64.zip) \| [TAR.GZ](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.97_linux_amd64.tar.gz)|
|Linux|arm|❌|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.9.97_linux_arm.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.97_linux_arm.zip)|
|Raspberry Pi|v2|✅|❌|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.9.97_raspi2.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.97_raspi2.zip)|
|Windows|386|✅|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.9.97_windows_386.zip) \| [ZIP w/ mws](https://dl.gogs.io/gogs_v0.9.97_windows_386_mws.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.97_windows_386.zip) \| [ZIP w/mws](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.97_windows_386_mws.zip)|
|Windows|amd64|✅|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.9.97_windows_amd64.zip) \| [ZIP w/ mws](https://dl.gogs.io/gogs_v0.9.97_windows_amd64_mws.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.97_windows_amd64.zip) \| [ZIP w/ mws](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.97_windows_amd64_mws.zip)|
|Mac OS|amd64|✅|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.9.97_darwin_amd64.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.97_darwin_amd64.zip)|

### v0.9.71 @ 2016-08-10

|系统名称|系统类型|SQLite|TiDB|PAM|下载（[GitHub](https://github.com/gogits/gogs/releases/tag/v0.9.71)）|
|------|----|------|----|---|--------|
|Linux|386|✅|❌|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.9.71_linux_386.zip) \| [TAR.GZ](https://dl.gogs.io/gogs_v0.9.71_linux_386.tar.gz) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.71_linux_386.zip) \| [TAR.GZ](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.71_linux_386.tar.gz)|
|Linux|amd64|✅|❌|✅|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.9.71_linux_amd64.zip) \| [TAR.GZ](https://dl.gogs.io/gogs_v0.9.71_linux_amd64.tar.gz) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.71_linux_amd64.zip) \| [TAR.GZ](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.71_linux_amd64.tar.gz)|
|Linux|arm|❌|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.9.71_linux_arm.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.71_linux_arm.zip)|
|Raspberry Pi|v2|N/A|N/A|N/A|LOCAL: N/A - CDN: N/A|
|Windows|386|✅|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.9.71_windows_386.zip) \| [ZIP w/ mws](https://dl.gogs.io/gogs_v0.9.71_windows_386_mws.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.71_windows_386.zip) \| [ZIP w/mws](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.71_windows_386_mws.zip)|
|Windows|amd64|✅|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.9.71_windows_amd64.zip) \| [ZIP w/ mws](https://dl.gogs.io/gogs_v0.9.71_windows_amd64_mws.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.71_windows_amd64.zip) \| [ZIP w/ mws](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.71_windows_amd64_mws.zip)|
|Mac OS|amd64|✅|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/gogs_v0.9.71_darwin_amd64.zip) - CDN: [ZIP](http://7d9nal.com2.z0.glb.qiniucdn.com/gogs_v0.9.71_darwin_amd64.zip)|

安装完成后可继续参照 [配置与运行](configuration_and_run.html)。
