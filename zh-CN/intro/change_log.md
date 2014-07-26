---
name: 变更日志
sort: 1
---

# 变更日志

### V0.5.0(2014-8-12)

#### Bug 修复

- 浏览由 Gogs 创建的 release 时发生 panic [#197](https://github.com/gogits/gogs/issues/197)
- 编辑 issue 或评论时修改里程碑或标签会导致文本丢失 [#216](https://github.com/gogits/gogs/issues/216)
- 通过 SSH 推送的代码无法触发 Web 钩子 [#242](https://github.com/gogits/gogs/issues/242)
- 无法在 Windows 下获取静态文件 [#271](https://github.com/gogits/gogs/issues/271)
- Dashboard 的 issue 链接显示不完整 [#273](https://github.com/gogits/gogs/issues/273)
- 协作者能够修改项目设置
- 非仓库拥有者或协作者也可修改 issue 标签 [#288](https://github.com/gogits/gogs/issues/288)
- 关闭/开启 issue 时里程碑的统计数据未更新

#### 功能改进

- 增加 `webhook` 配置分区来自定义 Web 钩子 **任务检查周期** 和 **发送超时**
- 增加仓库 TAR.GZ 格式打包下载按钮
- 当不同 release 具有相同数量的 commit 时，使用创建时间排序 [#199](https://github.com/gogits/gogs/issues/199)
- 在应用启动时检查 Git 版本
- 增加更多类型的 SSH 密钥类型验证支持 [#293](https://github.com/gogits/gogs/pull/293)
- 仓库描述的链接可点击 [#300](https://github.com/gogits/gogs/pull/300)
- 允许使用 `/:username` 作为用户主页路由

#### 新增特性

- 增加命令 `gogs fix location <old path>` 用于处理 Gogs 应用位置改变
- 支持编辑 release 以及保存为草稿
- 增加 Cron 任务和运行进程监控面板
- 增加记录日志到数据库选项
- 管理员面板增加删除所有未激活帐户操作
- 增加反向代理用户认证支持 [#165](https://github.com/gogits/gogs/issues/165)
- 增加 `server -> ENABLE_GZIP` 配置选项支持应用级别 GZIP

#### 其它变更

- 全新设计的官方网站（[gogs.io](http://gogs.io)）

### V0.4.2(2014-6-6)

#### Bug 修复

- 系统邮件未使用 `mailer -> FROM` 配置选项的值作为发送者 [#214](https://github.com/gogits/gogs/issues/214)
- 创建仓库页面 gitignore 和 license 选项列表不必要的前缀 [#230](https://github.com/gogits/gogs/issues/230)
- 评论长度最大为 255 [#232](https://github.com/gogits/gogs/issues/232)
- 无法创建使用自定义 gitignore 和 license 文件的仓库 [#237](https://github.com/gogits/gogs/issues/237)

### V0.4.1(2014-6-2)

#### Bug 修复

- 当未使用 SSH 默认端口（22）时无法执行克隆操作 [#94](https://github.com/gogits/gogs/issues/94) 
- 使用 PostgreSQL 时无法迁移仓库 [#141](https://github.com/gogits/gogs/issues/141)
- 在公开活动列表显示私有仓库活动 [#148](https://github.com/gogits/gogs/issues/148)
- 安装页面管理员用户名未进行验证 [#149](https://github.com/gogits/gogs/issues/149)
- 修改用户名未完全更新权限表 [#150](https://github.com/gogits/gogs/issues/150)
- 没有 master 分支时发生 panic
- 删除分支时发生 panic [#155](https://github.com/gogits/gogs/issues/155)
- 当评论者不是仓库拥有者时，会跳转至 404 页面 [#159](https://github.com/gogits/gogs/issues/159)
- 当 Issue 的创建者已不存在时，会跳转至 500 页面 [#167](https://github.com/gogits/gogs/issues/167)
- 在代码块中使用 @ 符号会被认为是提醒操作 [#178](https://github.com/gogits/gogs/issues/178)

#### 功能改进

- 允许在数据库中取消社交帐号的关联
- 增加新增评论和在评论中被提醒的邮件提醒
- 增加当有新评论时会显示在活动列表中
- 管理面板增加清理未绑定 OAuth 操作
- 缺陷管理底层系统
- 支持同时将日志记录到多个符合条件的适配器
- 在用户首页显示参与协作的项目
- 增加编辑 Issue 时可进行预览 [#204](https://github.com/gogits/gogs/issues/204)
- 允许通过设置环境变量 `GOGS_CUSTOM` 来设置全局自定义目录 [#209](https://github.com/gogits/gogs/issues/209)
- 增加 `log -> ROOT_PATH` 配置选项来自定义日志文件路径 [#209](https://github.com/gogits/gogs/issues/209)

#### 新增特性

- 支持 SMTP 用户认证 [#8](https://github.com/gogits/gogs/issues/8)
- 支持用户名包含点 `.` [#91](https://github.com/gogits/gogs/issues/91)
- 支持 添加/删除 仓库协作者
- 增加 `server -> DISABLE_ROUTER_LOG` 配置选项来禁止路由访问日志
- 增加 `picture -> DISABLE_GRAVATAR` 配置选项来禁止 Gravatar
- 增加 `gogs dump` 命令用于打包文件和数据库
- 支持 Web 钩子服务 [#98](https://github.com/gogits/gogs/issues/98)
- 增加 已读/未读 状态给 Issue
- 增加 Issue 指派人员功能
- 增加文件历史页面 [#166](https://github.com/gogits/gogs/issues/166)
- 增加自定义 .gitignore 和 license 文件的支持，将新文件增加至 `custom/conf/gitignore` 和 `custom/conf/license` 即可 [#174](https://github.com/gogits/gogs/issues/174)
- 增加里程碑功能到缺陷追踪
- 支持下载 tar.gz 格式的发布版本源码 [#186](https://github.com/gogits/gogs/issues/186)
- 增加 `server -> STATIC_ROOT_PATH` 配置选项来指定自定义模板和静态文件路径 [#209](https://github.com/gogits/gogs/issues/209)

#### 其它变更

- 官方网站上线（[gogs.io](http://gogs.io)）
- 支持通过 Vagrant 安装（[备注](https://github.com/geerlingguy/ansible-vagrant-examples/tree/master/gogs)）
- 支持通过 AUR 包管理安装 [#176](https://github.com/gogits/gogs/issues/176)

### V0.3.1(2014-4-28)

#### Bug 修复

- 当 tag 没有作者时会导致 panic [#92](https://github.com/gogits/gogs/issues/92)
- Docker 启动脚本的相关问题 [#124](https://github.com/gogits/gogs/pull/124) [#129](https://github.com/gogits/gogs/pull/129)
- 单个文件浏览时图片体积过大而导致样式溢出

#### 功能改进

- 在安装页面记住数据库选项

#### 新增特性

- 对 LDAP/Microsoft Active Directory 的基本支持 [#112](https://github.com/gogits/gogs/pull/112)
- 增加离线模式来禁止从 CDN 获取资源
- 支持使用 e-mail 登录

#### 其它变更

- 修正许多语法和拼写错误
- 提供 MySQL 引擎初始化错误的解决方案（[备注](https://github.com/gogits/gogs/wiki/Troubleshooting#error-1071-specified-key-was-too-long-max-key-length-is-1000-bytes)）
- 当激活 SQLite3 选项时将其作为默认数据库

### V0.3.0(2014-4-23)

#### Bug 修复

- 单击复制克隆链接按钮无效（[备注](https://github.com/gogits/gogs/wiki/Known-Issues#repository-viewerurl-usernamereponame)）
- 删除用户时未清理相应的权限表和关注表的数据
- 服务器日志未记录到正确位置

#### 功能改进

- 在提醒邮件中增加相应的 Issue 链接
- 为每个用户增加单独的盐
- 使用 PBKDF2 和用户单独的盐来加密密码（[备注](https://github.com/gogits/gogs/wiki/Troubleshooting#upgrade-from-v020)）
- 大幅缩短在获取仓库文件时的时间、CPU 和内存占用
- 按页面显示仓库 Commits 列表
- 使用构建 tags 来激活 SQLite3 选项（[备注](https://github.com/gogits/gogs/wiki/Install-from-source#install)）

#### 新增特性

- 支持重命名 仓库/用户
- 支持转移仓库所有权
- 支持重置用户密码
- 支持在 Markdown 渲染中捕捉 `@someone`、`#issueNum`、SHA1 字符串和 Issue 链接
- 支持在创建 Issue 时对 @ 到的用户进行邮件提醒
- 支持 `go get` 的 `meta` 标签
- 支持设置默认分支
- 支持 HTTP(S) 推送
- 支持在指定分支根据关键字搜索 commit
- 支持私有仓库
- 支持迁移和镜像 公开/私有 仓库
- 支持采用社交帐号登录（GitHub、Google、QQ、微博）
- 支持查看和新增 release（使用已有 tag 或直接新建）
- 支持下载指定 commit 的 zip 文件
- 支持根据 tag 浏览仓库

#### 其它变更

- 服务端和客户端的 Git 版本要求提升至 1.6.6（用于支持 Smart HTTP）
- 支持 Docker 部署（[备注](https://github.com/gogits/gogs/tree/master/dockerfiles)）

### V0.2.0(2014-4-1)

- 首个公开发布版本