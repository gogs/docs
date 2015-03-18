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

- Web 框架：[Macaron](https://github.com/Unknwon/macaron)
- UI 框架：[Semantic UI](http://semantic-ui.com/) + [GitHub Octicons](https://octicons.github.com/) + [Font Awesome](http://fontawesome.io/)
- ORM：[Xorm](https://github.com/go-xorm/xorm)
- 数据库驱动：[github.com/go-sql-driver/mysql](https://github.com/go-sql-driver/mysql) + [github.com/lib/pq](https://github.com/lib/pq) + [github.com/mattn/go-sqlite3](https://github.com/mattn/go-sqlite3)

