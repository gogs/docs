---
name: 变更日志
---

# 变更日志

### v0.8.x（未发布）

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

### v0.8.0 @ 2015-12-13

#### Bug 修复

- 无法推送像 Linux Kernel 这么多代码提交（Commit）的仓库 [#279](https://github.com/gogits/gogs/issues/279) 
- SMTP 授权认证未完全遵循协议规定 [#2152](https://github.com/gogits/gogs/issues/2152) 

#### 功能改进

- 当有新的合并请求提交时发送邮件提醒 [#1612](https://github.com/gogits/gogs/issues/1612) 
- 如果在安装页面设置了管理员，完成安装后自动登录 [#1627](https://github.com/gogits/gogs/issues/1627) 
- 禁止非本地类型的用户修改用户名和密码 [#1374](https://github.com/gogits/gogs/issues/1374)  [#1938](https://github.com/gogits/gogs/issues/1938) [#2154](https://github.com/gogits/gogs/issues/2154) 
- 允许自定义 `git fsck` 的超时设置 [#1943](https://github.com/gogits/gogs/issues/1943) 
- 在仓库页面显示和编辑镜像的地址 [#1984](https://github.com/gogits/gogs/issues/1984) 
- 不在活动线中显示工单（Issue）的内容 [#2029](https://github.com/gogits/gogs/issues/2029)
- 在差异对比页面显示作者的邮箱 [#2035](https://github.com/gogits/gogs/issues/2035) 
- 允许修改仓库的镜像源地址
- 控制面板增加 “创建新的镜像” 按钮 [#2037](https://github.com/gogits/gogs/issues/2037) 
- 允许使用外部 Wiki 链接 [#2114](https://github.com/gogits/gogs/issues/2114)

#### 新增特性

- 允许限制每个用户的最大允许创建仓库数 [#1575](https://github.com/gogits/gogs/issues/1575) 
- 允许在代码提交页面直接切换分支 [#1846](https://github.com/gogits/gogs/issues/1846) 

#### 其它变更

- 停止支持 `0.5.x` 系列版本，最低要求的自动迁移版本为 `0.6.0`

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

### v0.7.22 @ 2015-11-25

#### Bug 修复

- Markdown 存在双层嵌套链接时发生 panic [#2019](https://github.com/gogits/gogs/issues/2019) 
- 内置 SSH 服务器在 Windows 无法工作

#### 功能改进

- 组织首页 URL 去除 `org/` 前缀 [#1944](https://github.com/gogits/gogs/issues/1944) 
- 更多 Git 钩子的原生支持

#### 其它变更

- 所有页面均以使用全新的 Semantic UI [#650](https://github.com/gogits/gogs/issues/650)

### v0.7.19 @ 2015-11-21

#### Bug 修复

- 坑爹的代码高亮 [#670](https://github.com/gogits/gogs/issues/670) [#1315](https://github.com/gogits/gogs/issues/1315) [#1549](https://github.com/gogits/gogs/issues/1549) [#1712](https://github.com/gogits/gogs/issues/1712)
- 坑爹的复制链接按钮 [#1168](https://github.com/gogits/gogs/issues/1168) [#1396](https://github.com/gogits/gogs/issues/1396) 
- 坑爹的下载源码 UI [#1668](https://github.com/gogits/gogs/issues/1668)
- 合并请求（Pull Request）不支持 BIN 格式的差异对比 [#1922](https://github.com/gogits/gogs/issues/1922)
- 测试补丁（Patch）时未检出正确的基准分支 [#1931](https://github.com/gogits/gogs/issues/1931) 
- 分支和标签选择列表的 z-index 值错误 [#1942](https://github.com/gogits/gogs/issues/1942) 
- 文件内容浏览页面无法正确显示巨型图片
- 管理员创建的帐户注册通知邮件中未提供登录 URL [#1979](https://github.com/gogits/gogs/issues/1979) 
- 仓库描述在派生完成之后未真正同步 [#1981](https://github.com/gogits/gogs/issues/1981) 
- 派生仓库在修改设置时会自动修改可见性 [#1987](https://github.com/gogits/gogs/issues/1987) 

#### 功能改进

- 控制面板的协作仓库根据最后更新时间排序 [#1302](https://github.com/gogits/gogs/issues/1302) 
- 支持删除某个版本发布 [#1383](https://github.com/gogits/gogs/issues/1383) 
- 在 Web 界面先修改默认分支时同时修改 Git 仓库的相应值 [#1742](https://github.com/gogits/gogs/issues/1742)
- 在活动线显示工单（Issue）的标题和内容 [#1854](https://github.com/gogits/gogs/issues/1854) 
- 在活动线的推送代码列表中显示可用的自定义头像
- 允许使用配置选项 `[other] SHOW_FOOTER_VERSION = true` 来禁止在非管理员页面的页脚显示版本信息 [#1957](https://github.com/gogits/gogs/issues/1957) 

#### 新增特性

- 管理员允许浏览和修改私有仓库的设置 [#493](https://github.com/gogits/gogs/issues/493) [#1401](https://github.com/gogits/gogs/issues/1401) 

**更早的变更日志可以在 [GitHub](https://github.com/gogits/gogs/releases?after=v0.7.19) 上找到。**
