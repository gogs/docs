---
name: 故障排查
---

# 故障排查

## 安装

- 错误描述：`../gosrc/src/github.com/gogits/gogs/cmd/cert.go:79: undefined: elliptic.P224`
- 可能原因：Go 语言的 RHEL/CentOS 官方发行版中因专利问题移除了相关加密算法的代码
- 解决方案：从 [golang.org/dl](http://golang.org/dl) 下载安装 Go 语言

## SSH

- 错误描述：SSH 链接挂起 60 秒
- 可能原因：Gogs 会在每次 SSH Push 完成之后请求自身的 Web 服务，您的防火墙或服务器提供商未允许该操作

## Git

- 错误描述：`bash /path/to/gogs: no such file or directory`
- 可能原因：您修改了 Gogs 二进制的位置
- 解决方案：进入 `admin` 面板然后执行 `重新生成 '.ssh/authorized_keys' 文件` 和 `重新生成所有仓库的 Update 钩子` 操作

-----

- 错误描述：
	- `fatal: 'XX/XX.git' does not appear to be a git repository`
	- 推送代码提交后依旧显示为空仓库
- 可能原因：`~/.ssh/authorized_keys` 文件中存在重复的 SSH 密钥，可能是由于您曾经或正在通过同一个系统用户使用 GitLab。
- 解决方案：删除除了属于 Gogs 自动添加以外的所有密钥。

-----

- 错误描述：`repo.NewRepoContext(fail to set git user.email):`
- 可能原因：该错误会发生在 Windows 安装 Git Bash 时未启用 `cmd` 选项。
- 解决方案：重装并启用 `cmd` 选项。

## 表单验证

- 错误描述：`Repository/User name contains illegal characters`
- 可能原因：为了防止不必要的异常，您的用户名或仓库在符合以下任意一条规则时会被认为非法：
	- 名称为 `"debug", "raw", "install", "api", "avatar", "user", "org", "help", "stars", "issues", "pulls", "commits", "repo", "template", "admin", "new"`。
	- 名称后缀为 `".git", ".keys"`。

## Cache

- 错误描述：`cache: unknown adaptername "memcache" (forgotten import?)`
- 可能原因：为了减少不必要的导入，您需要使用构建 tags 来启用某个缓存适配器。
- 解决方案：
	- 下载：`go get -tags memcache github.com/gogits/gogs`
	- 构建：`go build -tags memcache`
	- 如果要启用 `redis` 也是一样的步骤。

## MySQL

- 错误描述：`Error 1071: Specified key was too long; max key length is 1000 bytes`
- 可能原因：这是由于数据库引擎为 MyISAM 导致的。
- 解决方案：在使用 `config/mysql.sql` 创建完数据库后，进入数据库然后执行：

	```sql
	use gogs;
	set global storage_engine=INNODB;
	```

最后，访问 [http://localhost:3000/install](http://localhost:3000/install) 即可（感谢 [@linc01n](https://github.com/linc01n)）。

-----

- 错误描述：`Database setting is not correct: This server only supports the insecure old password authentication. If you still want to use it, please add 'allowOldPasswords=1' to your DSN. See also https://github.com/go-sql-driver/mysql/wiki/old_passwords`
- 可能原因：只更新了 @localhost 的密码，但 @% 用户依旧使用旧密码
- 解决方案：[GitHub 讨论](https://github.com/gogits/gogs/issues/385#issuecomment-54357073)

## 邮件服务

- 错误描述：Gmail 发送返回 Error 534: `Please log in via your web browser and then try again`
- 可能原因：这是因为 Google 不信任您的服务器导致的。
- 解决方案：
	- 访问 https://accounts.google.com 并登录。
	- 访问 https://accounts.google.com/DisplayUnlockCaptcha 单击 `continue`。
	- 重试发送。

## Windows

- 错误描述：

```
2014/09/18 15:04:40 [repo.go:115 CreatePost()] [E] CreatePost: initRepository: initRepository(git clone): cygwin warning:
MS-DOS style path detected: C:\Users\user\gogs-repositories\unos\test3.git/.git
Preferred POSIX equivalent is: /cygdrive/c/Users/user/gogs-repositories/unos/test3.git/.git
CYGWIN environment variable option "nodosfilewarning" turns off this warning.
Consult the user's guide for more details about POSIX paths:
http://cygwin.com/cygwin-ug-net/using.html#using-pathnames
Cloning into 'C:\Users\user\AppData\Local\Temp\484264900'...
fatal: '/cygdrive/d/svnroot/research/gogs/C:\Users\user\gogs-repositories\unos\test3.git' does not appear to be a git repository
fatal: Could not read from remote repository.
```

- 可能原因：您在系统中安装了另一种命令行工具，并且与系统默认的 CMD 有不同路径风格。
- 解决方案：请您尝试用默认的 CMD 启动 Gogs。

-----

- 错误描述：`Resource interpreted as Stylesheet but transferred with MIME type application/x-css`
- 可能原因：Windows 注册表中错误的值
- 解决方案：在注册表中找到 `HKEY_CLASSES_ROOT` 下的 `.css`，并将其 `Content Type` 的值修改为 `text/css`。

## 其它

- 错误描述：页面响应非常慢，但是显示在页面底部的时间正常（低于 100 毫秒）。
- 可能原因：这可能是由于 Nginx 尝试通过 IPv6 的方式解析 IPv4 的地址。
- 解决方案：显式的使用 `127.0.0.1` 作为主机名而不是 `localhost`。

-----

- 错误描述：`Error 1062: Duplicate entry 'Unknown-Mac' for key 'UQE_public_key_name'`
- 可能原因：这是由于遗留代码导致的，`public_key` 表之前含有唯一索引 `UQE_public_key_name`。
- 解决方案：您只需删除它即可。

-----

- 错误描述：`GLIBC_2.14 not found`
- 解决方案：尝试 `sudo apt-get -t testing install libc6-dev`。

-----

- 错误描述：`[Macaron] PANIC: session(start): mkdir data: permission denied`
- 可能原因：Gogs 会在程序所在目录创建 `data` 子目录。
- 解决方案：确保 Gogs 具有在相同目录创建子目录的权限。
