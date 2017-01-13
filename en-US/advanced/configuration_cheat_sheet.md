---
name: Config Cheat Sheet
---

# Configuration Cheat Sheet

This is a cheat sheet for the Gogs configuration file. It is helpful for more fully understanding how it powers Gogs.

Before getting started, make sure you know that any change to the configuration should be made in `custom/conf/app.ini` or any corresponding location.

All default settings can be found in [app.ini](https://github.com/gogits/gogs/blob/master/conf/app.ini). If you see anything which looks like `%(X)s`, it is a feature powered by [ini](https://github.com/go-ini/ini/#recursive-values) for reading values recursively.

Any configuration option that is marked by :exclamation: means that you should keep the default value unless you fully understand what you are doing.

## Overall

- `APP_NAME`: Application name, change to whatever you want.
- `RUN_USER`: The user to run Gogs as, we recommend it be `git`; however, change this to whatever your username is if you run Gogs on your personal computer. Gogs may crash if this value is not set properly.
- `RUN_MODE`: For performance and other purposes, change this to `prod` when deployed to a production environment. The installation process will set this to `prod` automatically.

## Repository (`repository`)

- `ROOT`: Root path for storing all users' repository data. It must be an absolute path. The default is `~/<username>/gogs-repositories`.
- `SCRIPT_TYPE`: The script type your server supports, usually this is `bash`, but some customers report that they only have `sh`.
- `ANSI_CHARSET`: The default charset for an unrecognized charset.
- `FORCE_PRIVATE`: Force every new repository to be private.
- `MAX_CREATION_LIMIT`: Global maximum creation limit of repositories per user, `-1` means no limit.
- `PULL_REQUEST_QUEUE_LENGTH`:exclamation:: Length of pull request patch test queue, make it as large as possible.

## UI (`ui`)

- `EXPLORE_PAGING_NUM`: Number of repositories that are shown in one explore page.
- `ISSUE_PAGING_NUM`: Number of issues that are shown in one page (for all pages that list issues).
- `FEED_MAX_COMMIT_NUM`: Number of maximum commits shown in one activity feed.

### UI - Admin (`ui.admin`)

- `USER_PAGING_NUM`: Number of users that are shown in one page.
- `REPO_PAGING_NUM`: Number of repos that are shown in one page.
- `NOTICE_PAGING_NUM`: Number of notices that are shown in one page.
- `ORG_PAGING_NUM`: Number of organizations that are shown in one page.

## Markdown (`markdown`)

- `ENABLE_HARD_LINE_BREAK`: Whether or not to enable hard the line break extension.

## Server (`server`)

- `PROTOCOL`: Either `http` or `https`.
- `DOMAIN`: Domain name of your server.
- `ROOT_URL`: Full public URL of Gogs server.
- `HTTP_ADDR`: HTTP listen address.
- `HTTP_PORT`: HTTP listen port.
- `DISABLE_SSH`: Disables SSH feature when it's not available.
- `START_SSH_SERVER`: Starts built-in SSH server when enabled.
- `SSH_PORT`: The SSH port, in case yours is not `22`.
- `OFFLINE_MODE`: Disables use of CDN for static files and Gravatar for profile pictures.
- `DISABLE_ROUTER_LOG`: Mutes printing of the router log.
- `CERT_FILE`: Cert file path used for HTTPS.
- `KEY_FILE`: Key file path used for HTTPS.
- `STATIC_ROOT_PATH`: Upper level of template and static files path, default is the path where Gogs is located.
- `ENABLE_GZIP`: Enables application-level GZIP support.
- `LANDING_PAGE`: Non-logged-in users' landing page, either `home` or `explore`.

## Database (`database`)

- `DB_TYPE`: The database type you choose, either `mysql`, `postgres` or `sqlite3`.
- `HOST`: Database host address and port.
- `NAME`: Database name.
- `USER`: Database username.
- `PASSWD`: Database user password.
- `SSL_MODE`: For PostgreSQL only.
- `PATH`: For SQLite3 only, the database file path.

## Security (`security`)

- `INSTALL_LOCK`: Indicates whether to allow the open install page (setting admin account is involved, so it's a very important value).
- `SECRET_KEY`: Global secret key for your server security, **you'd better change it** (will generate a random string every time you install).
- `LOGIN_REMEMBER_DAYS`: Cookie lifetime, in days.
- `COOKIE_USERNAME`: Name of the cookie that saves username.
- `COOKIE_REMEMBER_NAME`: Name of cookie that saves auto-login information.
- `REVERSE_PROXY_AUTHENTICATION_USER`: Header name for reverse proxy authentication username.

## Service (`service`)

- `ACTIVE_CODE_LIVE_MINUTES`: The minutes of active code life time.
- `RESET_PASSWD_CODE_LIVE_MINUTES`: The minutes of reset password code life time.
- `REGISTER_EMAIL_CONFIRM`: Enable this to ask for mail confirmation of registration, requires `Mailer` to be enabled.
- `DISABLE_REGISTRATION`: Disable registration, after which only admin can create accounts for users.
- `SHOW_REGISTRATION_BUTTON`: Indicate whether to show registration button or not.
- `REQUIRE_SIGNIN_VIEW`: Enable this to force users to log in to view any page.
- `ENABLE_CACHE_AVATAR`: Enable this to cache avatar from Gravatar.
- `ENABLE_NOTIFY_MAIL`: Enable this to send e-mail to watchers of repository when something happens like creating issues, requires `Mailer` to be enabled.
- `ENABLE_REVERSE_PROXY_AUTHENTICATION`: Enable this to allow reverse proxy authentication, more detail: https://github.com/gogits/gogs/issues/165
- `ENABLE_REVERSE_PROXY_AUTO_REGISTRATION`: Enable this to allow auto-registration for reverse authentication.
- `DISABLE_MINIMUM_KEY_SIZE_CHECK`: Do not check minimum key size with corresponding type.
- `ENABLE_CAPTCHA`: Enable this to use captcha validation for registration.

## Webhook (`webhook`)

- `QUEUE_LENGTH`:exclamation:: Hook task queue length.
- `DELIVER_TIMEOUT`: Delivery timeout in seconds for shooting webhooks.
- `SKIP_TLS_VERIFY`: Indicate whether to allow insecure certification or not.
- `PAGING_NUM`: Number of webhook history that are shown in one page.

## Mailer (`mailer`)

- `ENABLED`: Enable this to use a mail service.
- `DISABLE_HELO`: Disable HELO operation.
- `HELO_HOSTNAME`: Custom hostname for HELO operation.
- `HOST`: SMTP mail host address and port (example: smtp.gogs.io:587).
- `FROM`: Mail from address, RFC 5322. This can be just an email address, or the "Name" \<email@example.com\> format.
- `USER`: Username of mailer (usually just your e-mail address).
- `PASSWD`: Password of mailer.
- `SKIP_VERIFY`: Do not verify the self-signed certificates.

Note: Actually, Gogs supports only SMTP with STARTTLS.

## Cache (`cache`)

- `ADAPTER`: Cache engine adapter, either `memory`, `redis`, or `memcache`. If you want to use `redis` or `memcache`, be sure to rebuild everything with build tags `redis` or `memcache`: `go build -tags='redis'`.
- `INTERVAL`: for memory cache only, GC interval in seconds.
- `HOST`: For redis and memcache, the host address and port number.
    - Redis: `network=tcp,addr=127.0.0.1:6379,password=macaron,db=0,pool_size=100,idle_timeout=180`
    - Memache: `127.0.0.1:9090;127.0.0.1:9091`

## Session (`session`)

- `PROVIDER`: Session engine provider, either `memory`, `file`, `redis`, or `mysql`.
- `PROVIDER_CONFIG`: For file, it's the root path; for others, it's the host address and port number.
- `COOKIE_SECURE`: Enable this to force using HTTPS for all session access.
- `GC_INTERVAL_TIME`: GC interval in seconds.

## Picture (`picture`)

- `GRAVATAR_SOURCE`: Can be `gravatar`, `duoshuo` or anything like `http://cn.gravatar.com/avatar/`.
- `DISABLE_GRAVATAR`: Enable this to use local avatars only.
- `ENABLE_FEDERATED_AVATAR`: Enable support for federated avatars (see http://www.libravatar.org)

## Attachment (`attachment`)

- `ENABLED`: Enable this to allow users upload attachments.
- `PATH`: Path to store attachments.
- `ALLOWED_TYPES`: Allowed MIME types, e.g. `image/jpeg|image/png`, use `*/*` for all types.
- `MAX_SIZE`: Maximum size in MB, e.g. `4`
- `MAX_FILES`: Maximum number of attachments can be uploaded at once, e.g. `5`.

## Log (`log`)

- `ROOT_PATH`: Root path for log files.
- `MODE`: Logging mode, default is `console`. For multiple modes, use comma to separate it.
- `LEVEL`: General log level, default is `Trace`.

## Cron (`cron`)

- `ENABLED`: Enable this to run cron tasks periodically.
- `RUN_AT_START`: Enable this to run cron tasks at start time.

### Cron - Update Mirrors (`cron.update_mirrors`)

- `SCHEDULE`: Cron syntax for scheduling update mirrors, e.g. `@every 1h`.

### Cron - Repository Health Check (`cron.repo_health_check`)

- `SCHEDULE`: Cron syntax for scheduling repository health check, e.g. `@every 24h`.
- `TIMEOUT`: Time duration syntax for health check execution timeout, e.g. `60s`.
- `ARGS`: Arguments for command `git fsck`, e.g. `--unreachable --tags`.

### Cron - Repository Statistics Check (`cron.check_repo_stats`)

- `RUN_AT_START`: Enable this to run repository statistics check at start time.
- `SCHEDULE`: Cron syntax for scheduling repository statistics check, e.g. `@every 24h`.

## Git (`git`)

- `MAX_GIT_DIFF_LINES`: Max number of lines allowed of a single file in diff view.
- `MAX_GIT_DIFF_LINE_CHARACTERS`: Max number of characters of a line allowed in diff view.
- `MAX_GIT_DIFF_FILES`: Max number of files shown in diff view.
- `GC_ARGS`: Arguments for command `git gc`, e.g. `--aggressive --auto`.

## Other (`other`)

- `SHOW_FOOTER_BRANDING`: Enable this to show Gogs branding in the footer.
- `SHOW_FOOTER_VERSION`: Enable this to show Gogs version information in the footer.
- `SHOW_FOOTER_TEMPLATE_LOAD_TIME`: Enable this to show Gogs template loading time in the footer.
