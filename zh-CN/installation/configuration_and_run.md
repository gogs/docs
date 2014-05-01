---
name: 配置与运行
sort: 3
---

# 配置与运行

## 配置文件

### 默认配置文件

默认配置都保存在 `conf/app.ini`，您 **永远不需要** 编辑它。

### 自定义配置文件

那么，在不允许修改默认配置文件 `conf/app.ini` 的情况下，怎么才能自定义配置呢？很简单，只要创建 `custom/conf/app.ini` 就可以！在 `custom/conf/app.ini` 文件中修改相应选项的值即可。

例如，需要改变仓库根目录的路径：

```
[repository]
ROOT = /home/jiahuachen/gogs-repositories
```

当然，您也可以修改数据库配置：

```
[database]
PASSWD = root
```

### 为什么要这么做？

乍一看，这么做有些复杂，但是这么做可以有效地保护您的自定义配置不被破坏：

- 从二进制安装的用户，可以直接替换二进制及其它文件而不至于重新编写自定义配置。
- 从源码安装的用户，可以避免由于版本管理系统导致的文件修改冲突。

## 运行 Gogs 服务

### 开发者模式

- 您需要在 `custom/conf/app.ini` 文件中将选项 `security -> INSTALL_LOCK` 的值设置为 `true`。
- 您可以在 Gogs 源码目录使用命令 `bee run`/`fswatch`：
 - 安装 [bee](https://github.com/beego/bee) 工具：`go get -u github.com/beego/bee`
 - 安装 [fswatch](https://github.com/codeskyblue/fswatch)：`go get -u github.com/codeskyblue/fswatch`

### 部署模式

- 只需运行 `./gogs web`
- 然后访问 `/install` 来完成首次运行的配置工作