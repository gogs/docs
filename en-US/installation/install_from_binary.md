---
name: From binary
---

# Install from binary

**Downloads are only available for latest 5 releases, older downloads can be found at [releases](https://github.com/gogits/gogs/releases?after=v0.9.13).**

All downloads come with **MySQL** and **PostgreSQL** support, and build **with tags `cert`**. Keep in mind that support status may be different from older releases, please follow the instructions on older Gogs instances.

## Notes

- `mws` means builtin Windows service support. Please use the other one if you're using NSSM.

## How to use downloads?

1. Extract the archive.
2. `cd` into the directory just created.
3. Execute `./gogs web` and you're done.

### v0.9.71 @ 2016-08-10

|System|Type|SQLite|TiDB|PAM|Download ([GitHub](https://github.com/gogits/gogs/releases/tag/v0.9.71))|
|------|----|------|----|---|--------|
|Linux|386|✅|❌|✅|LOCAL: [ZIP](https://dl.gogs.io/gogs_v0.9.71_linux_386.zip) \| [TAR.GZ](https://dl.gogs.io/gogs_v0.9.71_linux_386.tar.gz) - CDN: [ZIP](https://cdn.gogs.io/gogs_v0.9.71_linux_386.zip) \| [TAR.GZ](https://cdn.gogs.io/gogs_v0.9.71_linux_386.tar.gz)|
|Linux|amd64|✅|❌|✅|LOCAL: [ZIP](https://dl.gogs.io/gogs_v0.9.71_linux_amd64.zip) \| [TAR.GZ](https://dl.gogs.io/gogs_v0.9.71_linux_amd64.tar.gz) - CDN: [ZIP](https://cdn.gogs.io/gogs_v0.9.71_linux_amd64.zip) \| [TAR.GZ](https://cdn.gogs.io/gogs_v0.9.71_linux_amd64.tar.gz)|
|Linux|arm|❌|❌|❌|LOCAL: [ZIP](https://dl.gogs.io/gogs_v0.9.71_linux_arm.zip) - CDN: [ZIP](https://cdn.gogs.io/gogs_v0.9.71_linux_arm.zip)|
|Raspberry Pi|v2|N/A|N/A|N/A|LOCAL: N/A - CDN: N/A|
|Windows|386|✅|❌|❌|LOCAL: [ZIP](https://dl.gogs.io/gogs_v0.9.71_windows_386.zip) \| [ZIP w/ mws](https://dl.gogs.io/gogs_v0.9.71_windows_386_mws.zip) - CDN: [ZIP](https://cdn.gogs.io/gogs_v0.9.71_windows_386.zip) \| [ZIP w/mws](https://cdn.gogs.io/gogs_v0.9.71_windows_386_mws.zip)|
|Windows|amd64|✅|❌|❌|LOCAL: [ZIP](https://dl.gogs.io/gogs_v0.9.71_windows_amd64.zip) \| [ZIP w/ mws](https://dl.gogs.io/gogs_v0.9.71_windows_amd64_mws.zip) - CDN: [ZIP](https://cdn.gogs.io/gogs_v0.9.71_windows_amd64.zip) \| [ZIP w/ mws](https://cdn.gogs.io/gogs_v0.9.71_windows_amd64_mws.zip)|
|Mac OS|amd64|✅|❌|❌|LOCAL: [ZIP](https://dl.gogs.io/gogs_v0.9.71_darwin_amd64.zip) - CDN: [ZIP](https://cdn.gogs.io/gogs_v0.9.71_darwin_amd64.zip)|

### v0.9.60 @ 2016-08-03

|System|Type|SQLite|TiDB|PAM|Download ([GitHub](https://github.com/gogits/gogs/releases/tag/v0.9.60))|
|------|----|------|----|---|--------|
|Linux|386|✅|❌|✅|LOCAL: [ZIP](https://dl.gogs.io/gogs_v0.9.60_linux_386.zip) \| [TAR.GZ](https://dl.gogs.io/gogs_v0.9.60_linux_386.tar.gz) - CDN: [ZIP](https://cdn.gogs.io/gogs_v0.9.60_linux_386.zip) \| [TAR.GZ](https://cdn.gogs.io/gogs_v0.9.60_linux_386.tar.gz)|
|Linux|amd64|✅|❌|✅|LOCAL: [ZIP](https://dl.gogs.io/gogs_v0.9.60_linux_amd64.zip) \| [TAR.GZ](https://dl.gogs.io/gogs_v0.9.60_linux_amd64.tar.gz) - CDN: [ZIP](https://cdn.gogs.io/gogs_v0.9.60_linux_amd64.zip) \| [TAR.GZ](https://cdn.gogs.io/gogs_v0.9.60_linux_amd64.tar.gz)|
|Linux|arm|❌|❌|❌|LOCAL: [ZIP](https://dl.gogs.io/gogs_v0.9.60_linux_arm.zip) - CDN: [ZIP](https://cdn.gogs.io/gogs_v0.9.60_linux_arm.zip)|
|Raspberry Pi|v2|✅|❌|✅|LOCAL: [ZIP](https://dl.gogs.io/gogs_v0.9.60_raspi2.zip) - CDN: [ZIP](https://cdn.gogs.io/gogs_v0.9.60_raspi2.zip)|
|Windows|386|✅|❌|❌|LOCAL: [ZIP](https://dl.gogs.io/gogs_v0.9.60_windows_386.zip) \| [ZIP w/ mws](https://dl.gogs.io/gogs_v0.9.60_windows_386_mws.zip) - CDN: [ZIP](https://cdn.gogs.io/gogs_v0.9.60_windows_386.zip) \| [ZIP w/mws](https://cdn.gogs.io/gogs_v0.9.60_windows_386_mws.zip)|
|Windows|amd64|✅|❌|❌|LOCAL: [ZIP](https://dl.gogs.io/gogs_v0.9.60_windows_amd64.zip) \| [ZIP w/ mws](https://dl.gogs.io/gogs_v0.9.60_windows_amd64_mws.zip) - CDN: [ZIP](https://cdn.gogs.io/gogs_v0.9.60_windows_amd64.zip) \| [ZIP w/ mws](https://cdn.gogs.io/gogs_v0.9.60_windows_amd64_mws.zip)|
|Mac OS|amd64|✅|❌|❌|LOCAL: [ZIP](https://dl.gogs.io/gogs_v0.9.60_darwin_amd64.zip) - CDN: [ZIP](https://cdn.gogs.io/gogs_v0.9.60_darwin_amd64.zip)|

### v0.9.48 @ 2016-07-22

|System|Type|SQLite|TiDB|PAM|Download ([GitHub](https://github.com/gogits/gogs/releases/tag/v0.9.48))|
|------|----|------|----|---|--------|
|Linux|386|✅|❌|✅|LOCAL: [ZIP](https://dl.gogs.io/gogs_v0.9.48_linux_386.zip) \| [TAR.GZ](https://dl.gogs.io/gogs_v0.9.48_linux_386.tar.gz) - CDN: [ZIP](https://cdn.gogs.io/gogs_v0.9.48_linux_386.zip) \| [TAR.GZ](https://cdn.gogs.io/gogs_v0.9.48_linux_386.tar.gz)|
|Linux|amd64|✅|❌|✅|LOCAL: [ZIP](https://dl.gogs.io/gogs_v0.9.48_linux_amd64.zip) \| [TAR.GZ](https://dl.gogs.io/gogs_v0.9.48_linux_amd64.tar.gz) - CDN: [ZIP](https://cdn.gogs.io/gogs_v0.9.48_linux_amd64.zip) \| [TAR.GZ](https://cdn.gogs.io/gogs_v0.9.48_linux_amd64.tar.gz)|
|Linux|arm|❌|❌|❌|LOCAL: [ZIP](https://dl.gogs.io/gogs_v0.9.48_linux_arm.zip) - CDN: [ZIP](https://cdn.gogs.io/gogs_v0.9.48_linux_arm.zip)|
|Raspberry Pi|v2|✅|❌|✅|LOCAL: [ZIP](https://dl.gogs.io/gogs_v0.9.48_raspi2.zip) - CDN: [ZIP](https://cdn.gogs.io/gogs_v0.9.48_raspi2.zip)|
|Windows|386|✅|❌|❌|LOCAL: [ZIP](https://dl.gogs.io/gogs_v0.9.48_windows_386.zip) \| [ZIP w/ mws](https://dl.gogs.io/gogs_v0.9.48_windows_386_mws.zip) - CDN: [ZIP](https://cdn.gogs.io/gogs_v0.9.48_windows_386.zip) \| [ZIP w/mws](https://cdn.gogs.io/gogs_v0.9.48_windows_386_mws.zip)|
|Windows|amd64|✅|❌|❌|LOCAL: [ZIP](https://dl.gogs.io/gogs_v0.9.48_windows_amd64.zip) \| [ZIP w/ mws](https://dl.gogs.io/gogs_v0.9.48_windows_amd64_mws.zip) - CDN: [ZIP](https://cdn.gogs.io/gogs_v0.9.48_windows_amd64.zip) \| [ZIP w/ mws](https://cdn.gogs.io/gogs_v0.9.48_windows_amd64_mws.zip)|
|Mac OS|amd64|✅|❌|❌|LOCAL: [ZIP](https://dl.gogs.io/gogs_v0.9.48_darwin_amd64.zip) - CDN: [ZIP](https://cdn.gogs.io/gogs_v0.9.48_darwin_amd64.zip)|

### v0.9.46 @ 2016-07-17

|System|Type|SQLite|TiDB|PAM|Download ([GitHub](https://github.com/gogits/gogs/releases/tag/v0.9.46))|
|------|----|------|----|---|--------|
|Linux|386|N/A|N/A|N/A|LOCAL: N/A - CDN: N/A|
|Linux|amd64|✅|❌|✅|LOCAL: [ZIP](https://dl.gogs.io/gogs_v0.9.46_linux_amd64.zip) \| [TAR.GZ](https://dl.gogs.io/gogs_v0.9.46_linux_amd64.tar.gz) - CDN: [ZIP](https://cdn.gogs.io/gogs_v0.9.46_linux_amd64.zip) \| [TAR.GZ](https://cdn.gogs.io/gogs_v0.9.46_linux_amd64.tar.gz)|
|Linux|arm|❌|❌|❌|LOCAL: [ZIP](https://dl.gogs.io/gogs_v0.9.46_linux_arm.zip) - CDN: [ZIP](https://cdn.gogs.io/gogs_v0.9.46_linux_arm.zip)|
|Raspberry Pi|v2|N/A|N/A|N/A|LOCAL: N/A - CDN: N/A|
|Windows|386|N/A|N/A|N/A|LOCAL: N/A - CDN: N/A|
|Windows|amd64|✅|❌|❌|LOCAL: [ZIP](https://dl.gogs.io/gogs_v0.9.46_windows_amd64.zip) \| [ZIP w/ mws](https://dl.gogs.io/gogs_v0.9.46_windows_amd64_mws.zip) - CDN: [ZIP](https://cdn.gogs.io/gogs_v0.9.46_windows_amd64.zip) \| [ZIP w/ mws](https://cdn.gogs.io/gogs_v0.9.46_windows_amd64_mws.zip)|
|Mac OS|amd64|✅|❌|❌|LOCAL: [ZIP](https://dl.gogs.io/gogs_v0.9.46_darwin_amd64.zip) - CDN: [ZIP](https://cdn.gogs.io/gogs_v0.9.46_darwin_amd64.zip)|

### v0.9.13 @ 2016-03-19

|System|Type|SQLite|TiDB|PAM|Download ([GitHub](https://github.com/gogits/gogs/releases/tag/v0.9.13))|
|------|----|------|----|---|--------|
|Linux|386|✅|❌|✅|LOCAL: [ZIP](https://dl.gogs.io/gogs_v0.9.13_linux_386.zip) \| [TAR.GZ](https://dl.gogs.io/gogs_v0.9.13_linux_386.tar.gz) - CDN: [ZIP](https://cdn.gogs.io/gogs_v0.9.13_linux_386.zip) \| [TAR.GZ](https://cdn.gogs.io/gogs_v0.9.13_linux_386.tar.gz)|
|Linux|amd64|✅|❌|✅|LOCAL: [ZIP](https://dl.gogs.io/gogs_v0.9.13_linux_amd64.zip) \| [TAR.GZ](https://dl.gogs.io/gogs_v0.9.13_linux_amd64.tar.gz) - CDN: [ZIP](https://cdn.gogs.io/gogs_v0.9.13_linux_amd64.zip) \| [TAR.GZ](https://cdn.gogs.io/gogs_v0.9.13_linux_amd64.tar.gz)|
|Linux|arm|❌|❌|❌|LOCAL: [ZIP](https://dl.gogs.io/gogs_v0.9.13_linux_arm.zip) - CDN: [ZIP](https://cdn.gogs.io/gogs_v0.9.13_linux_arm.zip)|
|Raspberry Pi|v2|✅|❌|✅|LOCAL: [ZIP](https://dl.gogs.io/gogs_v0.9.13_raspi2.zip) - CDN: [ZIP](https://cdn.gogs.io/gogs_v0.9.13_raspi2.zip)|
|Windows|386|✅|❌|❌|LOCAL: [ZIP](https://dl.gogs.io/gogs_v0.9.13_windows_386.zip) \| [ZIP w/ mws](https://dl.gogs.io/gogs_v0.9.13_windows_386_mws.zip) - CDN: [ZIP](https://cdn.gogs.io/gogs_v0.9.13_windows_386.zip) \| [ZIP w/mws](https://cdn.gogs.io/gogs_v0.9.13_windows_386_mws.zip)|
|Windows|amd64|✅|❌|❌|LOCAL: [ZIP](https://dl.gogs.io/gogs_v0.9.13_windows_amd64.zip) \| [ZIP w/ mws](https://dl.gogs.io/gogs_v0.9.13_windows_amd64_mws.zip) - CDN: [ZIP](https://cdn.gogs.io/gogs_v0.9.13_windows_amd64.zip) \| [ZIP w/ mws](https://cdn.gogs.io/gogs_v0.9.13_windows_amd64_mws.zip)|
|Mac OS|amd64|✅|❌|❌|LOCAL: [ZIP](https://dl.gogs.io/gogs_v0.9.13_darwin_amd64.zip) - CDN: [ZIP](https://cdn.gogs.io/gogs_v0.9.13_darwin_amd64.zip)|

See [Configuration and run](/docs/installation/configuration_and_run) to go further.