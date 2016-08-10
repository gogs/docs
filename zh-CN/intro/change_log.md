---
name: 变更日志
---

# 变更日志

### v0.9.x（未发布）

#### Bug 修复

- 当标签已经存在时，版本发布没用使用标签的创建时间 [#3315](https://github.com/gogits/gogs/issues/3315)
- 使用反向代理时无法显示图片 [#3348](https://github.com/gogits/gogs/issues/3348)
- JavaScript 行数生成破坏代码高亮的元素块 [#3316](https://github.com/gogits/gogs/issues/3316)
- 组织的控制面板工单显示受限于用户的 `num_repos` 字段 [#3410](https://github.com/gogits/gogs/issues/3410)

#### 功能改进

- 当 URL 参数包含 `?go-get=1` 时总是返回相应的 go-import 元数据 [#2825](https://github.com/gogits/gogs/issues/2825)
- 增加配置选项 `[git.timeout] GC` 用于自定义 Git GC 超时 [#3091](https://github.com/gogits/gogs/issues/3091)
- Windows 下不再检查 `RUN_USER` [#3158](https://github.com/gogits/gogs/issues/3158)

#### 新增特性

- 支持 Federated Avatars
- 允许使用 URL 参数 `?render=1` 使 HTML 在原始模式下返回渲染结果 [#2593](https://github.com/gogits/gogs/issues/2593)

### v0.9.60 @ 2016-08-03

#### Bug 修复

- 合并请求（Pull Request）页面文件差异（Diff）对比的分列视图无法使用 [#2790](https://github.com/gogits/gogs/issues/2790)
- 使用无效的标签名称创建版本发布时不能正确处理错误 [#3076](https://github.com/gogits/gogs/issues/3076)
- 无法 @ 用户名包含横线的用户 [#3107](https://github.com/gogits/gogs/issues/3107)
- 删除合并请求的基准分支后无法浏览页面 [#3181](https://github.com/gogits/gogs/issues/3181)
- 派生仓库的新建合并请求所指向的链接不存在 [#3186](https://github.com/gogits/gogs/issues/3186)
- 使用标签过滤工单时发生错误 [#3327](https://github.com/gogits/gogs/issues/3327)

#### 功能改进

- 对仓库进行分页显示 [#1384](https://github.com/gogits/gogs/issues/1384)
- 针对仓库和用户使用不同的保留关键字和匹配模式 [#2903](https://github.com/gogits/gogs/issues/2903)

#### 新增特性

- 增加工单标签相关的 API
- 支持删除工单评论 [#1601](https://github.com/gogits/gogs/issues/1601)
- 支持下载文件对比差异的补丁文件（Patch）[#2641](https://github.com/gogits/gogs/issues/2641)

### v0.9.48 @ 2016-07-22

#### Bug 修复

- 使用 SQLite3 创建合并请求（Pull Reuqest）时发生错误 [#3291](https://github.com/gogits/gogs/issues/3291)
- 错误的 LDAP 用户名验证规则 [#3295](https://github.com/gogits/gogs/issues/3295)
- 重新生成 Update 钩子操作没有修复错误的脚本权限 [#3302](https://github.com/gogits/gogs/issues/3302)

### v0.9.46 @ 2016-07-17

#### Bug 修复

- 显示超大体积的文本文件时崩溃 [#1513](https://github.com/gogits/gogs/issues/1513)
- 编辑工单后 Emoji 表情被过滤 [#2458](https://github.com/gogits/gogs/issues/2458)	
- 没有对从 LDAP 获取的属性进行规则验证 [#2709](https://github.com/gogits/gogs/issues/2709)
- 原始文件链接包含空格时跳转不正确 [#2842](https://github.com/gogits/gogs/issues/2842)
- 工单被关闭或重新开启时没有邮件提醒 [#2854](https://github.com/gogits/gogs/issues/2854)
- 用户可以获取任意仓库的 Web 钩子内容 [#3057](https://github.com/gogits/gogs/issues/3057)
- 当仓库名称为 `.` 和 `..` 时会触发浏览器的自动行为 [#3229](https://github.com/gogits/gogs/issues/3229)

#### 功能改进

- 下载的档案压缩包内创建与仓库名称相同的父目录 [#518](https://github.com/gogits/gogs/issues/518)
- 使用 `text/plain` 作为默认的邮件内容格式 [#1496](https://github.com/gogits/gogs/issues/1496)
- 离开有未保存内容的页面时提醒用户确认 [#2881](https://github.com/gogits/gogs/issues/2881)
- 私有仓库在被删除后所有分支将变成独立的仓库 [#3232](https://github.com/gogits/gogs/pull/3232)

#### 新增特性

- 支持禁止用户登录 [#2937](https://github.com/gogits/gogs/issues/2937)
- 支持字母结合数字格式（ABC-1234）作为外部工单系统的匹配模式 [#2992](https://github.com/gogits/gogs/issues/2992)
- 支持 PDF 预览 [#2993](https://github.com/gogits/gogs/issues/2993)

#### 其它变更

- 增加土耳其语支持

### v0.9.13 @ 2016-03-19

#### Bug 修复

- 管理员无法在组织首页查看私有仓库 [#2372](https://github.com/gogits/gogs/issues/2372)
- 非本地类型用户允许重置密码 [#2811](https://github.com/gogits/gogs/issues/2811)
- 分支名称包含 '#' 符号时发起合并请求会发生错误 [#2822](https://github.com/gogits/gogs/issues/2822)
- 内置 SSH 服务器潜在的并发问题 [#2850](https://github.com/gogits/gogs/issues/2850)

#### 功能改进

- 根据仓库信息输出相应的 HTML meta 值 [#2670](https://github.com/gogits/gogs/issues/2670)
- 允许使用用户名或全名搜索用户 [#2792](https://github.com/gogits/gogs/issues/2792)

#### 新增特性

- 支持在探索和管理面板搜索用户和仓库 [#13](https://github.com/gogits/gogs/issues/13)

### v0.9.0 @ 2016-03-06

#### Bug 修复

- 使用代码提交消息关闭工单时发生错误 [#2697](https://github.com/gogits/gogs/issues/2697)
- 使用 SQLite3 作为数据库时无法在创建工单时同时指定 2 个或更多的标签 [#2700](https://github.com/gogits/gogs/issues/2700)

#### 功能改进

- 允许在管理员面板测试邮件服务设置 [#1531](https://github.com/gogits/gogs/issues/1531)
- 增强工单标签的可读性 [#2033](https://github.com/gogits/gogs/issues/2033)
- 允许为 Git 操作自定义超时 [#2653](https://github.com/gogits/gogs/issues/2653) [#2701](https://github.com/gogits/gogs/issues/2701) [#2704](https://github.com/gogits/gogs/issues/2704)
- 允许删除用户或组织的当前使用头像

#### 新增特性

- 更加细化的协作者权限管理 [#1146](https://github.com/gogits/gogs/issues/1146)
- 支持在同个仓库内的不同分支之间发起合并请求 [#1597](https://github.com/gogits/gogs/issues/1597)
- 支持在本地仓库检出合并请求 [#1655](https://github.com/gogits/gogs/issues/1655)
- 允许删除 Wiki 页面和其所有数据 [#2183](https://github.com/gogits/gogs/issues/2183)

#### 其它变更

- 增加芬兰语支持

**更早的变更日志可以在 [GitHub](https://github.com/gogits/gogs/releases?after=v0.9.0) 上找到。**
