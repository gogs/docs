---
name: 二进制安装
---

# 二进制安装

所有的版本都支持 **PostgreSQL**、**MySQL**、和 **SQLite 3** 作为数据库后端。

带有 `mws` 后缀的下载表示提供内置 Windows 服务支持，如果您使用 NSSM 请下载正常版本的文件。

请访问 [dl.gogs.io](https://dl.gogs.io) 和 [GitHub releases](https://github.com/gogs/gogs/releases) 获取对应版本的下载文件。

## 如何使用下载好的压缩包？

1. 检查[环境要求](/docs/installation)是否已满足
2. 解压压缩包。
3. 使用命令 `cd` 进入到刚刚创建的目录。
4. 执行命令 `./gogs web`。
5. Gogs 默认会在端口 `3000` 启动 HTTP 服务，访问 `/install` 以进行初始配置（例如 http://localhost:3000/install ）。

安装完成后可继续参照 [配置与运行](configuration_and_run.html)。
