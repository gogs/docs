---
name: 源码安装
---

# 源码安装

## 安装 Go 语言

Gogs 要求至少使用 Go 1.14 或更高的版本进行编译，具体安装步骤请参考 [官方文档](https://golang.org/doc/install)。

## 设置环境

我们将创建一个名为 `git` 用户，并在该用户空间内完成剩余的安装步骤：

```sh
sudo adduser --disabled-login --gecos 'Gogs' git
```

## 编译 Gogs

```sh
# 克隆仓库到 "gogs" 子目录
git clone --depth 1 https://github.com/gogs/gogs.git gogs
# 修改工作目录
cd gogs
# 编译主程序，这个步骤会下载所有依赖
go build -o gogs
```

## 测试安装

您可以通过以下方式检查 Gogs 是否可以正常工作：

```sh
./gogs web
```

如果您没有发现任何错误信息，则可以使用 `Ctrl-C` 来终止运行。

## 使用标签构建

Gogs 默认并没有支持一些功能，这些功能需要在构建时明确使用构建标签（[build tags](https://golang.org/pkg/go/build/#hdr-Build_Constraints)）来支持。

目前使用标签构建的功能如下：

- `sqlite3`：SQLite3 数据库支持
- `pam`：PAM 授权认证支持
- `cert`：生成自定义证书支持
- `minwinsvc`：Windows 服务内置支持（或者您可以使用 NSSM 来创建服务）

```sh
go build -tags "sqlite pam cert" -o gogs
```

安装完成后可继续参照 [配置与运行](configuration_and_run.html)。
