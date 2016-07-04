---
name: 配置文件手册
---

# 配置文件手册

本手册会详尽地描述有关 Gogs 配置文件的选项，帮助您更好地理解和使用 Gogs。

请记住，任何修改都是发生在 `custom/conf/app.ini` 自定义配置文件中，该文件的具体位置与您的设置有关。

完整的默认设置可以通过 [app.ini](https://github.com/gogits/gogs/blob/master/conf/app.ini) 文件查看。如果您看到类似 `%(X)s` 字符，这是由 [ini](https://github.com/go-ini/ini/tree/v1#recursive-values) 提供的递归取值的特性。

任何带有 :exclamation: 标记的配置选项表示除非您完全了解修改后的影响，否则请保持默认值。

## 概览

- `APP_NAME`：应用名称，可以改成您的组织或公司名称
- `RUN_USER`：运行应用的用户名称，我们建议您使用 `git`，但如果您在个人计算机上运行 Gogs，请修改为您的系统用户名称。如果没有正确设置这个值，很可能导致您的应用崩溃
- `RUN_MODE`：鉴于性能和其它考虑，建议在部署环境下修改为 `prod` 模式。在您完成安装操作时，该值也会被设置为 `prod`

## Repository (`repository`)

- `ROOT`：用户仓库存储根目录，必须为绝对路径，默认为 `~/<user name>/gogs-repositories`
- `SCRIPT_TYPE`：系统脚本类型，一般情况下均为 `bash`，但有些用户反应只能使用 `sh`
- `ANSI_CHARSET`：当遇到无法识别的字符集时使用的默认字符集
- `FORCE_PRIVATE`：强制要求所有新建的仓库都是私有的
- `MAX_CREATION_LIMIT`：全局默认的每个用户可创建创建仓库上限，`-1` 表示无限制
- `PULL_REQUEST_QUEUE_LENGTH`:exclamation:：测试合并请求（Pull Request）的任务队列长度，该值越大越好

## UI (`ui`)

- `EXPLORE_PAGING_NUM`：探索页面每页显示仓库的数量
- `ISSUE_PAGING_NUM`：每页显示工单（Issue）的数量（应用到所有以列表形式显示工单的页面）
- `FEED_MAX_COMMIT_NUM`：一条最新活动中显示代码提交（Commit）的最大数量

### UI - Admin (`ui.admin`)

- `USER_PAGING_NUM`：用户管理页面每页显示记录条数
- `REPO_PAGING_NUM`：仓库管理页面每页显示记录条数
- `NOTICE_PAGING_NUM`：系统提示管理页面每页显示记录条数
- `ORG_PAGING_NUM`：组织管理页面每页显示记录条数

## Markdown (`markdown`)

- `ENABLE_HARD_LINE_BREAK`：指示是否启动硬性换行扩展

## Server (`server`)

- `PROTOCOL`：`http` 或 `https`
- `DOMAIN`：服务器域名
- `ROOT_URL`：公开的完整 URL 路径
- `HTTP_ADDR`：应用 HTTP 监听地址
- `HTTP_PORT`：应用 HTTP 监听端口号
- `DISABLE_SSH`：当 SSH 功能不可用时可以禁用
- `START_SSH_SERVER`：启用该选项来启动内置 SSH 服务器
- `SSH_PORT`：SSH 端口号，如果不为 `22` 的话可以在此修改
- `OFFLINE_MODE`：激活该选项来禁止从 CDN 获取静态资源，同时 Gravatar 服务也将被自动禁用
- `DISABLE_ROUTER_LOG`：激活该选项来禁止打印路由日志
- `CERT_FILE`：HTTPS 授权文件路径
- `KEY_FILE`：HTTPS 的密钥文件路径
- `STATIC_ROOT_PATH`：模板文件和静态文件的上级目录，默认为应用二进制所在的位置
- `ENABLE_GZIP`：激活该选项来启用应用级别 GZIP 支持
- `LANDING_PAGE`：未登录用户的默认首页，可以是 `home` 或 `explore`（探索页）

## Database (`database`)

- `DB_TYPE`：数据库类型，可以是 `mysql`、`postgres` 或 `sqlite3`
- `HOST`：数据库主机地址与端口
- `NAME`：数据库名称
- `USER`：数据库用户名
- `PASSWD`：数据库用户密码
- `SSL_MODE`：仅限 PostgreSQL 使用
- `PATH`：仅限 SQLite3 使用，数据库文件路径

## Security (`security`)

- `INSTALL_LOCK`：用于指示是否允许访问安装页面（该页面可以设置管理员帐号，因此该选项非常重要）
- `SECRET_KEY`：全局的加密密钥，**务必修改该值以确保您的服务器安全**（会在每次安装时自动生成随机字符串）
- `LOGIN_REMEMBER_DAYS`：记住登录的天数
- `COOKIE_USERNAME`：记录用户名的 Cookie 名称
- `COOKIE_REMEMBER_NAME`：记录用户自动登录信息的 Cookie 名称
- `REVERSE_PROXY_AUTHENTICATION_USER`：反向代理认证用户的 Header 字段名

## Service (`service`)

- `ACTIVE_CODE_LIVE_MINUTES`：激活码的有效期，单位为分钟
- `RESET_PASSWD_CODE_LIVE_MINUTES`：重置密码的有效期，单位为分钟
- `REGISTER_EMAIL_CONFIRM`：激活该选项来要求注册用户必须验证邮箱，要求已启用 `Mailer`
- `DISABLE_REGISTRATION`：激活该选项来禁止用户注册功能，只能由管理员创建帐号
- `SHOW_REGISTRATION_BUTTON`：用于指示是否显示注册按钮
- `REQUIRE_SIGNIN_VIEW`：激活该选项来要求用户必须登录才能浏览任何页面
- `ENABLE_CACHE_AVATAR`：激活该选项来缓存 Gravatar 的头像
- `ENABLE_NOTIFY_MAIL`：激活该选项来发送通知邮件给关注者，例如创建 issue 时，要求已启用 `Mailer`
- `ENABLE_REVERSE_PROXY_AUTHENTICATION`：激活该选项来开启反向代理用户认证，请从 https://github.com/gogits/gogs/issues/165 了解更多信息
- `ENABLE_REVERSE_PROXY_AUTO_REGISTRATION`：激活该选项来开启反向代理用户认证的自动注册功能
- `DISABLE_MINIMUM_KEY_SIZE_CHECK`：激活该选项来禁止检查响应类型的密钥最小长度
- `ENABLE_CAPTCHA`：激活该选项以在用户注册时要求输入验证码

## Webhook (`webhook`)

- `QUEUE_LENGTH`:exclamation:：发送通知的队列长度
- `DELIVER_TIMEOUT`：发送通知的超时时间，以秒为单位
- `SKIP_TLS_VERIFY`：指示是否允许向具有非信任证书的地址发送通知
- `PAGING_NUM`：Web 钩子历史页面每页显示记录条数

## Mailer (`mailer`)

- `ENABLED`：启用该选项以激活邮件服务
- `DISABLE_HELO`：禁用 HELO 操作
- `HELO_HOSTNAME`：HELO 操作的自定义主机名
- `HOST`：SMTP 主机地址与端口
- `FROM`：邮箱的来自地址，遵循 RFC 5322规范，可以是一个单纯的邮箱地址或者 "名字" \<email@example.com\> 的形式
- `USER`：邮箱用户名
- `PASSWD`：邮箱密码
- `SKIP_VERIFY`：不验证自签发证书的有效性

## Cache (`cache`)

- `ADAPTER`：缓存引擎适配器，可以为 `momery`、`redis` 或 `memcache`。如果您使用 `redis` 或 `memcache`，请确保使用 `-tags` 选项重新构建所有依赖，例如：`go build -tags='redis'`
- `INTERVAL`：仅限内存缓存使用，GC 周期，单位为秒
- `HOST`：仅限 redis 和 memcache 使用，主机地址和端口号
    - Redis：`network=tcp,addr=127.0.0.1:6379,password=macaron,db=0,pool_size=100,idle_timeout=180`
    - Memache：`127.0.0.1:9090;127.0.0.1:9091`

## Session (`session`)

- `PROVIDER`：Session 引擎提供者，可以是 `memory`、`file`、`redis` 或 `mysql`
- `PROVIDER_CONFIG`：如果提供者为 file，则为文件根目录；如果为其它提供者，则为主机地址和端口号
- `COOKIE_SECURE`：激活该选项以要求所有 session 操作均通过 HTTPS
- `GC_INTERVAL_TIME`：GC 周期，单位为秒

## Picture (`picture`)

- `GRAVATAR_SOURCE`：可以是 `gravatar`、`duoshuo` 或任何 URL，例如：`http://cn.gravatar.com/avatar/`
- `DISABLE_GRAVATAR`：激活该选项来仅使用本地头像

## Attachment (`attachment`)

- `ENABLED`：启用该选项以允许用户上传附件
- `PATH`：存放附件的路径
- `ALLOWED_TYPES`：允许上传的 MIME 类型，例如 `image/jpeg|image/png`，使用 `*/*` 允许所有类型的文件
- `MAX_SIZE`：最大允许上传的附件体积，单位为 MB，例如 `4`
- `MAX_FILES`：最大允许一次性上传的附件个数，例如 `5`

## Log (`log`)

- `ROOT_PATH`：日志文件的根目录
- `MODE`：日志记录模式，默认为 `console`。如果想要开启多模式，请使用逗号分割
- `LEVEL`：基本日志级别，默认为 `Trace`

## Cron (`cron`)

- `ENABLED`：激活该选项以允许周期性运行 Cron 任务
- `RUN_AT_START`：激活该选项以允许在启动时执行 Cron 任务

### Cron - Update Mirrors (`cron.update_mirrors`)

- `SCHEDULE`：定时更新仓库镜像的 Cron 语法，例如：`@every 1h`

### Cron - Repository Health Check (`cron.repo_health_check`)

- `SCHEDULE`：定时进行仓库健康检查的 Cron 语法，例如：`@every 24h`
- `TIMEOUT`：仓库健康检查超时的定义语法，例如：`60s`
- `ARGS`：`git fsck` 命令的参数，例如：`--unreachable --tags`

### Cron - Repository Statistics Check (`cron.check_repo_stats`)

- `RUN_AT_START`：激活该选项以在启动时执行仓库统计检查
- `SCHEDULE`：定时进行仓库统计检查的 Cron 语法，例如：`@every 24h`

## Git (`git`)

- `MAX_GIT_DIFF_LINES`: 差异对比页面单个文件显示的最大行数
- `MAX_GIT_DIFF_LINE_CHARACTERS`: 差异对比页面单行显示的最大字符数
- `MAX_GIT_DIFF_FILES`: 差异对比页面文件显示的最多个数
- `GC_ARGS`：`git gc` 命令的参数，例如：`--aggressive --auto`

## Other (`other`)

- `SHOW_FOOTER_BRANDING`：激活该选项以在页脚显示 Gogs 推广信息
- `SHOW_FOOTER_VERSION`：激活该选项以在页脚显示 Gogs 版本信息
