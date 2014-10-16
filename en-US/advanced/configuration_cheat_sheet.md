---
name: Config Cheat Sheet
sort: 1
---

# Configuration Cheat Sheet

This is a cheat sheet for Gogs configuration file, it helps some if you want to fully understand how it powers Gogs.

Before we get started, make sure you know any change of configuration should be made in `custom/conf/app.ini` rather than `conf/app.ini`.

If you see anything like `%(X)s`, it's the feature powered by [goconfig](https://github.com/Unknwon/goconfig) for reading value recursively.

## Overall

- `APP_NAME`: Application name, change to whatever you want.
- `RUN_USER`: The system user requires to run, we recommend to be `git`; however, change to whatever your user name is if you run Gogs in your personal computer. Server may crash due to not set this value properly.
- `RUN_MODE`: For performance and other purpose, change this to `prod` when deploy to production environment.

## Repository

- `ROOT`: Root path of repositories that will be stored for all users, it has to be absolute path, default is `~/<user name>/gogs-repositories`.
- `SCRIPT_TYPE`: The script type your server supports, usually is `bash`, but some customers report that they only have `sh`.

## Server

- `PROTOCOL`: Either `http` or `https`.
- `DOMAIN`: Domain name of your server.
- `ROOT_URL`: Full URL of Gogs server in public domain.
- `HTTP_ADDR`: Listen HTTP address.
- `HTTP_PORT`: HTTP port you want Gogs server to listen.
- `SSH_PORT`: The SSH port, in case yours is not `22`.
- `OFFLINE_MODE`: Enable this to not use CDN for static files.
- `DISABLE_ROUTER_LOG`: Enable this to not print router log.
- `CERT_FILE`: Cert file path of HTTPS.
- `KEY_FILE`: Key file path of HTTPS.
- `STATIC_ROOT_PATH`: Upper level of template and static file path, default is the path where Gogs is executed.
- `ENABLE_GZIP`: Enable this to have application level GZIP support.

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
- `DISABLE_REGISTRATION`: Disable registration, which only admin can create accounts for users.
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

- `ADAPTER`: Cache engine adapter, either `memery`, `redis`, or `memcache`. If you want to use `redis` or `memcache`, be sure to rebuild everything with build tags `redis` or `memcache`: `go build -tags='redis'`.
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
