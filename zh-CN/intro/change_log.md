---
name: 变更日志
---

# 变更日志

### 未发布

#### Bug 修复

- 如果仓库曾经为公开的，则变为私有后相关活动信息未被设为私有 [#4414](https://github.com/gogits/gogs/issues/4414)
- 探索页面分页不正确 [#4441](https://github.com/gogits/gogs/issues/4441)
- 创建合并请求完成后发生错误 [#4572](https://github.com/gogits/gogs/issues/4572)

### 0.11.19 @ 2017-06-10

#### Bug 修复

- 无法使用 go get 子包 [#1878](https://github.com/gogits/gogs/issues/1878)
- 非首次使用 LDAP 登录无法更新用户为管理员 [#2855](https://github.com/gogits/gogs/issues/2855)
- 使用 PAM 登录时发生错误 [#4216](https://github.com/gogits/gogs/issues/4216)
- PostgreSQL 恢复备份后出现错误 `unique constraint violation` [#4357](https://github.com/gogits/gogs/issues/4357)
- IPython notebook 的图片无法显示 [#4366](https://github.com/gogits/gogs/issues/4366)
- 编辑文件预览时无法正确处理图片相对链接 [#4368](https://github.com/gogits/gogs/issues/4368)
- 提交历史页面无法渲染 Emoji [#4439](https://github.com/gogits/gogs/issues/4439)
- 查看包含文件权限更改的单个提交时 CPU 异常高 [#4475](https://github.com/gogits/gogs/issues/4475)
- 无法修改协作者的权限 [#4512](https://github.com/gogits/gogs/issues/4512)

#### 新增特性

- 支持两步验证登录 [#945](https://github.com/gogits/gogs/issues/945)
- 支持 LDAP 登录时验证组成员身份 [#4398](https://github.com/gogits/gogs/pull/4398)

#### 功能改进

- 安装页面检查 SMTP 地址中是否包含端口号 [#2243](https://github.com/gogits/gogs/issues/2243)
- 镜像仓库没有拉取新代码提交时不更新最后更新时间 [#4341](https://github.com/gogits/gogs/issues/4341)
- 支持 IPython Notebook 形式的 README [#4367](https://github.com/gogits/gogs/issues/4367)
- 支持自定义 TLS 相关配置 [#4450](https://github.com/gogits/gogs/issues/4450)

### 0.11.4 @ 2017-04-05

#### Bug 修复

- 在进行 HTTP/HTTPS 推送和拉取时客户端没有提示用户输入凭据
- 镜像用户凭据没有进行 URL 编码 [#4014](https://github.com/gogits/gogs/issues/4014)
- 仓库禁用合并请求时，发起合并请求按钮仍旧在分支页面显示 [#4377](https://github.com/gogits/gogs/issues/4377)
- 用户在安装页面发生验证错误时应用会崩溃 [#4383](https://github.com/gogits/gogs/issues/4383) 

### 0.11 @ 2017-04-03

#### Bug 修复

- 编辑个人信息发生验证错误时丢失内容 [#1123](https://github.com/gogits/gogs/issues/1123)
- 组织控制面板显示错误的仓库统计 [#4351](https://github.com/gogits/gogs/issues/4351)
- 从 0.10 之前的版本自动迁移失败 [#4355](https://github.com/gogits/gogs/issues/4355)
- 允许公开访问工单的私有仓库没有正确处理匿名访问 [#4359](https://github.com/gogits/gogs/issues/4359)

### 0.11 RC @ 2017-03-27

#### Bug 修复

- 不正确的会话文件权限 [#3363](https://github.com/gogits/gogs/issues/3363)
- API：仓库对象的权限字段返回无效的值 [#4309](https://github.com/gogits/gogs/issues/4309)
- 非本地用户无法更新个人设置 [#4313](https://github.com/gogits/gogs/issues/4313)
- 工单索引不存在会显示随机工单 [#4315](https://github.com/gogits/gogs/issues/4315)
- 无法从二级派生仓库发起合并请求 [#4324](https://github.com/gogits/gogs/issues/4324)
- 无法更新保护分支白名单 [#4333](https://github.com/gogits/gogs/issues/4333)
- 派生、迁移和镜像仓库的体积没有正确更新 [#4336](https://github.com/gogits/gogs/issues/4336)

#### 新增特性

- 支持私有仓库工单的公开访问 [#649](https://github.com/gogits/gogs/issues/649)
- 支持私有仓库 Wiki 的公开访问 [#2157](https://github.com/gogits/gogs/issues/2157)
- 支持重新推送 Web 钩子的历史记录 [#2187](https://github.com/gogits/gogs/issues/2187)
- API：同步镜像仓库 [#2235](https://github.com/gogits/gogs/issues/2235)
- 支持在控制面板中加载更多的活动内容 [#2511](https://github.com/gogits/gogs/issues/2511)
- 支持设置指定当前用户时候登录的 Cookie 值 [#2885](https://github.com/gogits/gogs/issues/2885)
- 支持备份及恢复 [#2924](https://github.com/gogits/gogs/issues/2924)
- 支持空仓库的工单和 Wiki 操作 [#4104](https://github.com/gogits/gogs/issues/4104)
- 提交历史页面自定义每页显示的数量 [#4230](https://github.com/gogits/gogs/issues/4230)
- 用户设置页面添加管理仓库面板 [#4277](https://github.com/gogits/gogs/issues/4277)

#### 功能改进

- 探索页面显示私有但有访问权限的仓库 [#3088](https://github.com/gogits/gogs/issues/3088)
- 允许在安装页面选择使用终端模式的日志 [#3119](https://github.com/gogits/gogs/issues/3119)
- 允许配置 XORM 的日志器 [#3183](https://github.com/gogits/gogs/issues/3183)
- 添加有关 HTML 渲染模式的配置选项 [#3608](https://github.com/gogits/gogs/issues/3608)
- Web 钩子推送事件添加有关文件被添加、删除和修改的信息 [#3897](https://github.com/gogits/gogs/issues/3897)
- 允许设置控制面板每页显示的活动数量 [#4247](https://github.com/gogits/gogs/issues/4247)

### 0.10.18 @ 2017-03-14

#### Bug 修复

- 镜像仓库同步完成后未修改最后更新时间 [#2807](https://github.com/gogits/gogs/issues/2807)
- **回退** 无法编辑和查看版本发布草稿 [#4262](https://github.com/gogits/gogs/issues/4262)

#### 功能改进

- 更多的 Web 钩子事件
- 所有的工单参与者都会收到通知邮件 [#2929](https://github.com/gogits/gogs/issues/2929)
- 白名单用户可以跳过保护分支的合并请求检查 [#4207](https://github.com/gogits/gogs/issues/4207)

#### 新增特性

- 在管理面板显示仓库体积
- 支持添加附件到版本发布 [#1614](https://github.com/gogits/gogs/issues/1614)
- 仓库分支页面 [#2310](https://github.com/gogits/gogs/issues/2310)
- 支持 Smartypants 以及其配置分区 `[smartypants]` [#4162](https://github.com/gogits/gogs/issues/4162)

### 0.10.8 @ 2017-03-07

#### Bug 修复

- Windows `mws` 版的 Git 钩子无法正常使用
- 包含图片的链接无法指向正确的 URL [#2636](https://github.com/gogits/gogs/issues/2636)
- Web 编辑器无法创建带有斜杠的分支 [#3568](https://github.com/gogits/gogs/issues/3568)
- 克隆仓库时无法省略 `.git` 后缀 [#4189](https://github.com/gogits/gogs/issues/4189)
- Git 钩子工作目录不是仓库目录 [#4225](https://github.com/gogits/gogs/issues/4225)
- `go get` 功能支持回退 [#4226](https://github.com/gogits/gogs/issues/4226)
- Web 钩子的忽略 TLS 验证选项无法生效 [#4228](https://github.com/gogits/gogs/issues/4228)

#### 功能改进

- 邮箱文本编码默认设置为 `text/html`，并可使用配置选项 `[mailer] USE_PLAIN_TEXT` 禁用
- 使用创建仓库的用户信息作为首个代码提交的作者，而不是系统用户
- 支持 Gogs 相关的 Git 钩子环境变量 [#4094](https://github.com/gogits/gogs/issues/4094)

**更早的变更日志可以在 [GitHub](https://github.com/gogits/gogs/releases?after=v0.10.8) 上找到。**
