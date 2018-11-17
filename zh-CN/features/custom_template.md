---
name: 自定义模板
---

# 自定义模板

您可以不需要修改仓库源码就能注入自定义头部和尾部内容，这对添加分析代码和自定义静态资源非常有用。

了解更多有关 [注入自定义头部和尾部](https://discuss.gogs.io/t/how-to-inject-custom-head-and-footer/943)。

## 添加自定义 CSS 文件

这里展示如何为您的 Gogs 实例添加自定义 CSS 文件，目录和文件名都是为了方便演示，您可以把文件放在任何能够通过网络访问的目录。

1. 在 `public/css` 目录下创建一个名为 `custom.css` 的文件
2. 向文件中添加一些 CSS 规则
3. 编辑 `custom/templates/inject/head.tmpl` 文件并添加一行内容 `<link rel="stylesheet" href="/css/custom.css">`
4. 重启 Gogs
5. 后续对自定义 CSS 文件的编辑不需要重启 Gogs

# 自定义首页

首页内容属于仓库源码，首页修改不包括自定义头部和尾部内容。

## 修改首页内容

首页源码位置 `templates/home.tmpl`

1. 保留该文件的头部和尾部引用
注意保留：头：{{template "base/head" .}}，尾：{{template "base/footer" .}}
2. 编辑自定义首页中间部分 `templates/home.tmpl`
4. 重启 Gogs
