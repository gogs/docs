---
name: 二进制安装
sort: 1
---

# 二进制安装

我们目前只提供 64 位操作系统的二进制。你也可以自己构建二进制包。

## 如何自己构建二进制包？

1. 先[构建分支](http://gogs.io/docs/installation/install_from_source.html#%E6%9E%84%E5%BB%BA-develop-%E5%88%86%E6%94%AF%E7%89%88%E6%9C%AC)版本，如有必要，[构建 SQLite3/Redis/Memcache 集成版](http://gogs.io/docs/installation/install_from_source.html#%E6%9E%84%E5%BB%BA-sqlite3%2Fredis%2Fmemcache-%E9%9B%86%E6%88%90%E7%89%88)
2. 手动构建二进制
```bash
cd $GOPATH/src/github.com/gogits/gogs/scripts
# 32位系统可以使用 
./build.sh
# bsd系统可以使用 
./build_freebsd.sh
# 64位系统可以使用
./build_linux64.sh
```
3. 运行，检查功能
```bash
cd output_amd64
./gogs web
```

4. 生成二进制包
```bash
# 确定自从构建之后就没有做过任何的修改才可以平滑升级,但是在运行的时候以防万一
./build_linux64.sh
mv output_amd64 gogs
zip -r gogs.zip gogs
```

## 如何通过二进制升级？

1. 下载最新版的二进制 ZIP 压缩包。
2. 删除当前的 `templates` 目录。
3. 解压压缩包并将所有内容复制粘贴到相应位置。

### v0.6.5 @ 2015-8-16

- CDN：[Windows](http://gogs.dn.qbox.me/gogs_v0.6.5_windows_amd64.zip) - [Linux](http://gogs.dn.qbox.me/gogs_v0.6.5_linux_amd64.zip) - [Mac OS X](http://gogs.dn.qbox.me/gogs_v0.6.5_darwin_amd64.zip)
- [GitHub](https://github.com/gogits/gogs/releases/tag/v0.6.5)

安装完成后可继续参照 [配置与运行](configuration_and_run.md)。

### v0.6.3 @ 2015-8-2

- CDN：~~[Windows](http://gogs.dn.qbox.me/gogs_v0.6.3_windows_amd64.zip) - [Linux](http://gogs.dn.qbox.me/gogs_v0.6.3_linux_amd64.zip) - [Mac OS X](http://gogs.dn.qbox.me/gogs_v0.6.3_darwin_amd64.zip)~~
- ~~[GitHub](https://github.com/gogits/gogs/releases/tag/v0.6.3)~~

### v0.6.1 @ 2015-3-26

- CDN：~~[Windows](http://gogs.dn.qbox.me/gogs_v0.6.1_windows_amd64.zip) - [Linux](http://gogs.dn.qbox.me/gogs_v0.6.1_linux_amd64.zip) - [Mac OS X](http://gogs.dn.qbox.me/gogs_v0.6.1_darwin_amd64.zip)~~
- ~~[GitHub](https://github.com/gogits/gogs/releases/tag/v0.6.1)~~

### v0.6.0 @ 2015-3-19

- CDN：~~[Windows](http://gogs.dn.qbox.me/gogs_v0.6.0_windows_amd64.zip) - [Linux](http://gogs.dn.qbox.me/gogs_v0.6.0_linux_amd64.zip) - [Mac OS X](http://gogs.dn.qbox.me/gogs_v0.6.0_darwin_amd64.zip)~~
- ~~[GitHub](https://github.com/gogits/gogs/releases/tag/v0.6.0)~~

### v0.5.13 @ 2015-2-13

- CDN：~~[Windows](http://gogs.dn.qbox.me/gogs_v0.5.13_windows_amd64.zip) - [Linux](http://gogs.dn.qbox.me/gogs_v0.5.13_linux_amd64.zip) - [Mac OS X](http://gogs.dn.qbox.me/gogs_v0.5.13_darwin_amd64.zip)~~
- ~~[GitHub](https://github.com/gogits/gogs/releases/tag/v0.5.13)~~

### v0.5.11 @ 2015-1-5

- CDN：~~[Linux](http://gogs.dn.qbox.me/gogs_v0.5.11_linux_amd64.zip) - [Mac OS X](http://gogs.dn.qbox.me/gogs_v0.5.11_darwin_amd64.zip)~~
- ~~[GitHub](https://github.com/gogits/gogs/releases/tag/v0.5.11)~~

### v0.5.9 @ 2014-12-13

- CDN：[Windows](http://gogs.dn.qbox.me/gogs_v0.5.9_windows_amd64.zip) - [Linux](http://gogs.dn.qbox.me/gogs_v0.5.9_linux_amd64.zip) - [Mac OS X](http://gogs.dn.qbox.me/gogs_v0.5.9_darwin_amd64.zip)
- [GitHub](https://github.com/gogits/gogs/releases/tag/v0.5.9)

### v0.5.8 @ 2014-11-19

- ~~CDN：[Windows](http://gogs.dn.qbox.me/gogs_v0.5.8_windows_amd64.zip) - [Linux](http://gogs.dn.qbox.me/gogs_v0.5.8_linux_amd64.zip) - [Mac OS X](http://gogs.dn.qbox.me/gogs_v0.5.8_darwin_amd64.zip)~~
- ~~[GitHub](https://github.com/gogits/gogs/releases/tag/v0.5.8)~~

### v0.5.5 @ 2014-10-10

- CDN：~~[Windows](http://gogs.dn.qbox.me/gogs_v0.5.5_windows_amd64.zip) - [Linux](http://gogs.dn.qbox.me/gogs_v0.5.5_linux_amd64.zip) - [Mac OS X](http://gogs.dn.qbox.me/gogs_v0.5.5_darwin_amd64.zip)~~
- ~~[GitHub](https://github.com/gogits/gogs/releases/tag/v0.5.5)~~

**更早的版本可以通过 [GitHub](https://github.com/gogits/gogs/releases) 下载。**
