---
name: 变更日志
---

# 变更日志

### 未发布

#### Bug 修复

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

### 0.10.1 @ 2017-02-28

#### Bug 修复

- 非组织仓库无法保存分支保护选项

### 0.10 @ 2017-02-27

#### Bug 修复

- 迁移仓库时检测到 Wiki 会意外地将仓库本身删除
- 无法通过 Web 编辑器预览文件对比差异
- 组织级 Web 钩子最后推送状态无法被更新
- 管理员无法删除组织仓库
- 创建合并请求页面无法查看分列视图 [#3695](https://github.com/gogits/gogs/issues/3695)
- 无法编辑派生仓库的版本发布 [#4174](https://github.com/gogits/gogs/issues/4174)

#### 功能改进

- 允许添加组织成员为仓库协作者
- 允许设置自定义页面头部和底部内容 [#1286](https://github.com/gogits/gogs/issues/1286)
- 允许测试推送只触发当前浏览的 Web 钩子 [#3030](https://github.com/gogits/gogs/issues/3030)
- 允许仅启用部分类型的 Web 钩子 [#3356](https://github.com/gogits/gogs/issues/3356)
- 支持 Web 钩子发送 SHA256 HMAC 校验和 [#3692](https://github.com/gogits/gogs/issues/3692)
- 添加配置选项 `[session] CSRF_COOKIE_NAME` 用于自定义 CSRF Cookie 名称 [#4172](https://github.com/gogits/gogs/issues/4172)
- 允许为组织仓库添加用户和团队推送白名单 [#4177](https://github.com/gogits/gogs/issues/4177)

### 0.10 RC @ 2017-02-21

#### Bug 修复

- 未配置邮件服务无法完成安装或启动程序
- 通过 HTTP 推送大量内容时内存溢出 [#636](https://github.com/gogits/gogs/issues/636)
- 无法导航到 Wiki 标题包含 `-` 的页面 [#3754](https://github.com/gogits/gogs/issues/3754)
- 无法编辑标题包含 `#` 的 Wiki 页面 [#3767](https://github.com/gogits/gogs/issues/3767)
- Wiki 标题包含 Tab 键时崩溃 [#3916](https://github.com/gogits/gogs/issues/3916)
- 无法通过 API 关闭里程碑 [#4102](https://github.com/gogits/gogs/issues/4102)
- 强制推送后仓库本地副本无法使用 [#4123](https://github.com/gogits/gogs/issues/4123)
- 完成合并请求后无法删除发起分支 [#4128](https://github.com/gogits/gogs/issues/4128)

#### 功能改进

- 允许派生自己的仓库 [#1791](https://github.com/gogits/gogs/issues/1791)
- 版本发布增加分页功能 [#2164](https://github.com/gogits/gogs/issues/2164)
- 允许将工单指定给只读权限的成员 [#3739](https://github.com/gogits/gogs/issues/3739)
- 允许使用短哈希下载仓库归档 [#3834](https://github.com/gogits/gogs/issues/3834)
- 文件差异对比页面可以高亮某一行

#### 新增特性

- 支持 Discord Web 钩子
- 支持保护分支 [#776](https://github.com/gogits/gogs/issues/776)
- 支持 MSSQL [#3772](https://github.com/gogits/gogs/pull/3772)

#### 其它变更

- 停止支持 0.6.x 系列

**更早的变更日志可以在 [GitHub](https://github.com/gogits/gogs/releases?after=v0.10rc) 上找到。**
