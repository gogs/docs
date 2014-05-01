---
root: true
name: 简介
sort: 0
---

# 什么是 Gogs?

Gogs(Go Git Service) 是一个由 Go 语言编写的自助 Git 托管服务。

## 开发目的

Gogs 完全使用 Go 语言来实现对 Git 数据的操作，实现 **零** 依赖，并且支持 Go 语言所支持的 **所有平台**，包括 Linux、Mac OS X 以及 Windows。

更重要的是，您只需要一个可执行文件就能借助 Gogs 快速搭建属于您自己的代码托管服务！

## 项目设计

- Web 框架：[github.com/codegangsta/martini](https://github.com/codegangsta/martini)
- UI 框架：[TODC Bootstrap](http://todc.github.io/todc-bootstrap/) + [Font Awesome](http://fontawesome.io/)
- ORM：[github.com/lunny/xorm](https://github.com/lunny/xorm)
- 数据库驱动：[github.com/go-sql-driver/mysql](https://github.com/go-sql-driver/mysql) or [github.com/lib/pq](https://github.com/lib/pq) or [github.com/mattn/go-sqlite3](https://github.com/mattn/go-sqlite3)

## 项目结构

- `/conf` - 配置文件
 - `/content` - 全局文档
 - `/gitignore` - .gitignore 文件
 - `/license` - 版权文件
- `/models` -  业务逻辑
- `/modules` - 协助模块
 - `/auth` - 表单授权
 - `/avatar` - 头像缓存服务
 - `/base` - 基本函数与类型
 - `/cron` - cron 任务
 - `/log` - gogits/log 的封装
 - `/mailer` - 邮件服务
 - `/middleware` - 自定义中间件
- `public`   -  CSS、JS、images 和 fonts 等静态资源
- `routers` - 控制器逻辑
- `templates` - 模板文件
