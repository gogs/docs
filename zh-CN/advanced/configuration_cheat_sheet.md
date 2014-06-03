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
- `APP_LOGO`：相对于 `public` 目录的 LOGO 图片路径
- `RUN_USER`：运行应用的用户名称，我们建议您使用 `git`，但如果您在个人计算机上运行 Gogs，请修改为您的系统用户名称。如果没有正确设置这个值，很可能导致您的应用崩溃。
- `RUN_MODE`：请在部署环境下修改为 `prod` 模式

## Repository

- `ROOT`: Root path of repositories that will be stored for all users, default is `~/<user name>/gogs-repositories`.
- `SCRIPT_TYPE`: The script type your server supports, usually is `bash`, but some customers report that they only have `sh`.

## Server

- `PROTOCOL`: Either `http` or `https`.
- `DOMAIN`: Domain name of your server.
- `ROOT_URL`: Full URL of Gogs server in public domain.
- `HTTP_PORT`: HTTP port you want Gogs server to listen.
- `SSH_PORT`: The SSH port, in case yours is not `22`.
- `OFFLINE_MODE`: Enable this to not use CDN for static files.
- `DISABLE_ROUTER_LOG`: Enable this to not print router log.
- `CERT_FILE`: Cert file path of HTTPS.
- `KEY_FILE`: Key file path of HTTPS.
- `STATIC_ROOT_PATH`: Upper level of template and static file path, default is the path where Gogs is executed.

## Database

- `DB_TYPE`: The database type you choose.
- `HOST`: Database host address and port.
- `NAME`: Database name for Gogs.
- `USER`: Database user name.
- `PASSWD`: Database password.
- `SSL_MODE`: For PostgreSQL only.
- `PATH`: For SQLite3 only, the database file path.

## Security

- `INSTALL_LOCK`: To indicate whether allow open install page(setting admin account involved so it's a very important value).
- `SECRET_KEY`: Global secret key for your server security, you'd better change it.
- `LOGIN_REMEMBER_DAYS`: The days of cookies life time.

## Service

- `ACTIVE_CODE_LIVE_MINUTES`: The minutes of active code life time.
- `RESET_PASSWD_CODE_LIVE_MINUTES`: The minutes of reset password code life time.
- `REGISTER_EMAIL_CONFIRM`: Enable this to ask for mail confirmation of registration, requires enable `Mailer`.
- `DISENABLE_REGISTERATION`: Disable registration, which only admin can create accounts for users.
- `REQUIRE_SIGNIN_VIEW`: Enable this to force users to log in to view any page.
- `ENABLE_CACHE_AVATAR`: Enable this to cache avatar from Gravatar.
- `ENABLE_NOTIFY_MAIL`: This indicates whether send e-mail to watchers of repository when something happens like create issue, requires enable `Mailer`.

## Mailer

- `ENABLED`: To indicate whether enable mail service of any.
- `HOST`: SMTP mail host address.
- `USER`: User name of system mailer(usually just your e-mail address).
- `PASSWD`: Password of you mailer.

## OAuth

- `ENABLED`: General switch for oAuth, default value is "false"

## Cache

- `ADAPTER`: Cache engine adapter, either `momery`, `redis`, or `memcache`. If you want to use `redis` or `memcache`, be sure to rebuild everything with build tags `redis` or `memcahce`: `go build -tags='redis'`.
- `INTERVAL`: for memory cache only, GC interval in seconds.
- `HOST`: For redis and memcache, the host address and port number.

## Session

- `PROVIDER`: Session engine provider, either `memory`, `file`, `redis`, or `mysql`. 
- `PROVIDER_CONFIG`: For file, it's the root path; for others, it's the host address and port number.
- `COOKIE_SECURE`: Enable this to force using HTTPS for all session access.
- `GC_INTERVAL_TIME`: GC interval in seconds.

## Log

- `ROOT_PATH`: Root path for log files.
- `MODE`: Logging mode, default is `console`. For multiple modes, use comma to separate it.
- `LEVEL`: General log level, default is `Trace`.

### log.console

- `LEVEL`: Log level for console output. When no value is set, it is general log level.

### log.file

- `LEVEL`: Log level for file output. When no value is set, it is general log level.

### log.conn

- `LEVEL`: Log level for connection output. When no value is set, it is general log level.

### log.smtp

- `LEVEL`: Log level for smtp output. When no value is set, it is general log level.
