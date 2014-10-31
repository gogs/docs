---
name: 配置文件手册
sort: 1
---

# 配置文件手册

本手册会详尽地描述有关 Gogs 配置文件的选项，帮助您更好地理解和使用 Gogs。

请记住，任何修改都是发生在 `custom/conf/app.ini` 自定义配置文件中，而非默认的 `conf/app.ini` 配置文件。

如果您看到类似 `%(X)s` 字符，这是由 [goconfig](https://github.com/Unknwon/goconfig) 提供的递归取值的特性。

## 概览

- `APP_NAME`：应用名称，可以改成您的组织或公司名称
- `RUN_USER`：运行应用的用户名称，我们建议您使用 `git`，但如果您在个人计算机上运行 Gogs，请修改为您的系统用户名称。如果没有正确设置这个值，很可能导致您的应用崩溃
- `RUN_MODE`：请在部署环境下修改为 `prod` 模式

## Repository

- `ROOT`：用户仓库存储根目录，必须为绝对路径，默认为 `~/<user name>/gogs-repositories`
- `SCRIPT_TYPE`：系统脚本类型，一般情况下均为 `bash`，但有些用户反应只能使用 `sh`

## Server

- `PROTOCOL`：`http` 或 `https`
- `DOMAIN`：服务器域名
- `ROOT_URL`：应用的完整 URL 路径
- `HTTP_ADDR`：应用 HTTP 监听地址
- `HTTP_PORT`：应用 HTTP 监听端口号
- `SSH_PORT`：SSH 端口号，如果不为 `22` 的话可以在此修改
- `OFFLINE_MODE`：激活该选项来禁止从 CDN 获取静态资源
- `DISABLE_ROUTER_LOG`：激活该选项来禁止打印路由日志
- `CERT_FILE`：HTTPS 授权文件路径
- `KEY_FILE`：HTTPS 的密钥文件路径
- `STATIC_ROOT_PATH`：模板文件和静态文件的上级目录，默认为应用的执行路径
- `ENABLE_GZIP`：激活该选项来启用应用级别 GZIP 支持

## Database

- `DB_TYPE`：数据库类型，可以是 `mysql`、`postgres` 或 `sqlite3`
- `HOST`：数据库主机地址与端口
- `NAME`：数据库名称
- `USER`：数据库用户名
- `PASSWD`：数据库用户密码
- `SSL_MODE`：仅限 PostgreSQL 使用
- `PATH`：仅限 SQLite3 使用，数据库文件路径

## Security

- `INSTALL_LOCK`：用于指示是否允许访问安装页面（该页面可以设置管理员帐号，因此该选项非常重要）
- `SECRET_KEY`：全局的加密密钥，**务必修改该值以确保您的服务器安全**（会在每次安装时自动生成随机字符串）
- `LOGIN_REMEMBER_DAYS`：记住登录的天数
- `COOKIE_USERNAME`：记录用户名的 Cookie 名称
- `COOKIE_REMEMBER_NAME`：记录用户自动登录信息的 Cookie 名称
- `REVERSE_PROXY_AUTHENTICATION_USER`：反向代理认证用户的 Header 字段名

## Service

- `ACTIVE_CODE_LIVE_MINUTES`：激活码的有效期，单位为分钟
- `RESET_PASSWD_CODE_LIVE_MINUTES`：重置密码的有效期，单位为分钟
- `REGISTER_EMAIL_CONFIRM`：激活该选项来要求注册用户必须验证邮箱，要求已启用 `Mailer`
- `DISABLE_REGISTRATION`：激活该选项来禁止用户注册功能，只能由管理员创建帐号
- `REQUIRE_SIGNIN_VIEW`：激活该选项来要求用户必须登录才能浏览任何页面
- `ENABLE_CACHE_AVATAR`：激活该选项来缓存 Gravatar 的头像
- `ENABLE_NOTIFY_MAIL`：激活该选项来发送通知邮件给关注者，例如创建 issue 时，要求已启用 `Mailer`
- `ENABLE_REVERSE_PROXY_AUTHENTICATION`：激活该选项来开启反向代理用户认证，请从 https://github.com/gogits/gogs/issues/165 了解更多信息

## Webhook

- `TASK_INTERVAL`：发送通知的时间周期，以分钟为单位
- `DELIVER_TIMEOUT`：发送通知的超时时间，以秒为单位

## Mailer

- `ENABLED`：用于指示是否激活邮件服务
- `HOST`：SMTP 主机地址与端口
- `USER`：邮箱用户名
- `PASSWD`：邮箱密码

## OAuth

- `ENABLED`：OAuth 服务的基本开关

## Cache

- `ADAPTER`：缓存引擎适配器，可以为 `momery`、`redis` 或 `memcache`。如果您使用 `redis` 或 `memcache`，请确保使用 `-tags` 选项重新构建所有依赖，例如：`go build -tags='redis'`
- `INTERVAL`：仅限内存缓存使用，GC 周期，单位为秒
- `HOST`：仅限 redis 和 memcache 使用，主机地址和端口号

## Session

- `PROVIDER`：Session 引擎提供者，可以是 `memory`、`file`、`redis` 或 `mysql`
- `PROVIDER_CONFIG`：如果提供者为 file，则为文件根目录；如果为其它提供者，则为主机地址和端口号
- `COOKIE_SECURE`：激活该选项以要求所有 session 操作均通过 HTTPS
- `GC_INTERVAL_TIME`：GC 周期，单位为秒

## Log

- `ROOT_PATH`：日志文件的根目录
- `MODE`：日志记录模式，默认为 `console`。如果想要开启多模式，请使用逗号分割
- `LEVEL`：基本日志级别，默认为 `Trace`

### log.console

- `LEVEL`：console 模式的日志级别，如果该值为空，则使用基本日志级别

### log.file

- `LEVEL`：file 模式的日志级别，如果该值为空，则使用基本日志级别

### log.conn

- `LEVEL`：conn 模式的日志级别，如果该值为空，则使用基本日志级别

### log.smtp

- `LEVEL`：smtp 模式的日志级别，如果该值为空，则使用基本日志级别

## Git

- `MAX_GITDIFF_LINES`：对比页面显示的最大行数