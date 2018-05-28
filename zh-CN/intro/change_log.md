---
name: 变更日志
---

# 变更日志

### 未发布

#### Bug 修复

- 分支名包含 `#` 时无法进行正常操作 [#4601](https://github.com/gogs/gogs/issues/4601)
- 尖括号中间的工单编号没有被渲染 [#4706](https://github.com/gogs/gogs/issues/4706)
- 当基准分支不是默认分支时无法进行请求合并 [#5138](https://github.com/gogs/gogs/issues/5138)
- 生成的 Gravatar 链接不正确 [#5157](https://github.com/gogs/gogs/issues/5157)
- 允许重复使用相同的二步验证令牌

#### 新增特性

- 支持通过本地文件加载认证源 [#3142](https://github.com/gogs/gogs/issues/3142)

#### 其它变更

- 将导入路径从 "gogs/gogs" 修改为 "gogs/gogs"
- 安全漏洞修复
- 添加新语种支持：越南语

### 0.11.43 @ 2018-03-31

#### Bug 修复

- 保护分支可以在完成合并请求后被删除 [#4514](https://github.com/gogs/gogs/issues/4514)
- 不支持 MSSQL 数据库的 SYSNAME 字段类型 [#4642](https://github.com/gogs/gogs/issues/4642)
- 仓库快速开始页面只有仓库管理员可见 [#4646](https://github.com/gogs/gogs/issues/4646)
- 分支页面名称包含 `#` 的分支链接错误 [#4874](https://github.com/gogs/gogs/issues/4874)
- 在合并提交时使用衍合导致合并失效 [#5051](https://github.com/gogs/gogs/issues/5051)
- 分支一旦被设置为保护后，加锁标志在取消保护后也不消失 [#5053](https://github.com/gogs/gogs/issues/5053)
- IPython Notebook 中的 SVG 支持 [#5077](https://github.com/gogs/gogs/issues/5077)

#### 功能改进

- 支持 HTTP HEAD 请求 [#2857](https://github.com/gogs/gogs/issues/2857)
- 添加配置选项以允许在启动时重写 authorized_keys 文件 [#4435](https://github.com/gogs/gogs/issues/4435)
- 添加配置选项以设置邮件的全局主题前缀 [#4524](https://github.com/gogs/gogs/issues/4524)
- 默认禁用联合头像查找 [#5126](https://github.com/gogs/gogs/pull/5126)

#### 其它变更

- 添加新语种支持：印度尼西亚语、波斯语

### 0.11.34 @ 2017-11-22

#### Bug 修复

- *回退*：跨仓库合并请求无法正常工作 [#4890](https://github.com/gogs/gogs/issues/4890)

### 0.11.33 @ 2017-11-19

#### Bug 修复

- 部分安全修复
- 合并请求后发送的 Web 钩子推送内容包含错误的提交 ID [#4442](https://github.com/gogs/gogs/issues/4442)
- HTML 标签 go-import 未响应正确的值 [#4832](https://github.com/gogs/gogs/issues/4832)

#### 新增特性

- 添加钉钉 Web 钩子支持 [#4773](https://github.com/gogs/gogs/pull/4773)
- 支持合并请求前先进行衍合操作 [#4798](https://github.com/gogs/gogs/issues/4798)

#### 功能改进

- 在 LDAP BindDN 中支持使用 '%s' 作为用户名占位符 [#2526](https://github.com/gogs/gogs/issues/2526)
- 允许通过环境变量指定 Docker 容器内 git 用户的 UID [#3520](https://github.com/gogs/gogs/issues/3520)
- 添加仓库设置以便在检查合并请求冲突时忽略空白符的差异 [#4834](https://github.com/gogs/gogs/issues/4834)

#### 其它变更

- 添加新语种支持：斯洛伐克语

### 0.11.29 @ 2017-08-15

#### Bug 修复

- 如果仓库曾经为公开的，则变为私有后相关活动信息未被设为私有 [#4414](https://github.com/gogs/gogs/issues/4414)
- Web 钩子不接受 IPv6 URL [#4428](https://github.com/gogs/gogs/issues/4428)
- 通过代码提交关闭工单后没有发送邮件提醒 [#4430](https://github.com/gogs/gogs/issues/4430)
- 探索页面分页不正确 [#4441](https://github.com/gogs/gogs/issues/4441)
- `/api/v1/repos/search` 返回空值 [#4522](https://github.com/gogs/gogs/issues/4522)
- 创建合并请求完成后发生错误 [#4572](https://github.com/gogs/gogs/issues/4572)

### 0.11.19 @ 2017-06-10

#### Bug 修复

- 无法使用 go get 子包 [#1878](https://github.com/gogs/gogs/issues/1878)
- 非首次使用 LDAP 登录无法更新用户为管理员 [#2855](https://github.com/gogs/gogs/issues/2855)
- 使用 PAM 登录时发生错误 [#4216](https://github.com/gogs/gogs/issues/4216)
- PostgreSQL 恢复备份后出现错误 `unique constraint violation` [#4357](https://github.com/gogs/gogs/issues/4357)
- IPython notebook 的图片无法显示 [#4366](https://github.com/gogs/gogs/issues/4366)
- 编辑文件预览时无法正确处理图片相对链接 [#4368](https://github.com/gogs/gogs/issues/4368)
- 提交历史页面无法渲染 Emoji [#4439](https://github.com/gogs/gogs/issues/4439)
- 查看包含文件权限更改的单个提交时 CPU 异常高 [#4475](https://github.com/gogs/gogs/issues/4475)
- 无法修改协作者的权限 [#4512](https://github.com/gogs/gogs/issues/4512)

#### 新增特性

- 支持两步验证登录 [#945](https://github.com/gogs/gogs/issues/945)
- 支持 LDAP 登录时验证组成员身份 [#4398](https://github.com/gogs/gogs/pull/4398)

#### 功能改进

- 安装页面检查 SMTP 地址中是否包含端口号 [#2243](https://github.com/gogs/gogs/issues/2243)
- 镜像仓库没有拉取新代码提交时不更新最后更新时间 [#4341](https://github.com/gogs/gogs/issues/4341)
- 支持 IPython Notebook 形式的 README [#4367](https://github.com/gogs/gogs/issues/4367)
- 支持自定义 TLS 相关配置 [#4450](https://github.com/gogs/gogs/issues/4450)

### 0.11.4 @ 2017-04-05

#### Bug 修复

- 在进行 HTTP/HTTPS 推送和拉取时客户端没有提示用户输入凭据
- 镜像用户凭据没有进行 URL 编码 [#4014](https://github.com/gogs/gogs/issues/4014)
- 仓库禁用合并请求时，发起合并请求按钮仍旧在分支页面显示 [#4377](https://github.com/gogs/gogs/issues/4377)
- 用户在安装页面发生验证错误时应用会崩溃 [#4383](https://github.com/gogs/gogs/issues/4383) 

### 0.11 @ 2017-04-03

#### Bug 修复

- 编辑个人信息发生验证错误时丢失内容 [#1123](https://github.com/gogs/gogs/issues/1123)
- 组织控制面板显示错误的仓库统计 [#4351](https://github.com/gogs/gogs/issues/4351)
- 从 0.10 之前的版本自动迁移失败 [#4355](https://github.com/gogs/gogs/issues/4355)
- 允许公开访问工单的私有仓库没有正确处理匿名访问 [#4359](https://github.com/gogs/gogs/issues/4359)

**更早的变更日志可以在 [GitHub](https://github.com/gogs/gogs/releases?after=v0.11) 上找到。**
