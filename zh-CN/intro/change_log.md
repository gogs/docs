---
name: 变更日志
---

# 变更日志

### v0.7.x（未发布）

#### Bug 修复

- 坑爹的代码高亮 [#670](https://github.com/gogits/gogs/issues/670) [#1315](https://github.com/gogits/gogs/issues/1315) [#1549](https://github.com/gogits/gogs/issues/1549) [#1712](https://github.com/gogits/gogs/issues/1712)
- 坑爹的复制链接按钮 [#1168](https://github.com/gogits/gogs/issues/1168) [#1396](https://github.com/gogits/gogs/issues/1396) 
- 坑爹的下载源码 UI [#1668](https://github.com/gogits/gogs/issues/1668)
- 测试补丁（Patch）时未检出正确的基准分支 [#1931](https://github.com/gogits/gogs/issues/1931) 
- 分支和标签选择列表的 z-index 值错误 [#1942](https://github.com/gogits/gogs/issues/1942) 
- 文件内容浏览页面无法正确显示巨型图片
- 管理员创建的帐户注册通知邮件中未提供登录 URL [#1979](https://github.com/gogits/gogs/issues/1979) 
- 仓库描述在派生完成之后未真正同步 [#1981](https://github.com/gogits/gogs/issues/1981) 
- 派生仓库在修改设置时会自动修改可见性 [#1987](https://github.com/gogits/gogs/issues/1987) 

#### 功能改进

- 控制面板的协作仓库根据最后更新时间排序 [#1302](https://github.com/gogits/gogs/issues/1302) 
- 在活动线显示工单（Issue）的标题和内容 [#1854](https://github.com/gogits/gogs/issues/1854) 
- 在活动线的推送代码列表中显示可用的自定义头像
- 允许使用配置选项 `[other] SHOW_FOOTER_VERSION = true` 来禁止在非管理员页面的页脚显示版本信息 [#1957](https://github.com/gogits/gogs/issues/1957) 

### v0.7.6 @ 2015-11-12

#### Bug 修复

- 子目录下的图片不能正确渲染相对链接 [#1904](https://github.com/gogits/gogs/issues/1904)
- SSH 操作无法处理大小写混合的 URL
- 使用子路径时删除系统提示后重定向至错误的 URL [#1930](https://github.com/gogits/gogs/issues/1930) 

#### 功能改进

- 在代码提交历史页面显示当前历史所属的分支 [#1572](https://github.com/gogits/gogs/issues/1572) 
- 允许在工单页面使用 Tab 键移动焦点至按钮并使用 `Enter` 或空格触发单击事件 [#1824](https://github.com/gogits/gogs/issues/1824) [#1917](https://github.com/gogits/gogs/issues/1917) 

#### 新增特性

- 允许使用配置选项 `[server] START_SSH_SERVER = true` 来启动内置 SSH 服务器

### v0.7.0 @ 2015-11-08

#### Bug 修复

- 安装时管理员邮箱不允许使用 `root@localhost` [#470](https://github.com/gogits/gogs/issues/470)
- 工单（Issue）浏览页面错误的代码提交（Commit）引用顺序 [#1602](https://github.com/gogits/gogs/issues/1602)
- 注册成功后提示了不准确的邮箱登陆地址 [#1697](https://github.com/gogits/gogs/issues/1697)
- 迁移仓库无法使用 `--all` 参数推送 [#1705](https://github.com/gogits/gogs/issues/1705)
- 拥有管理员权限的团队成员无法关闭或重新开启工单（Issue）[#1748](https://github.com/gogits/gogs/issues/1748)
- 超大的文件差异（Diff）对比导致内存溢出 [#1790](https://github.com/gogits/gogs/issues/1790)
- 当没有实际可更新内容时，推送会返回错误消息 [#1896](https://github.com/gogits/gogs/issues/1896) 
- 使用相对路径的图片生成错误的超链接 [#1904](https://github.com/gogits/gogs/issues/1904) 

#### 功能改进

- 在文件对比差异中识别文件重命名和位置变更 [#1078](https://github.com/gogits/gogs/issues/1078)
- 控制面板的工单（Issue）增加排序功能 [#1459](https://github.com/gogits/gogs/issues/1459)
- 只允许管理员或授权用户迁移本地仓库 [#1511](https://github.com/gogits/gogs/issues/1511)
- 管理员可以在后台创建用户的同时向其发送注册成功邮件 [#1525](https://github.com/gogits/gogs/issues/1525)
- 克隆 URL 显示原本的大小写 [#1895](https://github.com/gogits/gogs/issues/1895)

#### 新增特性

- 支持合并请求（Pull Request） [#5](https://github.com/gogits/gogs/issues/5)
- 支持自动为图片渲染可单击的链接 [#1433](https://github.com/gogits/gogs/issues/1433)
- 新增配置选项 `[repository] FORCE_PRIVATE` 来强制要求所有新建仓库必须为私有的 [#1657](https://github.com/gogits/gogs/issues/1657)

#### 其它变更

- 停止对 Go 1.2 系列版本的支持，最低要求改为 Go 1.3 版本。
- 0.5 系列版本将从 0.8 版本开始停止支持

### v0.6.15 @ 2015-09-26

#### Bug 修复

- 仓库名称包含 "git" 时无法访问 [#1593](https://github.com/gogits/gogs/issues/1593)
- 控制面板的协作仓库链接丢失子路径前缀 [#1594](https://github.com/gogits/gogs/issues/1594)
- 推送新分支时会重复触发代码提交消息对工单的引用 [#1595](https://github.com/gogits/gogs/issues/1595)
- 上传图片未对子路径作处理 [#1603](https://github.com/gogits/gogs/issues/1603)
- 添加新的 SSH 公钥时注释包含空格会被截断 [#1622](https://github.com/gogits/gogs/issues/1622)
- 修改标签标题会重置其颜色 [#1659](https://github.com/gogits/gogs/issues/1659)

#### 功能改进

- 允许使用环境变量 `GOGS_WORK_DIR` 来指定工作目录
- 在创建完用户只会对用户类型进行转换 [#748](https://github.com/gogits/gogs/issues/748)
- 在新建和迁移仓库时根据组织的最后更新时间进行排序 [#1585](https://github.com/gogits/gogs/issues/1585)

#### 新增特性

- 增加 TiDB 作为后端数据库的支持
- 增加 Emoji 支持 [#633](https://github.com/gogits/gogs/issues/633)
- 增加通过设置配置选项 `[service] ENABLE_CAPTCHA = false` 来禁用验证码服务 [#697](https://github.com/gogits/gogs/issues/697)
- 增加对 SMTP 授权时只允许特定域名的支持 [#1620](https://github.com/gogits/gogs/issues/1620)

#### 其它变更

- 移除社交帐号登录支持

### v0.6.9 @ 2015-09-05

#### Bug 修复

- 文件名包含双引号导致仓库无法读取 [#966](https://github.com/gogits/gogs/issues/966)
- 时区显示问题 [#1500](https://github.com/gogits/gogs/issues/1500)
- 删除部署密钥失败 [#1535](https://github.com/gogits/gogs/issues/1535)

#### 功能改进

- 增加 Web 钩子上次推送状态的显示、最近推送记录和新的钩子事件
- 自动记忆最后一次创建仓库的可见性 [#965](https://github.com/gogits/gogs/issues/965)
- LDAP 支持 BindDN 字段和 TLS 协议 [#1145](https://github.com/gogits/gogs/issues/1145)
- 显著改进 LDAP 支持 [#1476](https://github.com/gogits/gogs/pull/1476)
- 邮件发送支持 'AUTH LOGIN' [#1517](https://github.com/gogits/gogs/pull/1517)
- 增加配置选项 `[markdown] ENABLE_HARD_LINE_BREAK` 来开启 Markdown 渲染时的换行扩展

#### 新增特性

- 为组织增加控制面板工单管理页面
- 允许编辑已发布的评论 [#1280](https://github.com/gogits/gogs/issues/1280)
- 支持 README 模板 [#1487](https://github.com/gogits/gogs/issues/1487)

#### 其它变更

- 增加 [官方 Docker 镜像](https://hub.docker.com/r/gogs/gogs/)
- 修改用户密码的最小允许长度为 1
- 修改 RSA 的最小允许长度为 1024 [#1519](https://github.com/gogits/gogs/pull/1519)
- 修改邮箱地址的最大允许长度为 254 [#1579](https://github.com/gogits/gogs/pull/1579)

### v0.6.5 @ 2015-08-16

#### Bug 修复

- 不允许匿名的 SSH 克隆
- 私有仓库无法通过 SSH 推送来触发 Web 钩子
- 仓库所有者无法将工单指派给自己 [#747](https://github.com/gogits/gogs/issues/747)
- 工单无法指派给组织成员 [#839](https://github.com/gogits/gogs/issues/839)
- 创建工单时可能会触发多次请求 [#1051](https://github.com/gogits/gogs/issues/1051)
- 添加附件时显示 "无法解析 JSON" [#1233](https://github.com/gogits/gogs/issues/1233)
- 初始化新仓库之后未删除临时目录 [#1331](https://github.com/gogits/gogs/issues/1331)
- 重命名组织时可以使用中文名 [#1439](https://github.com/gogits/gogs/issues/1439)

#### 功能改进

- 支持自定义头像源 [#1457](https://github.com/gogits/gogs/pull/1457)

#### 新增特性

- 增加部署密钥支持 [#334](https://github.com/gogits/gogs/issues/334)
- 禁用 Gravatar 时根据邮箱为用户生成随机头像
- 增加对工单排序的功能

### v0.6.3 @ 2015-08-02

#### Bug 修复

- 标签被编辑后消失 [#542](https://github.com/gogits/gogs/issues/542)
- 文件差异页面如果文件名包含空格则会被截断 [#985](https://github.com/gogits/gogs/issues/985)
- 只允许使用 HTTPS 迁移仓库 [#1000](https://github.com/gogits/gogs/issues/1000)
- 私有仓库的工单活动会显示在公开活动页面 [#1112](https://github.com/gogits/gogs/issues/1112)
- 所有用户的邮箱都是公开的 [#1127](https://github.com/gogits/gogs/issues/1127)
- API 调用未进行强制登录验证 [#1128](https://github.com/gogits/gogs/issues/1128)
- 访问使用 URL 编码的文件名时显示 404 [#1137](https://github.com/gogits/gogs/issues/1137)
- 可以使用组织的 URL 来访问用户的个人页面 [#1169](https://github.com/gogits/gogs/issues/1169)
- LDAP 授权未检查空白的用户名 [#1207](https://github.com/gogits/gogs/issues/1207)
- 生成的 SSL 证书没有 CN 字段 [#1231](https://github.com/gogits/gogs/issues/1231)
- 删除组织仓库的协作者会删除组织仓库 [#1279](https://github.com/gogits/gogs/issues/1279)
- 可以通过篡改表单创建其它用户的仓库 [#1289](https://github.com/gogits/gogs/issues/1289)

#### 功能改进

- 针对保留名称具有更清晰的错误描述 [#1070](https://github.com/gogits/gogs/issues/1070)
- 管理员可以编辑用户的全名 [#1130](https://github.com/gogits/gogs/issues/1130)
- 不对未登录的用户显示组织邮箱 [#1204](https://github.com/gogits/gogs/issues/1204)
- 允许使用带有 ".git" 后缀的 URL 访问仓库主页 [#1227](https://github.com/gogits/gogs/issues/1227)

#### 新增特性

- 支持实时 Web 钩子 [#835](https://github.com/gogits/gogs/issues/835)

#### 其它变更

- 增加意大利语支持
- 在部署模式下禁用 Macaron 框架的彩色日志来提升性能
- 在探索页面显示仓库所有者名称 [#1150](https://github.com/gogits/gogs/issues/1150)

### v0.6.1 @ 2015-03-26

#### Bug 修复

- 带有 `#` 开头的行内代码被渲染为工单索引 [#637](https://github.com/gogits/gogs/issues/637)
- 当 `REQUIRE_SIGNIN_VIEW = true` 时未登录用户仍旧能够访问组织页面 [#1101](https://github.com/gogits/gogs/issues/1101)
- 新建版本发布按钮总是对所有人可见 [#1114](https://github.com/gogits/gogs/issues/1114)
- 镜像仓库转移所有权后无法继续同步 [#1120](https://github.com/gogits/gogs/issues/1120)
- 即使组织中的其它团队和某个仓库没有联系，团队的成员也可以获得仓库的权限
- LDAP 的添加和修改表单不一致 [#1124](https://github.com/gogits/gogs/issues/1124)
- 向组织的仓库添加协作者时团队成员的权限会丢失 [#1143](https://github.com/gogits/gogs/issues/1143)

#### 功能改进

- 当 Gravatar 被禁用时隐藏相应的设置字段 [#1098](https://github.com/gogits/gogs/issues/1098)
- 允许通过 `git://` 来迁移外部仓库 [#1105](https://github.com/gogits/gogs/pull/1105)
- 增加配置选项 `[service] DISABLE_MINIMUM_KEY_SIZE_CHECK` 禁止检查响应类型的密钥最小长度 [#1133](https://github.com/gogits/gogs/pull/1133)
- 当不是第一次启动安装程序时，不在表单中自动填写数据库的密码 [#1140](https://github.com/gogits/gogs/issues/1140)
- 允许通过 `[mailer] DISABLE_HELO` 配置选项来禁用 HELO 操作
- 允许通过 `[mailer] HELO_HOSTNAME` 配置选项来自定义 HELO 操作所使用的主机名

#### 其它变更

- 使用 `fake@gogs.local` 替换私有的邮箱地址作为默认的 Git `user.email` 设置 [#1089](https://github.com/gogits/gogs/issues/1089)
- 部分页面的 UI 改进

### v0.6.0 @ 2015-03-19

#### Bug 修复

- 管理员修改用户密码未进行规则验证 [#851](https://github.com/gogits/gogs/issues/851)
- 拥有多个团队成员身份的用户仓库权限级别不正确 [#858](https://github.com/gogits/gogs/issues/858)
- 删除工单时标签计数不更新 [#933](https://github.com/gogits/gogs/issues/933)
- 可以向镜像仓库推送代码 [#948](https://github.com/gogits/gogs/issues/948)
- 未加载自定义配置就检查模板文件版本 [#954](https://github.com/gogits/gogs/issues/954)
- 未判断附件和头像地址是否为绝对路径
- 活动时间线中重复的链接前缀 [#988](https://github.com/gogits/gogs/issues/988)
- LDAP 用户无法删除仓库 [#1006](https://github.com/gogits/gogs/issues/1006)
- 无法处理没有 .gitmodules 文件的 SubModule [#1023](https://github.com/gogits/gogs/issues/1023)
- HTTP/HTTPS 推送代码时 Update 函数调用错误 [#1037](https://github.com/gogits/gogs/issues/1037)
- 管理员页面在使用反向代理子路径时 URL 前缀未正确补上 [#1043](https://github.com/gogits/gogs/pull/1043)
- 站点首页设置没有考虑反向代理子路径的情况 [#1055](https://github.com/gogits/gogs/pull/1055)
- 空白仓库页面的帮助连接未正确显示 [#1082](https://github.com/gogits/gogs/issues/1082)

#### 功能改进

- 允许通过 Socket 连接 MySQL [#872](https://github.com/gogits/gogs/issues/872)
- 允许 SMTP 客户端使用 TLS 证书 [#943](https://github.com/gogits/gogs/pull/943)
- 修正 504 5.5.2 <localhost>: Helo command rejected [#973](https://github.com/gogits/gogs/pull/973)

#### 新增特性

- 允许导入本地 Git 仓库 [#99](https://github.com/gogits/gogs/issues/99)
- 支持绑定多个邮箱 [#755](https://github.com/gogits/gogs/pull/755)

### v0.5.13 @ 2015-02-13

#### Bug 修复

- 邮箱地址在渲染时被认作@某人 [#737](https://github.com/gogits/gogs/issues/737)
- 使用 SQLite3 添加团队成员时发生恐慌 [#739](https://github.com/gogits/gogs/issues/739)
- 迁移仓库没有 Update 钩子 [#789](https://github.com/gogits/gogs/issues/789)
- 当添加空仓库时，`num_watchers` 字段更新失败 [#819](https://github.com/gogits/gogs/issues/819)
- 当通过 SSH 推送代码时 Web 钩子会发生数据竞争 [#827](https://github.com/gogits/gogs/issues/827)
- 代码提交消息可进行 XSS 攻击 [#828](https://github.com/gogits/gogs/issues/828)
- 用户自动补全功能失效 [#832](https://github.com/gogits/gogs/issues/832)
- 有时会选择错误的 README 进行渲染 [#877](https://github.com/gogits/gogs/issues/877)
- 无法正确解析来自 LDAP 的 UTF-8 编码的字符串 [#916](https://github.com/gogits/gogs/issues/916)
- 用户未登录时尝试关注某个仓库会发生恐慌 [#929](https://github.com/gogits/gogs/issues/929)

#### 功能改进

- 迁移仓库时使用标准库解析用户信息 [#822](https://github.com/gogits/gogs/pull/822)
- 更加灵活的 SSH 公钥格式支持：OpenSSH、SSH2 和 base64 编码格式 [#825](https://github.com/gogits/gogs/pull/825)
- 可以使用 `./gogs web -port 3001` 来防止第一次运行 Gogs 时发生端口冲突
- 允许禁用 SSH 功能 [#883](https://github.com/gogits/gogs/issues/883)
- 当注册被禁止时默认隐藏注册相关按钮和链接 [#884](https://github.com/gogits/gogs/issues/884)
- 推送 Web 钩子时可以禁止验证证书有效性 [#891](https://github.com/gogits/gogs/issues/891)
- 差异对比页面将被删除的文件链接到上一次提交的状态而不显示 404 页面 [#911](https://github.com/gogits/gogs/pull/911)
- 能够在 Flash 被禁用的情况下一键选中仓库克隆地址以便复制 [#937](https://github.com/gogits/gogs/pull/937)

#### 新增特性

- 通过提交信息来控制工单状态 [#668](https://github.com/gogits/gogs/issues/668)
- 能够根据数据完全重写 `.ssh/authorized_key` 文件 [#818](https://github.com/gogits/gogs/pull/818)
- 能够根据配置重新生成仓库的 Update 钩子文件
- 增加俄语和日语支持
- 在对比模式下高亮选中代码 [@makhov](https://github.com/makhov)
- 允许在通过 HTTP(S) 推送时使用应用密钥 [#842](https://github.com/gogits/gogs/issues/842)

**更早的变更日志可以在 [GitHub](https://github.com/gogits/gogs/releases) 上找到。**
