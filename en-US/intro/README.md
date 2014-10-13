---
root: true
name: Introduction
sort: 0
---

# What is Gogs?

Gogs(Go Git Service) is a painless self-hosted Git Service written in Go.

## Purpose

The goal of this project is to make the easiest, fastest and most painless way to set up a self-hosted Git service. With Go, this can be done in independent binary distribution across **ALL platforms** that Go supports, including Linux, Mac OS X, and Windows.

## Requirements

- Web Framework: [github.com/Unknwon/macaron](https://github.com/Unknwon/macaron)
- UI Framework: [GitHub Octicons](https://octicons.github.com/) + [Font Awesome](http://fontawesome.io/)
- ORM: [github.com/go-xorm/xorm](https://github.com/go-xorm/xorm)
- Database Driver: [github.com/go-sql-driver/mysql](https://github.com/go-sql-driver/mysql) or [github.com/lib/pq](https://github.com/lib/pq) or [github.com/mattn/go-sqlite3](https://github.com/mattn/go-sqlite3)

## Directory Structure

```
cmd/								// commands
conf/								// configuration
  |__ content/						// global content
  |__ gitignore/		
  |__ license/				
  |__ locale/						// i18n locales
etc/
models/								// business logic
modules/							// helper modules
  |__ auth/							// auth forms
  |__ avatar/						// gravatar service
  |__ base/							// common functions and types
  |__ captcha/							
  |__ cron/						
  |__ git/							// git shell
  |__ httplib/						// HTTP helpers
  |__ log/					 
  |__ mailer/						
  |__ middleware/						
  |__ process/						// process manager
  |__ setting/						// app settings
  |__ social/						// OAuth2
  |__ ssh/							// SSH server(prototype)
  |__ uuid/							
public/								// static web elements
routers/							// controller logic
scripts/							// helper scripts
templates/								
```
