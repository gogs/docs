---
name: 自定义模板
---

# 自定义模板

## 重载 HTML 模板

用户可以通过在 `custom/templates/` 目录下创建一个自定义版本的副本实现 HTML 模板重载（包括邮件模板），该文件不会因为版本升级而受到影响，但可以会因为改动过大导致与后续版本不兼容。

例如，可以通过以下步骤自定义站点首页：

1. 复制模板文件 `templates/home.tmpl` 的内容
2. 将修改保存到文件 `custom/templates/home.tmpl`

:warning: 所有针对自定义模板的修改都**需要重启 Gogs 实例**

:warning: 当用户配置 `[server] LOAD_ASSETS_FROM_DISK = true` 时，邮件模板无法被重载

## 重载静态文件

用户可以通过在 `custom/public/` 目录下创建一个自定义版本的副本实现静态文件重载（CSS、JavaScript、图片等等），该文件不会因为版本升级而受到影响，但可以会因为改动过大导致与后续版本不兼容。

例如，可以通过保存自定义图标到 `custom/public/img/favicon.png` 实现站点图标的重载。

:warning: 所有针对自定义静态文件的修改都**不需要重启 Gogs 实例**

## 注入自定义内容到模板中

您可以不需要修改仓库源码就能注入自定义头部和尾部内容，这对添加分析代码和自定义静态资源非常有用。

了解更多有关 [注入自定义头部和尾部](https://discuss.gogs.io/t/how-to-inject-custom-head-and-footer/943)。

在条件允许的情况下，尽可能使用该方案以减少对模板渲染的影响。

### 注入自定义 CSS 文件

这里展示如何为您的 Gogs 实例添加自定义 CSS 文件，目录和文件名都是为了方便演示，您可以把文件放在任何能够通过网络访问的目录。

1. 在 `custom/public/css/` 目录下创建一个名为 `custom.css` 的文件
2. 向文件中添加一些 CSS 规则
3. 编辑 `custom/templates/inject/head.tmpl` 文件并添加一行内容 `<link rel="stylesheet" href="/css/custom.css">`
4. 重启 Gogs
5. 后续对自定义 CSS 文件的编辑**不需要重启 Gogs 实例**
