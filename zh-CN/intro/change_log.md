---
name: 变更日志
---

# 变更日志

### 未发布

#### Bug 修复

- 发起合并请求时没有使用当前正在浏览的分支作为对比分支 [#3604](https://github.com/gogits/gogs/issues/3604)
- 非拉丁字符无法生成快捷链接 [#3981](https://github.com/gogits/gogs/issues/3981)
- 尝试向空仓库获取单个文件时发生错误 [#3992](https://github.com/gogits/gogs/issues/3992)
- 攻击者可以派生任意仓库 [#4006](https://github.com/gogits/gogs/issues/4006)

#### 功能改进

- 查看所有指派给我的工单 [#1820](https://github.com/gogits/gogs/issues/1820)

### v0.9.113 @ 2016-12-24

#### Bug 修复

- HTTP 推送占用大量内存 [#636](https://github.com/gogits/gogs/issues/636)
- 使用 Mac OS X 系统下的 Safari 浏览器会使控制面板的最近活动强行分行 [#2875](https://github.com/gogits/gogs/issues/2875)
- 生成错误的用户头像链接 [#3577](https://github.com/gogits/gogs/issues/3577)
- 无法编辑版本发布草稿 [#3590](https://github.com/gogits/gogs/issues/3590)
- 工单提交者删除帐户后无法加载工单
- 攻击者可以删除任意用户的次要邮箱和应用令牌 [#3959](https://github.com/gogits/gogs/issues/3959)
- 攻击者可以删除任意仓库的版本发布 [#3962](https://github.com/gogits/gogs/issues/3962)
- 攻击者可以向工单添加任意仓库的标签

#### 功能改进

- 增加配置选项 `[other] SHOW_FOOTER_TEMPLATE_LOAD_TIME` 以隐藏模板执行时间 [#3492](https://github.com/gogits/gogs/issues/3492)

#### 新增特性

- 支持在探索页面搜索组织 [#2951](https://github.com/gogits/gogs/issues/2951)
- 在完成合并请求后可删除对应分支 [#3225](https://github.com/gogits/gogs/pull/3225)
- 支持禁用仓库相关的 HTTP 操作 [#3667](https://github.com/gogits/gogs/pull/3667)
- 支持使用 HTML5 标签来播放视频文件 [#3967](https://github.com/gogits/gogs/pull/3967)

#### 其它变更

- 增加韩语和加利西亚语支持

### v0.9.97 @ 2016-09-01

#### Bug 修复

- 只有拥有仓库可写权限的用户能发表评论
- 对比差异符号（+/-）没有显示 [#3464](https://github.com/gogits/gogs/pull/3464)
- 归档文件在 Windows 下包含了绝对路径 [#3535](https://github.com/gogits/gogs/pull/3535)

#### 功能改进

- 支持 git-daemon-export-ok 文件 [#2940](https://github.com/gogits/gogs/issues/2940)
- 登陆后重定向到初始页面 [#3089](https://github.com/gogits/gogs/issues/3089)
- 使用用户名作为邮件 FROM 字段的值 [#3279](https://github.com/gogits/gogs/issues/3279)

#### 新增特性

- 支持标签模板 [#1562](https://github.com/gogits/gogs/issues/1562)
- 支持通过 UI 同步镜像仓库 [#2018](https://github.com/gogits/gogs/issues/2018)
- 支持合并请求的 Web 钩子 [#2246](https://github.com/gogits/gogs/pull/2246)
- 支持监听 Unix 套接字 [#2852](https://github.com/gogits/gogs/pull/2852)
- 支持通过 Unix 套接字连接 PostgreSQL 数据库 [#3013](https://github.com/gogits/gogs/issues/3013)
- 支持在迁移仓库同时迁移 Wiki [#3233](https://github.com/gogits/gogs/pull/3233)
- 支持在线编辑仓库文件 [#3460](https://github.com/gogits/gogs/issues/3460)

### v0.9.71 @ 2016-08-10

#### Bug 修复

- 当标签已经存在时，版本发布没用使用标签的创建时间 [#3315](https://github.com/gogits/gogs/issues/3315)
- 使用反向代理时无法显示图片 [#3348](https://github.com/gogits/gogs/issues/3348)
- JavaScript 行数生成破坏代码高亮的元素块 [#3316](https://github.com/gogits/gogs/issues/3316)
- 用户离开组织时没有和任何仓库有关联时发生错误 [#3379](https://github.com/gogits/gogs/issues/3379)
- 合并请求的冲突检查没有及时运行 [#3396](https://github.com/gogits/gogs/issues/3396)
- 组织的控制面板工单显示受限于用户的 `num_repos` 字段 [#3410](https://github.com/gogits/gogs/issues/3410)
- 工单控制面板由您创建分类的统计数字不正确 [#3417](https://github.com/gogits/gogs/issues/3417)

#### 功能改进

- 当 URL 参数包含 `?go-get=1` 时总是返回相应的 go-import 元数据 [#2825](https://github.com/gogits/gogs/issues/2825)
- 增加配置选项 `[git.timeout] GC` 用于自定义 Git GC 超时 [#3091](https://github.com/gogits/gogs/issues/3091)
- Windows 下不再检查 `RUN_USER` [#3158](https://github.com/gogits/gogs/issues/3158)
- 增加配置选项 `[mirror] DEFAULT_INTERVAL` 用于自定义默认镜像更新检查间隔 [#3091](https://github.com/gogits/gogs/issues/3091)

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

**更早的变更日志可以在 [GitHub](https://github.com/gogits/gogs/releases?after=v0.9.46) 上找到。**
