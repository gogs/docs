---
name: 变更日志
---

# 变更日志

### v0.9.x（未发布）

#### Bug 修复

- 管理员无法在组织首页查看私有仓库 [#2372](https://github.com/gogits/gogs/issues/2372)

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

### v0.8.43 @ 2016-02-24

#### Bug 修复

- 对仓库没有操作权限后依旧显示相应的最近活动 [#2148](https://github.com/gogits/gogs/issues/2148)
- 反向代理子路径下的工单（Issue）引用链接不正确 [#2229](https://github.com/gogits/gogs/issues/2229)
- Email 中的换行符没用使用 HTML 格式 [#2332](https://github.com/gogits/gogs/issues/2332)
- 较长的 Web 钩子 URL 被强行截断 [#2465](https://github.com/gogits/gogs/issues/2465)
- 存在 Slack 类型的多个 Web 钩子会发送错误的推送信息 [#2485](https://github.com/gogits/gogs/issues/2485)
- 图片 URL 包含空格时无法显示 [#2556](https://github.com/gogits/gogs/issues/2556)
- 在转移仓库所有权后修改 Wiki 页面发生错误 [#2558](https://github.com/gogits/gogs/issues/2558)
- 删除用户后访问版本发布页面发生错误 [#2596](https://github.com/gogits/gogs/issues/2596)
- Web 钩子的 `avatar_url` 字段值不正确 [#2630](https://github.com/gogits/gogs/issues/2630)

#### 功能改进

- 支持在安装页面配置日志路径 [#691](https://github.com/gogits/gogs/issues/691)
- 在 Web 钩子的仓库对象中增加 `default_branch` 字段 [#1059](https://github.com/gogits/gogs/issues/1059)
- 增加显示关闭和重启工单的最近活动 [#1821](https://github.com/gogits/gogs/issues/1821)
- 允许派生镜像仓库 [#2505](https://github.com/gogits/gogs/issues/2505)
- 在工单页面高亮代码块 [#2538](https://github.com/gogits/gogs/pull/2538)

#### 新增特性

- 支持通过配置选项 `[markdown] CUSTOM_URL_SCHEMES` 来允许 Markdown 渲染自定义的 URL 协议 [#2406](https://github.com/gogits/gogs/pull/2406)
- 支持在文件差异对比（Diff）页面显示代码高亮 [#2528](https://github.com/gogits/gogs/pull/2528)
- 支持将镜像仓库转换为普通类型的仓库 [#2607](https://github.com/gogits/gogs/issues/2607)

### v0.8.25 @ 2016-01-30

#### Bug 修复

- 当合并请求（Pull Request）的发起者为组织时无法修改分支 [#2014](https://github.com/gogits/gogs/issues/2014)
- 目录中显示重复的文件名 [#2254](https://github.com/gogits/gogs/issues/2254)
- 重命名组织后重定向到错误的 URL [#2268](https://github.com/gogits/gogs/issues/2268) 
- HTML 页面在原始模式浏览时被渲染 [#2283](https://github.com/gogits/gogs/issues/2283) 
- 允许访问空仓库的非首页页面 [#2345](https://github.com/gogits/gogs/issues/2345) 
- 访问授权认证有关的页面时发生错误 [#2349](https://github.com/gogits/gogs/issues/2349)
- 无法处理以 ':' 开头的文件名 [#2373](https://github.com/gogits/gogs/issues/2373)

#### 功能改进

- 允许通过配置选项 `[server] SSH_ROOT_PATH` 来指定 `authorized_keys` 文件所在的目录 [#1436](https://github.com/gogits/gogs/issues/1436)
- 控制面板的代码提交 ID 使用等宽字体 [#2264](https://github.com/gogits/gogs/issues/2264)
- 仓库名称过长时进行截断 [#2287](https://github.com/gogits/gogs/issues/2287)

#### 新增特性

- 支持 GitHub 风格的 Markdown 检查列表 [#1048](https://github.com/gogits/gogs/issues/1048) 
- 开放更多 API 接口：操作用户关注者 [#1692](https://github.com/gogits/gogs/issues/1692) 
- 支持分列文件差异对比 [#1925](https://github.com/gogits/gogs/issues/1925) [#2296](https://github.com/gogits/gogs/issues/2296) 
- 支持行内差异高亮显示 [#2335](https://github.com/gogits/gogs/issues/2335)

### v0.8.10 @ 2015-12-18

#### Bug 修复

- 在 Windows 下无法识别 Git 版本 [#2167](https://github.com/gogits/gogs/issues/2167)
- 火狐下无法预览 Wiki [#2176](https://github.com/gogits/gogs/issues/2176)
- 使用 PostgreSQL 作为数据库时无法正常浏览仓库的关注者和称赞者 [#2176](https://github.com/gogits/gogs/issues/2176)
- 无法检测正确的文件编码 [#2185](https://github.com/gogits/gogs/issues/2185) 
- 超大文件差异对比导致无响应
- 无法处理非代码提交（Commit）关联的标签（Tag）
- 组织控制面板的最近活动出现串号显示 [#2223](https://github.com/gogits/gogs/issues/2223) 

#### 新增特性

- 开放更多 API 接口：操作用户邮箱、管理组织 [#1692](https://github.com/gogits/gogs/issues/1692) 

### v0.7.33 @ 2015-12-06

#### Bug 修复

- LDAP 搜索非 ASCII 字符失败 [#1139](https://github.com/gogits/gogs/issues/1139) 
- 删除仓库时未移除相应的称赞数据 [#2042](https://github.com/gogits/gogs/issues/2042) 
- 当文件差异存在超级长的一行时无法完整显示 [#2071](https://github.com/gogits/gogs/issues/2071)
- 无法在 Windows 下创建合并请求（Pull Request）[#2093](https://github.com/gogits/gogs/issues/2093) 

#### 功能改进

- 允许禁用仓库的 Wiki/工单（Issue）/合并请求（Pull Request）功能 [#1829](https://github.com/gogits/gogs/issues/1829) 
- 允许通过 Web 界面触发测试 Web 钩子 [#1857](https://github.com/gogits/gogs/issues/1857) 
- 允许批量删除系统提示 [#2052](https://github.com/gogits/gogs/issues/2052) 
- 允许在管理员面板删除指定仓库 [#2063](https://github.com/gogits/gogs/issues/2063) 

#### 新增特性

- 新增仓库 Wiki 支持 [#270](https://github.com/gogits/gogs/issues/270) 
- 支持工单链接生成相应的外部链接 [#890](https://github.com/gogits/gogs/issues/890) 
- 开放更多 API 接口：操作用户公钥 [#976](https://github.com/gogits/gogs/issues/976) 

**更早的变更日志可以在 [GitHub](https://github.com/gogits/gogs/releases?after=v0.7.22) 上找到。**
