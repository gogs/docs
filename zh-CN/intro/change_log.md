---
name: 变更日志
---

# 变更日志

### 未发布

#### 新增特性

- 允许管理员将用户从仓库的关注列表中移除 [#5803](https://github.com/gogs/gogs/pull/5803)
- 下载仓库原始内容时设置 `Last-Modified` HTTP 头信息 [#5811](https://github.com/gogs/gogs/issues/5811)
- 支持 SAS 代码文件的语法高亮（`.r`、`.sas`、`.tex`、`.yaml`）[#5856](https://github.com/gogs/gogs/pull/5856)

#### 功能修改

#### Bug 修复

- [安全] 镜像仓库存在潜在的远程代码执行的威胁 [#5767](https://github.com/gogs/gogs/issues/5767)
- 禁止个人令牌使用相同的名称 [#5587](https://github.com/gogs/gogs/issues/5587) [#5820](https://github.com/gogs/gogs/pull/5820)
- 使用联合头像查找（Federated Avatar Lookup）功能时可能会导致程序崩溃 [#5848](https://github.com/gogs/gogs/issues/5848)

#### 其它变更

### 0.11.91 @ 2019-08-11

#### Bug 修复

- MySQL: 无效的连接 [#5532](https://github.com/gogs/gogs/issues/5532)
- Docker: 弃用的 OpenSSH 选项提示 [#5647](https://github.com/gogs/gogs/issues/5647)
- 版权年份过时 [#5674](https://github.com/gogs/gogs/issues/5674)
- [安全] 无效的 API 权限控制 [#5764](https://github.com/gogs/gogs/issues/5764)

#### 功能改进

- 工单的被指派人能够收到邮件更新 [#4220](https://github.com/gogs/gogs/issues/4220)
- 在邮件中渲染 Markdown [#4552](https://github.com/gogs/gogs/issues/4552)
- 添加 `rsync` 到 Docker 镜像 [#5773](https://github.com/gogs/gogs/pull/5773)

### 0.11.86 @ 2019-01-30

#### Bug 修复

- Linux 下 Firefox 显示问题 [#5299](https://github.com/gogs/gogs/issues/5299)
- 使用外部工单系统时出现非预期的工单索引解析错误 [#5551](https://github.com/gogs/gogs/issues/5551)
- [安全] 远程代码执行和潜在的拒绝服务攻击 [#5558](https://github.com/gogs/gogs/issues/5558)

#### 新增特性

- 支持使用 GitHub（企业版）作为认证源 [#5340](https://github.com/gogs/gogs/pull/5340)
- 添加获取提交信息（Commit）详情的 API [#5546](https://github.com/gogs/gogs/pull/5546)

#### 其它变更

- 添加新语种支持：越南语

### 0.11.79 @ 2018-12-11

#### Bug 修复

- 在 LDAP 中使用 dn 作为用户查询属性时无效 [#4684](https://github.com/gogs/gogs/issues/4684)
- LDAP 组验证失败 [#4792](https://github.com/gogs/gogs/issues/4792)
- Emoji 在 Wiki 中无法显示 [#4869](https://github.com/gogs/gogs/issues/4869)
- 配置中的日志级别不生效 [#5007](https://github.com/gogs/gogs/issues/5007)
- 使用非 80 端口访问实例时无法使用 `go get` 命令下载 [#5305](https://github.com/gogs/gogs/issues/5305)
- 修复 API 路由中潜在的 CSRF 漏洞 [#5355](https://github.com/gogs/gogs/issues/5355)
- 若分支名称包含 `#` 则在更新保护分支设置后重定向到错误的地址 [#5442](https://github.com/gogs/gogs/issues/5442)
- 清除标签无法生效 [#5445](https://github.com/gogs/gogs/issues/5445)
- [安全] 远程代码执行 [#5469](https://github.com/gogs/gogs/issues/5469)
- 新的分支拉取到镜像仓库后，没有触发推送事件的 Web 钩子 [#5473](https://github.com/gogs/gogs/issues/5473)
- 过长的工单评论会超出控制面板的宽度 [#5502](https://github.com/gogs/gogs/issues/5502)
- 协作者 API 没有显示对应权限 [#5538](https://github.com/gogs/gogs/issues/5538)
- [安全] 登出仅删除客户端 Cookie [#5540](https://github.com/gogs/gogs/issues/5540)
- [安全] 部分路由需要使用 POST 请求 [#5541](https://github.com/gogs/gogs/issues/5541)
- [安全] 外部工单系统 URL 格式链接存在 XSS 漏洞 [#5545](https://github.com/gogs/gogs/issues/5545)

#### 功能改进

- 支持使用 URL 查询参数自动填充新工单的标题和内容 [#5302](https://github.com/gogs/gogs/issues/5302)
- 支持在 Markdown 中使用 Base64 编码的图像 [#5391](https://github.com/gogs/gogs/pull/5391)
- 允许未登录用户调用仓库信息 API `/repos/:username/:reponame` [#5475](https://github.com/gogs/gogs/issues/5475)

### 0.11.66 @ 2018-09-16

#### Bug 修复

- Web 编辑器提交后无法触发 Git 钩子 [#4338](https://github.com/gogs/gogs/issues/4338)
- 版本发布附件会由于删除任意评论而被清空 [#4627](https://github.com/gogs/gogs/issues/4627)
- 可公开访问的 Wiki 或工单的私有仓库无法在搜索结果中显示 [#4973](https://github.com/gogs/gogs/issues/4973)
- 无法连接 MySQL 8.0 [#5187](https://github.com/gogs/gogs/issues/5187)
- 删除仓库时未清理 Web 钩子和相关任务 [#5229](https://github.com/gogs/gogs/issues/5229)
- 恢复备份后时间戳全部变为当前时间 [#5264](https://github.com/gogs/gogs/issues/5264)
- 合并请求后删除分支没有触发 Web 钩子 [#5331](https://github.com/gogs/gogs/issues/5331)
- 派生仓库时没有检查用户仓库数量限制 [#5345](https://github.com/gogs/gogs/issues/5345)
- 使用 PostgreSQL 时无法删除用户 [#5376](https://github.com/gogs/gogs/issues/5376)

#### 新增特性

- 支持为仓库添加头像 [#2340](https://github.com/gogs/gogs/issues/2340)
- 增加由 Prometheus 提供的基本 Go Runtime 运行信息 [#4141](https://github.com/gogs/gogs/issues/4141)

#### 功能改进

- 默认忽略配置文件的行内注释
- 浏览文件时剔除文件末的空行 [#5270](https://github.com/gogs/gogs/pull/5270)
- 支持设定默认的用户认证方式 [#5274](https://github.com/gogs/gogs/issues/5274)
- 支持添加自定义合并提交描述 [#5276](https://github.com/gogs/gogs/pull/5276)

#### 其它变更

- 安全漏洞修复

### 0.11.53 @ 2018-06-05

#### Bug 修复

- 分支名包含 `#` 时无法进行正常操作 [#4601](https://github.com/gogs/gogs/issues/4601)
- 尖括号中间的工单编号没有被渲染 [#4706](https://github.com/gogs/gogs/issues/4706)
- 当基准分支不是默认分支时无法进行请求合并 [#5138](https://github.com/gogs/gogs/issues/5138)
- 生成的 Gravatar 链接不正确 [#5157](https://github.com/gogs/gogs/issues/5157)
- 允许重复使用相同的二步验证令牌
- 配置选项 `[git] GC_ARGS` 无法生效

#### 新增特性

- 在活动时间线显示镜像仓库更新 [#2017](https://github.com/gogs/gogs/issues/2017)
- 支持通过本地文件加载认证源 [#3142](https://github.com/gogs/gogs/issues/3142)
- 镜像同步后触发 Web 钩子 [#4528](https://github.com/gogs/gogs/issues/4528)

#### 其它变更

- 将导入路径从 "gogits/gogs" 修改为 "gogs/gogs"
- 安全漏洞修复
- 添加新语种支持：葡萄牙语

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

**更早的变更日志可以在 [GitHub](https://github.com/gogs/gogs/releases?after=v0.11.33) 上找到。**
