---
name: From binary
---

# Install from binary

All downloads come with support for **MySQL**, **PostgreSQL**, and **TiDB**, and support self-signed certificates (build tag `cert`).

The Windows downloads "w/ mws" have built-in Windows service support; if you use NSSM, pick the alternative Windows download.

## How to use downloads?

0. Check that [prerequisites are installed](/docs/installation)
1. Extract the archive.
2. `cd` into the directory that was just created.
3. Execute `./gogs web`.
4. Gogs will start up a HTTP service at port `3000` as default. Browse `/install` for initial configuration (e.g. http://localhost:3000/install).

To go further, see [Configuration and run](/docs/installation/configuration_and_run.html).

## Downloads

Below are links to downloads for the latest releases. Older downloads can be found at [releases](https://github.com/gogs/gogs/releases).

### 0.12.3 @ 2020-10-07

|System|Type|SQLite|PAM|Download ([GitHub](https://github.com/gogs/gogs/releases/tag/v0.12.3))|
|------|----|------|---|--------|
|Linux|386|✅|✅|HTTPS: [ZIP](https://dl.gogs.io/0.12.3/gogs_0.12.3_linux_386.zip) \| [TAR.GZ](https://dl.gogs.io/0.12.3/gogs_0.12.3_linux_386.tar.gz)|
|Linux|amd64|✅|✅|HTTPS: [ZIP](https://dl.gogs.io/0.12.3/gogs_0.12.3_linux_amd64.zip) \| [TAR.GZ](https://dl.gogs.io/0.12.3/gogs_0.12.3_linux_amd64.tar.gz)|
|Linux|armv7|✅|✅|HTTPS: [ZIP](https://dl.gogs.io/0.12.3/gogs_0.12.3_linux_armv7.zip)|
|Windows|amd64|✅|❌|HTTPS: [ZIP](https://dl.gogs.io/0.12.3/gogs_0.12.3_windows_amd64.zip) \| [ZIP w/ mws](https://dl.gogs.io/0.12.3/gogs_0.12.3_windows_amd64_mws.zip)|
|macOS|amd64|✅|❌|HTTPS: [ZIP](https://dl.gogs.io/0.12.3/gogs_0.12.3_darwin_amd64.zip)|

### 0.11.91 @ 2019-08-11

|System|Type|SQLite|PAM|Download ([GitHub](https://github.com/gogs/gogs/releases/tag/v0.11.91))|
|------|----|------|---|--------|
|Linux|386|✅|✅|HTTPS: [ZIP](https://dl.gogs.io/0.11.91/gogs_0.11.91_linux_386.zip) \| [TAR.GZ](https://dl.gogs.io/0.11.91/gogs_0.11.91_linux_386.tar.gz)|
|Linux|amd64|✅|✅|HTTPS: [ZIP](https://dl.gogs.io/0.11.91/gogs_0.11.91_linux_amd64.zip) \| [TAR.GZ](https://dl.gogs.io/0.11.91/gogs_0.11.91_linux_amd64.tar.gz)|
|Linux|armv5|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/0.11.91/gogs_0.11.91_linux_armv5.zip)|
|Linux|armv6|❌|❌|HTTPS: [ZIP](https://dl.gogs.io/0.11.91/gogs_0.11.91_linux_armv6.zip)|
|Raspberry Pi|v2/v3 / armv7|✅|✅|HTTPS: [ZIP](https://dl.gogs.io/0.11.91/gogs_0.11.91_raspi_armv7.zip) \| [TAR.GZ](https://dl.gogs.io/0.11.91/gogs_0.11.91_raspi_armv7.tar.gz)|
|Windows|386|✅|❌|HTTPS: [ZIP](https://dl.gogs.io/0.11.91/gogs_0.11.91_windows_386.zip) \| [ZIP w/ mws](https://dl.gogs.io/0.11.91/gogs_0.11.91_windows_386_mws.zip)|
|Windows|amd64|✅|❌|HTTPS: [ZIP](https://dl.gogs.io/0.11.91/gogs_0.11.91_windows_amd64.zip) \| [ZIP w/ mws](https://dl.gogs.io/0.11.91/gogs_0.11.91_windows_amd64_mws.zip)|
|macOS|amd64|✅|❌|HTTPS: [ZIP](https://dl.gogs.io/0.11.91/gogs_0.11.91_darwin_amd64.zip)|
