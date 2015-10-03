---
root: true
name: Introduction
sort: 0
---

# What is Gogs?

Gogs (Go Git Service) is a painless self-hosted Git Service written in Go.

## Purpose

The goal of this project is to make the easiest, fastest, and most painless way of setting up a self-hosted Git service. With Go, this can be done with an independent binary distribution across **ALL platforms** that Go supports, including Linux, Mac OS X, and Windows.

## Basic Requirements

- Web Framework: [Macaron](https://github.com/Unknwon/macaron)
- UI Framework: [Semantic UI](http://semantic-ui.com/) + [GitHub Octicons](https://octicons.github.com/) + [Font Awesome](http://fontawesome.io/)
- ORM: [Xorm](https://github.com/go-xorm/xorm)
- Database Driver: [github.com/go-sql-driver/mysql](https://github.com/go-sql-driver/mysql) + [github.com/lib/pq](https://github.com/lib/pq) + [github.com/mattn/go-sqlite3](https://github.com/mattn/go-sqlite3)
