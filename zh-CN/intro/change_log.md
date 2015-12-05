---
name: 变更日志
---

# 变更日志

### v0.8.0（未发布）

#### Bug 修复

- LDAP 搜索非 ASCII 字符失败 [#1139](https://github.com/gogits/gogs/issues/1139) 
- 删除仓库时未移除相应的称赞数据 [#2042](https://github.com/gogits/gogs/issues/2042) 
- 无法在 Windows 下创建合并请求（Pull Request）[#2093](https://github.com/gogits/gogs/issues/2093) 

#### 功能改进

- 允许禁用仓库的 Wiki/工单（Issue）/合并请求（Pull Request）功能 [#1829](https://github.com/gogits/gogs/issues/1829) 

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

#### 其它变更

- 开启在线论坛 http://forum.gogs.io/

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

**更早的变更日志可以在 [GitHub](https://github.com/gogits/gogs/releases) 上找到。**
