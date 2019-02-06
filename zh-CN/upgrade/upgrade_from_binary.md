---
name: 二进制升级
---

# 从二进制升级

**相关下载可以从 [二进制安装](/docs/installation/install_from_binary) 页面查看。**

首先，确认当前安装的位置：

```bash
# 默认位置在 git 用户下的家目录
$ sudo su - git
$ cd ~
$ pwd
/home/git
$ ls
gogs gogs-repositories
```

然后将当前目录移动到另一个临时的位置，但不是删除！

```bash
$ mv gogs gogs_old
```

下载并解压新的二进制：

```bash
# 请根据系统和类型获取相应的二进制版本
$ wget https://dl.gogs.io/$VERSION/gogs_$VERSION_$OS_$ARCH.tar.gz
$ tar -zxvf gogs_$VERSION_$OS_$ARCH.tar.gz
$ ls
gogs gogs_old  gogs-repositories gogs_$VERSION_$OS_$ARCH.tar.gz
```

复制 `custom`、`data` 和 `log` 目录到新解压的目录中：

```bash
$ cp -R gogs_old/custom gogs
$ cp -R gogs_old/data gogs
$ cp -R gogs_old/log gogs
```

最后，运行并打开浏览器进行测试：

```bash
$ cd gogs
$ ./gogs web
```

给自己点一个赞！
