---
name: 变更日志
sort: 1
---

# 变更日志

### v0.5.9 @ 2014-12-13

#### Bug 修复

- 管理面板无效的用户首页链接
- 空仓库的设置页面出现模板渲染错误 [#643](https://github.com/gogits/gogs/issues/643)
- 当 SSH 授权文件不存在时，命令 `gogs fix location` 会发生错误 [#659](https://github.com/gogits/gogs/issues/659)
- 提交历史页面未显示最旧的历史页 [#664](https://github.com/gogits/gogs/issues/664)
- 工单页面的用户主页链接失效 [#682](https://github.com/gogits/gogs/issues/682)
- 头像邮箱地址包含大写字母时会产生错误的哈希值 [#700](https://github.com/gogits/gogs/issues/700)
- Markdown 表格样式不正常 [#703](https://github.com/gogits/gogs/issues/703) 
- 在文件对比页面无法显示 GBK 编码字符 [#711](https://github.com/gogits/gogs/issues/711)
- 当密码包含 `:` 时无法通过 HTTP 基本授权 [#723](https://github.com/gogits/gogs/issues/723)

#### 功能改进

- 在用户搜索 API 中显示 `full_name` 字段 [#677](https://github.com/gogits/gogs/issues/677)
- 在提交历史中显示工单链接 [#712](https://github.com/gogits/gogs/issues/712)

#### 新增特性

- 支持上传自定义头像 [#139](https://github.com/gogits/gogs/issues/139)
- 支持通过配置选项 `[server] LANDING_PAGE` 将探索页面设置为未登录用户的首页 [#543](https://github.com/gogits/gogs/issues/543)
- 运行 `git fack` 作为定时任务、`git gc` 作为管理员操作 [#580](https://github.com/gogits/gogs/issues/580)
- 支持通过 `/:username.keys` 获取用户的公钥列表 [#652](https://github.com/gogits/gogs/issues/652)
- 增加拉脱维亚语支持

### v0.5.8 @ 2014-11-19

#### Bug 修复

- 修复漏洞 CVE-2014-8681 CVE-2014-8682 CVE-2014-8683
- 分支/标签名不能包含 `/` [#101](https://github.com/gogits/gogs/issues/101) [#255](https://github.com/gogits/gogs/issues/255)
- 配置选项 `ENABLE_GZIP` 无效 [#412](https://github.com/gogits/gogs/issues/412)
- 火狐下浏览代码行号与内容不对其 [#457](https://github.com/gogits/gogs/issues/457)
- Git 钩子未过滤 `\r` 字符 [#546](https://github.com/gogits/gogs/issues/546)
- 查看原始文件和文件历史按钮未显示 [#550](https://github.com/gogits/gogs/issues/550)
- 几处 UI 对齐问题 [#554](https://github.com/gogits/gogs/issues/554)
- 无法使用 Redis 作为缓存
- 无法在 Markdown 文件中显示相对路径图片
- 提交信息内容长度很大时 UI 被破坏 [#570](https://github.com/gogits/gogs/issues/570)
- HTTP/HTTPS 克隆不支持 GZIP 编码 [#572](https://github.com/gogits/gogs/issues/572)
- 在浏览自己的个人页面时无法查看私有仓库 [#605](https://github.com/gogits/gogs/issues/605)
- 错误的 MIT 开源许可证文件 [#608](https://github.com/gogits/gogs/issues/608)

#### 功能改进

- 允许协作者在个人页面查看到私有仓库

#### 新增特性

- 允许派生仓库 [#5](https://github.com/gogits/gogs/issues/5)
- Drone CI 持续部署集成 [#12](https://github.com/gogits/gogs/issues/12)
- 能够查看 2 次提交的内容对比页面
- 支持设置 `[picture] GRAVATAR_SOURCE = duoshuo` 来使用 Gravatar 的中国镜像源
- 支持通过管理面板清除所有仓库存档 [#635](https://github.com/gogits/gogs/issues/635)

### v0.5.5 @ 2014-10-10

#### Bug 修复

- 无法下载仓库存档 [#495](https://github.com/gogits/gogs/issues/495)
- 无法根据标签（tag）浏览仓库代码
- 无法将仓库从组织转移到个人用户
- 当仓库所有者将仓库转移给协作者时发生错误
- 不支持注解标签 [#515](https://github.com/gogits/gogs/issues/515)
- 无效的授权认证逻辑

#### 功能改进

- 加强用户邮箱安全性 [#249](https://github.com/gogits/gogs/issues/249)
- 修正行内代码 Markdown 风格 [#491](https://github.com/gogits/gogs/issues/491)
- 在仓库列表视图中增加目录级别提交信息显示
- 修改工单标题最大长度为 255 个字符 [#522](https://github.com/gogits/gogs/issues/522)
- 允许通过自签名服务器发送邮件
- 支持自定义本地化文件

#### 新增特性

- 增加 Git 钩子支持 [#264](https://github.com/gogits/gogs/issues/264)
- 允许 Gogs 运行在反向代理的子路径下 [#463](https://github.com/gogits/gogs/pull/463)
- 增加 `gogs cert` 命令用于生产自签名 HTTPS 的文件 [#487](https://github.com/gogits/gogs/issues/487)
- 增加自定义 `robots.txt` 文件支持
- 增加基本的 SubModule 支持
- 增加法语、荷兰语和繁体中文支持
- 在管理面板增加系统提示功能

### v0.5.2 @ 2014-9-18

#### Bug 修复

- 错误的 `~/.ssh/` 目录权限检查 [#458](https://github.com/gogits/gogs/issues/458)
- 配置选项 `REQUIRE_SIGNIN_VIEW=true` 时依旧可以访问某些页面 [#464](https://github.com/gogits/gogs/issues/464)
- 模板渲染错误 `html/template: "user/activate" is undefined` [#465](https://github.com/gogits/gogs/issues/465)
- 模板函数 `TimeSince` 参数不足 [#473](https://github.com/gogits/gogs/issues/473)
- 组织控制面板中错误的权限检查 [#474](https://github.com/gogits/gogs/pull/474)
- Windows 下无法添加新的 SSH 公钥 [#475](https://github.com/gogits/gogs/issues/475)
- 无法转移仓库所有权 [#481](https://github.com/gogits/gogs/issues/481)

#### 功能改进

- Git 版本要求降低为 1.7.1 [#476](https://github.com/gogits/gogs/issues/476)
- 增加法语支持 [#479](https://github.com/gogits/gogs/pull/479)
- 增加 `git -> MAX_GITDIFF_LINES` 配置选项用于指定 Git Diff 页面的最大显示行数

#### 其它变更

- 演示站点启动 HTTPS 和新域名 [https://try.gogs.io](https://try.gogs.io)

### v0.5.0 @ 2014-9-15

#### Bug 修复

- 浏览由 Gogs 创建的版本发布时发生 panic [#197](https://github.com/gogits/gogs/issues/197)
- 编辑工单或评论时修改里程碑或标签会导致文本丢失 [#216](https://github.com/gogits/gogs/issues/216)
- 通过 SSH 推送的代码无法触发 Web 钩子 [#242](https://github.com/gogits/gogs/issues/242)
- 镜像仓库无法自动更新同步 [#258](https://github.com/gogits/gogs/issues/258)
- 无法在 Windows 下获取静态文件 [#271](https://github.com/gogits/gogs/issues/271)
- 控制面板的工单那链接显示不完整 [#273](https://github.com/gogits/gogs/issues/273)
- 协作者能够修改项目设置
- 非仓库拥有者或协作者也可修改 issue 标签 [#288](https://github.com/gogits/gogs/issues/288)
- 关闭/开启工单时里程碑的统计数据未更新 [#303](https://github.com/gogits/gogs/issues/303)
- 不正确的最大/最小长度限制错误提示 [#340](https://github.com/gogits/gogs/pull/340)
- 配置选项 `ROOT_URL` 未以 `/` 结尾时出现错误 [#367](https://github.com/gogits/gogs/issues/367)
- SSH 公钥包含换行符时无法被删除 [#370](https://github.com/gogits/gogs/issues/370)

#### 功能改进

- 增加 `webhook` 配置分区来自定义 Web 钩子 **任务检查周期** 和 **发送超时**
- 增加仓库 TAR.GZ 格式打包下载按钮
- 当不同版本发布具有相同数量的提交时，使用创建时间排序 [#199](https://github.com/gogits/gogs/issues/199)
- 在应用启动时检查 Git 安装和版本
- 在提交页面显示准确的提交时间 [#281](https://github.com/gogits/gogs/pull/281)
- 允许管理员修改用户密码 [#291](https://github.com/gogits/gogs/pull/291)
- 增加更多类型的 SSH 密钥类型验证支持 [#293](https://github.com/gogits/gogs/pull/293)
- 仓库描述的链接可点击 [#300](https://github.com/gogits/gogs/pull/300)
- 允许使用 `/:username` 作为用户主页路由
- 密码最大长度限制修改为 255 位 [#340](https://github.com/gogits/gogs/pull/340)
- Slack Web 钩子集成 [#379](https://github.com/gogits/gogs/pull/379)
- 允许仓库名称包含 `.` [#453](https://github.com/gogits/gogs/issues/453)

#### 新增特性

- 增加命令 `gogs fix location <old path>` 用于处理 Gogs 应用位置改变
- 支持编辑版本发布以及保存为草稿
- 增加 Cron 任务和运行进程监控面板
- 增加记录日志到数据库选项
- 管理员面板增加删除所有未激活帐户操作
- 增加反向代理用户认证支持 [#165](https://github.com/gogits/gogs/issues/165)
- 增加 `server -> ENABLE_GZIP` 配置选项支持应用级别 GZIP
- 通过提交消息关闭工单 [#302](https://github.com/gogits/gogs/issues/302)
- 增加对仓库的 点赞/取消点赞 功能
- 增加 `.mkd` 作为 Markdown 文件扩展名 [#362](https://github.com/gogits/gogs/issues/362)
- 增加工单评论附件支持 [#307](https://github.com/gogits/gogs/pull/307)
- 增加组织级别 Web 钩子 [#442](https://github.com/gogits/gogs/pull/442)

#### 其它变更

- 全新设计的官方网站（[gogs.io](http://gogs.io)）
- 全站新 UI 设计
- 大部分页面已实现多语言
- 增加 Ubuntu 包管理安装 [#455](https://github.com/gogits/gogs/pull/455)

### v0.4.2 @ 2014-6-6

#### Bug 修复

- 系统邮件未使用 `mailer -> FROM` 配置选项的值作为发送者 [#214](https://github.com/gogits/gogs/issues/214)
- 创建仓库页面 gitignore 和 license 选项列表不必要的前缀 [#230](https://github.com/gogits/gogs/issues/230)
- 评论长度最大为 255 [#232](https://github.com/gogits/gogs/issues/232)
- 无法创建使用自定义 gitignore 和 license 文件的仓库 [#237](https://github.com/gogits/gogs/issues/237)

### v0.4.1 @ 2014-6-2

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
- 支持 创建/管理/删除 组织以及团队管理功能

#### 其它变更

- 官方网站上线（[gogs.io](http://gogs.io)）
- 支持通过 Vagrant 安装（[备注](https://github.com/geerlingguy/ansible-vagrant-examples/tree/master/gogs)）
- 支持通过 AUR 包管理安装 [#176](https://github.com/gogits/gogs/issues/176)

### v0.3.1 @ 2014-4-28

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

### v0.3.0 @ 2014-4-23

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

### v0.2.0 @ 2014-4-1

- 首个公开发布版本