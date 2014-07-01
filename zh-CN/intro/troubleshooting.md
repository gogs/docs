---
name: 故障排查
sort: 2
---

# 故障排查

### Git

#### `git push` through SSH get error `bash /path/to/gogs: no such file or directory`

这是因为您修改了 Gogs 服务器的路径后导致新的路径与记录在 `~/.ssh/authorized_keys` 文件中的不同。

#### fatal: 'XX/XX.git' does not appear to be a git repository

这是因为 `authorized_keys` 文件已经存在和您添加到 Gogs 中相同的 Key，删除旧的 Key 即可。

#### `repo.NewRepoContext(fail to set git user.email):`

该错误会发生在 Windows 安装 Git Bash 时未启用 `cmd` 选项，需要重装并启用选项。

#### 无法通过 SSH 操作仓库

- 您的机器上同时有 GitLab 和 Gogs 使用同一个 `authorized_keys` 文件。

### Register/create user/repository

#### `Repository/User name contains illegal characters`

为了防止不必要的异常，您的用户名或仓库在符合以下任意一条规则时会被认为非法： 

- 名称为 `"raw", "install", "api", "avatar", "user", "org", "help", "stars", "issues", "pulls", "commits", "repo", "template", "admin", "new"`。
- 名称后缀为 `".git"`。

### Cache

#### `cache: unknown adaptername "memcache" (forgotten import?)`

为了减少不必要的导入，您需要使用构建 tags 来启用某个缓存适配器：

- 下载：`go get -tags memcache github.com/gogits.gogs`
- 构建：`go build -tags memcache`

如果要启用 `redis` 也是一样的步骤。

### MySQL

#### `Error 1071: Specified key was too long; max key length is 1000 bytes`

这是由于数据库引擎为 MyISAM 导致的。在使用 `config/mysql.sql` 创建完数据库后，进入数据库然后执行：

```sql
use gogs;
set global storage_engine=INNODB;
```

最后，访问 [http://localhost:3000/install](http://localhost:3000/install) 即可（感谢 [@linc01n](https://github.com/linc01n)）。

### 邮件服务

#### 无法发送邮件

目前 Go 语言不支持基于 SSL 的电子邮件，所以请选择一个不需要 SSL 验证的端口。如果您知道如何使用 Go 语言发送基于 SSL 的电子邮件，请联系我们！

#### Gmail 发送返回 Error 534: `Please log in via your web browser and then try again`

这是因为 Google 不信任您的服务器导致的。首先，访问 https://accounts.google.com 并登录，然后访问 https://accounts.google.com/DisplayUnlockCaptcha 单击 `continue`，然后重试发送。

### 其它

#### `Error 1062: Duplicate entry 'Unknown-Mac' for key 'UQE_public_key_name'`

这是由于遗留代码导致的，`public_key` 表之前含有唯一索引 `UQE_public_key_name`，您只需删除它即可。

#### `GLIBC_2.14 not found`

尝试 `sudo apt-get -t testing install libc6-dev`。

#### 无法解析 `custom/conf/app.ini`

如果您在启动时得到以下错误：

```
[FATAL][github.com/gogits/gogs/modules/base] conf.go:287: Cannot load config file(/Users/.../gogits/gogs/custom/conf/app.ini): could not parse line: ; App name that shows on every page title
```

这可能是您的编辑器将配置文件保存为 `UTF8 with BOM` 导致的（一般发生下 Windows 下），请修改编码为 `UTF8`。

#### 从 `v0.2.0` 升级

- 由于使用了更加安全的密码加密策略，所有该版本注册的用户都需要重置密码（URL：`/user/forget_password`）。