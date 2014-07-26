---
root: true
name: 简介
sort: 0
---

# 什么是 Gogs?

Gogs(Go Git Service) 是一个基于 Go 语言的自助 Git 服务。

## 开发目的

Gogs 的目标是打造一个最简单、最快速和最轻松的方式搭建自助 Git 服务。使用 Go 语言开发使得 Gogs 能够通过独立的二进制分发，并且支持 Go 语言支持的 **所有平台**，包括 Linux、Mac OS X 以及 Windows。

## 项目设计

- Web 框架：[github.com/Unknwon/macaron](https://github.com/Unknwon/macaron)
- UI 框架：[GitHub Octicons](https://octicons.github.com/) + [Font Awesome](http://fontawesome.io/)
- ORM：[github.com/go-xorm/xorm](https://github.com/go-xorm/xorm)
- 数据库驱动：[github.com/go-sql-driver/mysql](https://github.com/go-sql-driver/mysql) or [github.com/lib/pq](https://github.com/lib/pq) or [github.com/mattn/go-sqlite3](https://github.com/mattn/go-sqlite3)

## 项目结构

```
cmd/								// 命令文件
conf/								// 配置文件
  |__ content/						// 全局文件
  |__ gitignore/		
  !__ license/				
  |__ locale/						// i18n 本地化文件
         |__ locale_en-US.ini
         |__ locale_zh-CN.ini
etc/
models/								// 业务逻辑
modules/							// 辅助模块
  |__ auth/							// 表单验证
  |__ avatar/						// Gravatar 服务
  |__ base/							// 常用函数和类型
  |__ captcha/							
  |__ cron/						
  |__ git/							// Git Shell
  |__ httplib/						// HTTP 辅助模块
  |__ log/					 
  |__ mailer/						
  |__ middleware/						
  |__ process/						// 进程管理
  |__ setting/						// 应用设置
  |__ social/						// OAuth2
  |__ ssh/							// SSH 服务器（原型）
  |__ uuid/							
public/								// 静态资源
routers/							// 控制器逻辑
scripts/							// 辅助脚本
templates/								
```
