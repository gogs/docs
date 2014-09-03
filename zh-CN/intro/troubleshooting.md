---
name: 故障排查
sort: 2
---

# 故障排查

## Git

- 错误描述：`bash /path/to/gogs: no such file or directory`
- 可能原因：您修改了 Gogs 二进制的位置
- 解决方案：在新的 Gogs 目录下执行 `./gogs fix location <old Gogs path>`

-----

- 错误描述：`fatal: 'XX/XX.git' does not appear to be a git repository`
- 可能原因：`~/.ssh/authorized_keys` 文件中存在重复的 SSH 密钥，可能是由于您曾经或正在通过同一个系统用户使用 GitLab。
- 解决方案：删除除了属于 Gogs 自动添加以外的所有密钥。

-----

- 错误描述：`repo.NewRepoContext(fail to set git user.email):`
- 可能原因：该错误会发生在 Windows 安装 Git Bash 时未启用 `cmd` 选项。
- 解决方案：重装并启用 `cmd` 选项。

## 表单验证

- 错误描述：`Repository/User name contains illegal characters`
- 可能原因：为了防止不必要的异常，您的用户名或仓库在符合以下任意一条规则时会被认为非法： 
	- 名称为 `"raw", "install", "api", "avatar", "user", "org", "help", "stars", "issues", "pulls", "commits", "repo", "template", "admin", "new"`。
	- 名称后缀为 `".git"`。

## Cache

- 错误描述：`cache: unknown adaptername "memcache" (forgotten import?)`
- 可能原因：为了减少不必要的导入，您需要使用构建 tags 来启用某个缓存适配器。
- 解决方案：
	- 下载：`go get -tags memcache github.com/gogits.gogs`
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

- 错误描述：无法发送邮件
- 可能原因：目前 Go 语言不支持基于 SSL 的电子邮件，所以请选择一个不需要 SSL 验证的端口。
- 解决方案：如果您知道如何使用 Go 语言发送基于 SSL 的电子邮件，请联系我们！

-----

- 错误描述：Gmail 发送返回 Error 534: `Please log in via your web browser and then try again`
- 可能原因：这是因为 Google 不信任您的服务器导致的。
- 解决方案：
	- 访问 https://accounts.google.com 并登录。
	- 访问 https://accounts.google.com/DisplayUnlockCaptcha 单击 `continue`。
	- 重试发送。

## 其它

- 错误描述：`Error 1062: Duplicate entry 'Unknown-Mac' for key 'UQE_public_key_name'`
- 可能原因：这是由于遗留代码导致的，`public_key` 表之前含有唯一索引 `UQE_public_key_name`。
- 解决方案：您只需删除它即可。

-----

- 错误描述：`GLIBC_2.14 not found`
- 解决方案：尝试 `sudo apt-get -t testing install libc6-dev`。

-----

- 错误描述：`could not parse line: ; App name that shows on every page title`
- 可能原因：这可能是您的编辑器将配置文件保存为 `UTF8 with BOM` 导致的（一般发生下 Windows 下）。
- 解决方案：请修改编码为 `UTF8`。