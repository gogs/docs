---
name: Config Cheat Sheet
sort: 1
---

# Configuration Cheat Sheet

This is a cheat sheet for Gogs configuration file, it helps some if you want to fully understand how it powers Gogs.

Before we get started, make sure you know any change of configuration should be made in `custom/conf/app.ini` or any corresponding location.

All default settings can be found on [app.ini](https://github.com/gogits/gogs/blob/master/conf/app.ini). If you see anything like `%(X)s`, it's the feature powered by [ini](https://github.com/go-ini/ini/tree/v1#recursive-values) for reading value recursively.

## Overall

- `APP_NAME`: Application name, change to whatever you want.
- `RUN_USER`: The system user requires to run, we recommend to be `git`; however, change to whatever your user name is if you run Gogs in your personal computer. Server may crash due to not set this value properly.
- `RUN_MODE`: For performance and other purpose, change this to `prod` when deploy to production environment. Installation process will set this to `prod` automatically.

## Repository

- `ROOT`: Root path for storing all users' repositoriy data, it has to be absolute path, default is `~/<user name>/gogs-repositories`.
- `SCRIPT_TYPE`: The script type your server supports, usually is `bash`, but some customers report that they only have `sh`.

## Server

- `PROTOCOL`: Either `http` or `https`.
- `DOMAIN`: Domain name of your server.
- `ROOT_URL`: Full URL of Gogs server in public domain.
- `HTTP_ADDR`: HTTP listen address.
- `HTTP_PORT`: HTTP listen port.
- `DISABLE_SSH`: Disable SSH feature when it's not available.
- `SSH_PORT`: The SSH port, in case yours is not `22`.
- `OFFLINE_MODE`: Enable this to not use CDN for static files, also Gravatar will be disabled automatically.
- `DISABLE_ROUTER_LOG`: Enable this to not print router log.
- `CERT_FILE`: Cert file path used for HTTPS.
- `KEY_FILE`: Key file path used for HTTPS.
- `STATIC_ROOT_PATH`: Upper level of template and static files path, default is the path where Gogs is located.
- `ENABLE_GZIP`: Enable this to have application level GZIP support.
- `LANDING_PAGE`: Non-logged users' landing page, either `home` or `explore`.

## Database

- `DB_TYPE`: The database type you choose, either `mysql`, `postgres` or `sqlite3`.
- `HOST`: Database host address and port.
- `NAME`: Database name.
- `USER`: Database user name.
- `PASSWD`: Database user password.
- `SSL_MODE`: For PostgreSQL only.
- `PATH`: For SQLite3 only, the database file path.

## Security

- `INSTALL_LOCK`: To indicate whether allow open install page(setting admin account involved so it's a very important value).
- `SECRET_KEY`: Global secret key for your server security, **you'd better change it**(will generate a random string every time you install).
- `LOGIN_REMEMBER_DAYS`: The days of cookies life time.
- `COOKIE_USERNAME`: Cookie name to save username.
- `COOKIE_REMEMBER_NAME`: Cookie name to save auto-login information.
- `REVERSE_PROXY_AUTHENTICATION_USER`: Header name for reverse proxy authentication username.

## Service

- `ACTIVE_CODE_LIVE_MINUTES`: The minutes of active code life time.
- `RESET_PASSWD_CODE_LIVE_MINUTES`: The minutes of reset password code life time.
- `REGISTER_EMAIL_CONFIRM`: Enable this to ask for mail confirmation of registration, requires enable `Mailer`.
- `DISABLE_REGISTRATION`: Disable registration, which only admin can create accounts for users.
- `SHOW_REGISTRATION_BUTTON`: Indicate whether to show registration button or not.
- `REQUIRE_SIGNIN_VIEW`: Enable this to force users to log in to view any page.
- `ENABLE_CACHE_AVATAR`: Enable this to cache avatar from Gravatar.
- `ENABLE_NOTIFY_MAIL`: Enable this to send e-mail to watchers of repository when something happens like create issue, requires enable `Mailer`.
- `ENABLE_REVERSE_PROXY_AUTHENTICATION`: Enable this to allow reverse proxy authentication, more detail: https://github.com/gogits/gogs/issues/165
- `ENABLE_REVERSE_PROXY_AUTO_REGISTRATION`: Enable this to allow auto-registration for reverse authentication.
- `DISABLE_MINIMUM_KEY_SIZE_CHECK`: Do not check minimum key size with corresponding type.

## Webhook

- `QUEUE_LENGTH`: Hook task queue length.
- `DELIVER_TIMEOUT`: Delivery timeout in seconds for shooting webhooks.
- `SKIP_TLS_VERIFY`: Indicate whether allow insecure certification or not.

## Mailer

- `ENABLED`: Enable this to use mail service of any.
- `DISABLE_HELO`: Disable HELO operation.
- `HELO_HOSTNAME`: Custom hostname for HELO operation.
- `HOST`: SMTP mail host address.
- `FROM`: Mail from address, RFC 5322. This can be just an email address, or the "Name" <email@example.com> format.
- `USER`: User name of system mailer(usually just your e-mail address).
- `PASSWD`: Password of you mailer.
- `SKIP_VERIFY`: Not verify the self-signed certificates.

## OAuth

- `ENABLED`: General switch for OAuth, default value is "false"

## Cache

- `ADAPTER`: Cache engine adapter, either `memory`, `redis`, or `memcache`. If you want to use `redis` or `memcache`, be sure to rebuild everything with build tags `redis` or `memcache`: `go build -tags='redis'`.
- `INTERVAL`: for memory cache only, GC interval in seconds.
- `HOST`: For redis and memcache, the host address and port number.

## Session

- `PROVIDER`: Session engine provider, either `memory`, `file`, `redis`, or `mysql`.
- `PROVIDER_CONFIG`: For file, it's the root path; for others, it's the host address and port number.
- `COOKIE_SECURE`: Enable this to force using HTTPS for all session access.
- `GC_INTERVAL_TIME`: GC interval in seconds.

## Picture

- `GRAVATAR_SOURCE`: Can be `gravatar`, `duoshuo` or anything like `http://cn.gravatar.com/avatar/`.
- `DISABLE_GRAVATAR`: Enable this to use local avatar only.

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

## Git

- `MAX_GITDIFF_LINES`: Maxium show lines in diff page.
