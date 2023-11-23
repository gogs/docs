---
name: 二进制安装
---

# 二进制安装

**目前只提供最近发布的小版本二进制下载，更多版本下载请前往 [GitHub](https://github.com/gogs/gogs/releases) 查看。**

所有的版本都支持 **MySQL**、**PostgreSQL** 和 **TiDB**（使用 MySQL 协议）作为数据库，并且均使用构建标签（build tags）**`cert`** 进行构建。需要注意的是，不同的版本的支持状态有所不同，请根据实际的 Gogs 提示进行操作。

`mws` 表示提供内置 Windows 服务支持，如果您使用 NSSM 请使用另外一个版本。

## 如何使用下载好的压缩包？

0. 检查[环境要求](/docs/installation)是否已满足
1. 解压压缩包。
2. 使用命令 `cd` 进入到刚刚创建的目录。
3. 执行命令 `.\gogs web`。
4. Gogs 默认会在端口 `3000` 启动 HTTP 服务，访问 `/install` 以进行初始配置（例如 http://localhost:3000/install ）。

安装完成后可继续参照 [配置与运行](configuration_and_run.html)。

## 下载二进制

本页仅展示最新版的二进制，旧版的二进制可以在 [GitHub release](https://github.com/gogs/gogs/releases) 上查看。

### 0.13.0 @ 2023-02-25

|系统名称|系统类型|SQLite|PAM|下载 ([GitHub](https://github.com/gogs/gogs/releases/tag/v0.13.0))|
|------|----|------|---|--------|
|Linux|386|✅|✅|HTTPS: [ZIP](https://dl.gogs.io/0.13.0/gogs_0.13.0_linux_386.zip) \| [TAR.GZ](https://dl.gogs.io/0.13.0/gogs_0.13.0_linux_386.tar.gz)|
|Linux|amd64|✅|✅|HTTPS: [ZIP](https://dl.gogs.io/0.13.0/gogs_0.13.0_linux_amd64.zip) \| [TAR.GZ](https://dl.gogs.io/0.13.0/gogs_0.13.0_linux_amd64.tar.gz)|
|Linux|armv7|✅|✅|HTTPS: [ZIP](https://dl.gogs.io/0.13.0/gogs_0.13.0_linux_armv7.zip) \| [TAR.GZ](https://dl.gogs.io/0.13.0/gogs_0.13.0_linux_armv7.tar.gz)|
|Linux|armv8|✅|✅|HTTPS: [ZIP](https://dl.gogs.io/0.13.0/gogs_0.13.0_linux_armv8.zip) \| [TAR.GZ](https://dl.gogs.io/0.13.0/gogs_0.13.0_linux_armv8.tar.gz)|
|Windows|amd64|✅|❌|HTTPS: [ZIP](https://dl.gogs.io/0.13.0/gogs_0.13.0_windows_amd64.zip) \| [ZIP w/ mws](https://dl.gogs.io/0.13.0/gogs_0.13.0_windows_amd64_mws.zip)|
|macOS|amd64|✅|❌|HTTPS: [ZIP](https://dl.gogs.io/0.13.0/gogs_0.13.0_darwin_amd64.zip)|
|macOS|arm64|✅|❌|HTTPS: [ZIP](https://dl.gogs.io/0.13.0/gogs_0.13.0_darwin_arm64.zip)|

### 0.12.11 @ 2023-02-25

|系统名称|系统类型|SQLite|PAM|下载 ([GitHub](https://github.com/gogs/gogs/releases/tag/v0.12.11))|
|------|----|------|---|--------|
|Linux|386|✅|✅|HTTPS: [ZIP](https://dl.gogs.io/0.12.11/gogs_0.12.11_linux_386.zip) \| [TAR.GZ](https://dl.gogs.io/0.12.11/gogs_0.12.11_linux_386.tar.gz)|
|Linux|amd64|✅|✅|HTTPS: [ZIP](https://dl.gogs.io/0.12.11/gogs_0.12.11_linux_amd64.zip) \| [TAR.GZ](https://dl.gogs.io/0.12.11/gogs_0.12.11_linux_amd64.tar.gz)|
|Linux|armv7|✅|✅|HTTPS: [ZIP](https://dl.gogs.io/0.12.11/gogs_0.12.11_linux_armv7.zip) \| [TAR.GZ](https://dl.gogs.io/0.12.11/gogs_0.12.11_linux_armv7.tar.gz)|
|Linux|armv8|✅|✅|HTTPS: [ZIP](https://dl.gogs.io/0.12.11/gogs_0.12.11_linux_armv8.zip) \| [TAR.GZ](https://dl.gogs.io/0.12.11/gogs_0.12.11_linux_armv8.tar.gz)|
|Windows|amd64|✅|❌|HTTPS: [ZIP](https://dl.gogs.io/0.12.11/gogs_0.12.11_windows_amd64.zip) \| [ZIP w/ mws](https://dl.gogs.io/0.12.11/gogs_0.12.11_windows_amd64_mws.zip)|
|macOS|amd64|✅|❌|HTTPS: [ZIP](https://dl.gogs.io/0.12.11/gogs_0.12.11_darwin_amd64.zip)|
|macOS|arm64|✅|❌|HTTPS: [ZIP](https://dl.gogs.io/0.12.11/gogs_0.12.11_darwin_arm64.zip)|

### 0.11.91 @ 2019-08-11

|系统名称|系统类型|SQLite|PAM|下载（[GitHub](https://github.com/gogs/gogs/releases/tag/v0.11.91)）|
|------|----|------|---|--------|
|Linux|386|✅|✅|HTTPS: [ZIP](https://dl.gogs.io/0.11.91/gogs_0.11.91_linux_386.zip) \| [TAR.GZ](https://dl.gogs.io/0.11.91/gogs_0.11.91_linux_386.tar.gz)|
|Linux|amd64|✅|✅|HTTPS: [ZIP](https://dl.gogs.io/0.11.91/gogs_0.11.91_linux_amd64.zip) \| [TAR.GZ](https://dl.gogs.io/0.11.91/gogs_0.11.91_linux_amd64.tar.gz)|
|Linux|armv5|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/0.11.91/gogs_0.11.91_linux_armv5.zip)|
|Linux|armv6|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/0.11.91/gogs_0.11.91_linux_armv6.zip)|
|Raspberry Pi|v2/v3 / armv7|✅|✅|HTTPS: [ZIP](https://dl.gogs.io/0.11.91/gogs_0.11.91_raspi_armv7.zip) \| [TAR.GZ](https://dl.gogs.io/0.11.91/gogs_0.11.91_raspi_armv7.tar.gz)|
|Windows|386|✅|❌|HTTPS: [ZIP](https://dl.gogs.io/0.11.91/gogs_0.11.91_windows_386.zip) \| [ZIP w/ mws](https://dl.gogs.io/0.11.91/gogs_0.11.91_windows_386_mws.zip)|
|Windows|amd64|✅|❌|HTTPS: [ZIP](https://dl.gogs.io/0.11.91/gogs_0.11.91_windows_amd64.zip) \| [ZIP w/ mws](https://dl.gogs.io/0.11.91/gogs_0.11.91_windows_amd64_mws.zip)|
|macOS|amd64|✅|❌|HTTPS: [ZIP](https://dl.gogs.io/0.11.91/gogs_0.11.91_darwin_amd64.zip)|
