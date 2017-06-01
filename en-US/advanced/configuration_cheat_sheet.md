---
name: Config Cheat Sheet
---

# Configuration Cheat Sheet

This is a cheat sheet for the Gogs configuration file. It is helpful for more fully understanding how it powers Gogs.

Before getting started, make sure you know that any change to the configuration should be made in `custom/conf/app.ini` or any corresponding location.

All **default settings** can be found in [app.ini](https://github.com/gogits/gogs/blob/master/conf/app.ini). If you see anything which looks like `%(X)s`, it is a feature powered by [ini](https://github.com/go-ini/ini/#recursive-values) for reading values recursively.

### Overall (`DEFAULT`)

Name|Description
----|-----------
`APP_NAME`|Application name, can be your company or team name.
`RUN_USER`|The name of the system user that runs Gogs. The best practice is to user `git`; however, change this to whatever your username is if you run Gogs on your personal computer. Gogs may crash if this value is not set properly.
`RUN_MODE`|For performance and other purposes, change this to `prod` when deployed to a production environment. The installation process will set this to `prod` automatically.

### Server (`server`)

Name|Description
----|-----------
`PROTOCOL`|Either `http` or `https`.
`DOMAIN`|Domain name of your server.
`ROOT_URL`|Full public URL of Gogs server.
`HTTP_ADDR`|HTTP listen address.
`HTTP_PORT`|HTTP listen port.
`UNIX_SOCKET_PERMISSION`|Permission for unix socket.
`LOCAL_ROOT_URL`|Local (DMZ) URL for Gogs workers (such as SSH update) accessing web service. In most cases you do not need to change the default value. Alter it only if your SSH server node is not the same as HTTP node.
`DISABLE_SSH`|Disables SSH feature when it's not available.
`START_SSH_SERVER`|Starts built-in SSH server when enabled.
`SSH_DOMAIN`|Domain name to be exposed in SSH clone URL. The domain name that public network can access to your standalone SSH server.
`SSH_PORT`|Port number to be exposed in SSH clone URL. The port number that public network can access to your standalone SSH server, usually is the standard SSH port `22`.
`SSH_LISTEN_HOST`|Network interface builtin SSH server listens on.
`SSH_LISTEN_PORT`|Port number builtin SSH server listens on.
`SSH_ROOT_PATH`|Root path of SSH directory, default is `~/.ssh`, but you have to use `/home/git/.ssh`.
`SSH_KEY_TEST_PATH`|Directory to create temporary files when test publick key using ssh-keygen, default is system temporary directory.
`SSH_KEYGEN_PATH`|Path to ssh-keygen, default is `ssh-keygen` and let shell find out which one to call.
`MINIMUM_KEY_SIZE_CHECK`|Indicate whether to check minimum key size with corresponding type.
`OFFLINE_MODE`|Disables use of CDN for static files and Gravatar for profile pictures.
`DISABLE_ROUTER_LOG`|Mutes printing of the router log.
`CERT_FILE`|Cert file path used for HTTPS.
`KEY_FILE`|Key file path used for HTTPS.
`STATIC_ROOT_PATH`|Upper level of template and static files path, default is the path where Gogs is located.
`APP_DATA_PATH`|Default path for App data.
`ENABLE_GZIP`|Enables application-level GZIP support.
`LANDING_PAGE`|Non-logged-in users' landing page, either `home` or `explore`.

### Repository (`repository`)

Name|Description
----|-----------
`ROOT`|Root path for storing all users' repository data. It must be an absolute path. The default is `~/<username>/gogs-repositories`.
`SCRIPT_TYPE`|The script type your server supports, usually this is `bash`, but some customers report that they only have `sh`.
`ANSI_CHARSET`|The default charset for an unrecognized charset.
`FORCE_PRIVATE`|Force every new repository to be private.
`MAX_CREATION_LIMIT`|Global maximum creation limit of repositories per user, `-1` means no limit.
`PREFERRED_LICENSES`|Preferred Licenses to place at the top of the list.
`DISABLE_HTTP_GIT`|Indicates whether or not to disable Git clone through HTTP/HTTPS. When disabled, users can only perform Git operations via SSH.
`ENABLE_LOCAL_PATH_MIGRATION`|Indicates whether or not to disable migrate repository by local path. When enabled, user still needs to be a site admin or get permission from site admin in order to use this feature.

#### Repository - Editor (`repository.editor`)

Name|Description
----|-----------
`LINE_WRAP_EXTENSIONS`|List of file extensions that should have line wraps in the CodeMirror editor. Separate extensions with a comma. To line wrap files without extension, just put a comma, e.g. `.txt,`.

#### Repository - Upload (`repository.upload`)

Name|Description
----|-----------
`ENABLED`|Indicates whether or not to enable repository file upload feature.
`TEMP_PATH`|Path to temporarily store uploads. Use the default or system temporary path.
`ALLOWED_TYPES`|File types that are allowed to be uploaded (e.g. "image/jpeg\|image/png"). Leave empty means allow any file type.
`FILE_MAX_SIZE`|Maximum size of each file in MB.
`MAX_FILES`|Maximum number of files per upload.

#### Release - Attachment (`release.attachment`)

Name|Description
----|-----------
`ENABLED`|Indicates whether or not to enable release attachment feature.
`PATH`|Path to store attachments.
`ALLOWED_TYPES`|Allowed MIME types, e.g. "image/jpeg\|image/png", use `*/*` for all types.
`MAX_SIZE`|Maximum size in MB, e.g. `32`
`MAX_FILES`|Maximum number of attachments can be uploaded at once, e.g. `10`.

### Markdown (`markdown`)

Name|Description
----|-----------
`ENABLE_HARD_LINE_BREAK`|Whether or not to enable hard the line break extension.
`CUSTOM_URL_SCHEMES`|List of custom URL-Schemes that are allowed as links when rendering Markdown, for example `git` (for `git://`) and `magnet` (for `magnet://`).
`FILE_EXTENSIONS`|List of file extensions that should be rendered/edited as Markdown. Separate extensions with a comma. To render files without extension as Markdown, just put a comma.

### Smartypants (`smartypants`)

Name|Description
----|-----------
`ENABLED`|Indicates whether or not to enable Smartypants extension.

### HTTP (`http`)

Name|Description
----|-----------
`ACCESS_CONTROL_ALLOW_ORIGIN`|Value for `Access-Control-Allow-Origin` header, default is not to present.

### Database (`database`)

Name|Description
----|-----------
`DB_TYPE`|The database type you choose, either `mysql`, `postgres`, `mssql` or `sqlite3`.
`HOST`|Database host address and port.
`NAME`|Database name.
`USER`|Database username.
`PASSWD`|Database user password.
`SSL_MODE`|For PostgreSQL only.
`PATH`|For SQLite3 only, the database file path.

### Admin (`admin`)

Name|Description
----|-----------
`DISABLE_REGULAR_ORG_CREATION`|Disable regular (non-admin) users to create organizations.

### Security (`security`)

Name|Description
----|-----------
`INSTALL_LOCK`|Indicates whether to allow the open install page (setting admin account is involved, so it's a very important value).
`SECRET_KEY`|Global secret key for your server security, **you'd better change it** (will generate a random string every time you install).
`LOGIN_REMEMBER_DAYS`|Cookie lifetime, in days.
`COOKIE_USERNAME`|Name of the cookie that saves username.
`COOKIE_REMEMBER_NAME`|Name of cookie that saves auto-login information.
`REVERSE_PROXY_AUTHENTICATION_USER`|Header name for reverse proxy authentication username.

### Service (`service`)

Name|Description
----|-----------
`ACTIVE_CODE_LIVE_MINUTES`|The minutes of active code life time.
`RESET_PASSWD_CODE_LIVE_MINUTES`|The minutes of reset password code life time.
`REGISTER_EMAIL_CONFIRM`|Enable this to ask for mail confirmation of registration, requires `Mailer` to be enabled.
`DISABLE_REGISTRATION`|Disable registration, after which only admin can create accounts for users.
`SHOW_REGISTRATION_BUTTON`|Indicate whether to show registration button or not.
`REQUIRE_SIGNIN_VIEW`|Enable this to force users to log in to view any page.
`ENABLE_CACHE_AVATAR`|Enable this to cache avatar from Gravatar.
`ENABLE_NOTIFY_MAIL`|Enable this to send e-mail to watchers of repository when something happens like creating issues, requires `Mailer` to be enabled.
`ENABLE_REVERSE_PROXY_AUTHENTICATION`|Enable this to allow reverse proxy authentication, more detail|https://github.com/gogits/gogs/issues/165
`ENABLE_REVERSE_PROXY_AUTO_REGISTRATION`|Enable this to allow auto-registration for reverse authentication.
`DISABLE_MINIMUM_KEY_SIZE_CHECK`|Do not check minimum key size with corresponding type.
`ENABLE_CAPTCHA`|Enable this to use captcha validation for registration.

### Webhook (`webhook`)

Name|Description
----|-----------
`TYPES`|Types are enabled for users to use, can be `gogs`, `slack` or `discord`.
`DELIVER_TIMEOUT`|Delivery timeout in seconds for shooting webhooks.
`SKIP_TLS_VERIFY`|Indicate whether to allow insecure certification or not.
`PAGING_NUM`|Number of webhook history that are shown in one page.

### Mailer (`mailer`)

Name|Description
----|-----------
`ENABLED`|Enable this to use a mail service.
`DISABLE_HELO`|Disable HELO operation.
`HELO_HOSTNAME`|Custom hostname for HELO operation.
`HOST`|SMTP mail host address and port (example: smtp.gogs.io:587).
`FROM`|Mail from address, RFC 5322. This can be just an email address, or the `"Name" <email@example.com>` format.
`USER`|Username of mailer (usually just your e-mail address).
`PASSWD`|Password of mailer.
`SKIP_VERIFY`|Do not verify the self-signed certificates.
`USE_PLAIN_TEXT`|Indicate whether to use `text/plain` as format of content or not.

Note: Gogs supports only SMTP with STARTTLS.

### Cache (`cache`)

Name|Description
----|-----------
`ADAPTER`|Cache engine adapter, either `memory`, `redis`, or `memcache`. If you want to use `redis` or `memcache`, be sure to rebuild everything with build tags `redis` or `memcache`, for example: `go build -tags='redis'`.
`INTERVAL`|for memory cache only, GC interval in seconds.
`HOST`|For redis and memcache, the host address and port number.
-|Redis: `network=tcp,addr=127.0.0.1:6379,password=macaron,db=0,pool_size=100,idle_timeout=180`.
-|Memache: `127.0.0.1:9090;127.0.0.1:9091`

### Session (`session`)

Name|Description
----|-----------
`PROVIDER`|Session engine provider, either `memory`, `file`, or `redis`.
`PROVIDER_CONFIG`|For file, it's the root path; for others, it's the host address and port number.
`COOKIE_SECURE`|Enable this to force using HTTPS for all session access.
`GC_INTERVAL_TIME`|GC interval in seconds.

### Picture (`picture`)

Name|Description
----|-----------
`AVATAR_UPLOAD_PATH`|Path to store user uploaded avatars.
`GRAVATAR_SOURCE`|Can be `gravatar`, `duoshuo` or anything like `http://cn.gravatar.com/avatar/`.
`DISABLE_GRAVATAR`|Enable this to use local avatars only.
`ENABLE_FEDERATED_AVATAR`|Indicate whether to enable for federated avatars (see http://www.libravatar.org). This value will be forced to be false in offline mode or Gravatar is disbaled.

### Attachment (`attachment`)

Name|Description
----|-----------
`ENABLED`|Enable this to allow users upload attachments.
`PATH`|Path to store attachments.
`ALLOWED_TYPES`|Allowed MIME types, e.g. "image/jpeg\|image/png", use `*/*` for all types.
`MAX_SIZE`|Maximum size in MB, e.g. `4`
`MAX_FILES`|Maximum number of attachments can be uploaded at once, e.g. `5`.

### Time (`time`)

Name|Description
----|-----------
`FORMAT`|Specifies the format for fully outputed dates. Defaults to RFC1123. Special supported values are ANSIC, UnixDate, RubyDate, RFC822, RFC822Z, RFC850, RFC1123, RFC1123Z, RFC3339, RFC3339Nano, Kitchen, Stamp, StampMilli, StampMicro and StampNano. For more information about the format see http://golang.org/pkg/time/#pkg-constants.

### Log (`log`)

Name|Description
----|-----------
`ROOT_PATH`|Root path for log files.
`MODE`|Logging mode, default is `console`. For multiple modes, Use comma to separate multiple modes, e.g. `"console, file"`.
`LEVEL`|General log level, default is `Trace`.

#### Log - Console (`log.console`)

Name|Description
----|-----------
`LEVEL`|Console log level, leave empty to inherit.

#### Log - File (`log.file`)

Name|Description
----|-----------
`LEVEL`|File log level, leave empty to inherit.
`LOG_RORATE`|Enable this to have file rotation.
`DAILY_ROTATE`|Enable this to segment log file daily.
`MAX_SIZE_SHIFT`|Max size shift of single file for rotation, default is 28 means 1 << 28, 256MB.
`MAX_LINES`|Max line number of single file for rotation, default is `1000000`.
`MAX_DAYS`|Expired days of log file for rotation, default is to delete after `7` days.

#### Log - Slack (`log.slack`)

Name|Description
----|-----------
`LEVEL`|Slack log level, leave empty to inherit.
`URL`|Slack webhook URL.

### Cron (`cron`)

Name|Description
----|-----------
`ENABLED`|Enable this to run cron tasks periodically.
`RUN_AT_START`|Enable this to run cron tasks at start time.

#### Cron - Update Mirrors (`cron.update_mirrors`)

Name|Description
----|-----------
`SCHEDULE`|Cron syntax for scheduling update mirrors, e.g. `@every 1h`.

#### Cron - Repository Health Check (`cron.repo_health_check`)

Name|Description
----|-----------
`SCHEDULE`|Cron syntax for scheduling repository health check, e.g. `@every 24h`.
`TIMEOUT`|Time duration syntax for health check execution timeout, e.g. `60s`.
`ARGS`|Arguments for command `git fsck`, e.g. `--unreachable --tags`.

#### Cron - Repository Statistics Check (`cron.check_repo_stats`)

Name|Description
----|-----------
`RUN_AT_START`|Enable this to run repository statistics check at start time.
`SCHEDULE`|Cron syntax for scheduling repository statistics check, e.g. `@every 24h`.

#### Cron - Repository Archives Cleanup (`cron.repo_archive_cleanup`)

Name|Description
----|-----------
`RUN_AT_START`|Enable this to run repository archives cleanup at start time.
`SCHEDULE`|Cron syntax for scheduling repository statistics check, e.g. `@every 24h`.
`OLDER_THAN`|Time duration to check if archive should be cleaned, e.g. `24h`

### Git (`git`)

Name|Description
----|-----------
`DISABLE_DIFF_HIGHLIGHT`|Enable this to disable inline diff highlight.
`MAX_GIT_DIFF_LINES`|Max number of lines allowed of a single file in diff view.
`MAX_GIT_DIFF_LINE_CHARACTERS`|Max number of characters of a line allowed in diff view.
`MAX_GIT_DIFF_FILES`|Max number of files shown in diff view.
`GC_ARGS`|Arguments for command `git gc`, e.g. `--aggressive --auto`.

#### Git - Timeout (`git.timeout`)

Name|Description
----|-----------
`MIGRATE`|Repository migration timeout in seconds, default is `600`.
`MIRROR`|Repository mirror sync timeout in seconds, default is `300`.
`CLONE`|Repository clone timeout in seconds, default is `300`.
`PULL`|Repository pull timeout in seconds, default is `300`.
`GC`|Repository GC timeout in seconds, default is `60`.

### UI (`ui`)

Name|Description
----|-----------
`EXPLORE_PAGING_NUM`|Number of repositories that are shown in one explore page.
`ISSUE_PAGING_NUM`|Number of issues that are shown in one page (for all pages that list issues).
`FEED_MAX_COMMIT_NUM`|Number of maximum commits shown in one activity feed.
`THEME_COLOR_META_TAG`|Value of "theme-color" meta tag, used by Android >= 5.0. An invalid color like "none" or "disable" will have the default style, see [more info](https://developers.google.com/web/updates/2014/11/Support-for-theme-color-in-Chrome-39-for-Android).
`MAX_DISPLAY_FILE_SIZE`|Max size in bytes of files to be displayed.

#### UI - Admin (`ui.admin`)

Name|Description
----|-----------
`USER_PAGING_NUM`|Number of users that are shown in one page in admin panel.
`REPO_PAGING_NUM`|Number of repos that are shown in one page in admin panel.
`NOTICE_PAGING_NUM`|Number of notices that are shown in one page in admin panel.
`ORG_PAGING_NUM`|Number of organizations that are shown in one page in admin panel.

#### UI - User (`ui.user`)

Name|Description
----|-----------
`REPO_PAGING_NUM`|Number of repos that are showed in one page for user related pages.

### Other (`other`)

Name|Description
----|-----------
`SHOW_FOOTER_BRANDING`|Enable this to show Gogs branding in the footer.
`SHOW_FOOTER_VERSION`|Enable this to show Gogs version information in the footer.
`SHOW_FOOTER_TEMPLATE_LOAD_TIME`|Enable this to show Gogs template loading time in the footer.
