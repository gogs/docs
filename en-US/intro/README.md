---
root: true
name: Introduction
sort: 0
---

# What is Gogs?

Gogs(Go Git Service) is a Self Hosted Git Service in the Go Programming Language. 

## Purpose

Since we choose to use pure Go implementation of Git manipulation, Gogs certainly supports **ALL platforms**  that Go supports, including Linux, Mac OS X, and Windows with **ZERO** dependency. 

More importantly, Gogs only needs one binary to setup your own project hosting on the fly!

## Requirements

- Web Framework: [github.com/go-martini/martini](https://github.com/go-martini/martini)
- UI Framework: [TODC Bootstrap](http://todc.github.io/todc-bootstrap/) + [Font Awesome](http://fontawesome.io/)
- ORM: [github.com/lunny/xorm](https://github.com/lunny/xorm)
- Database Driver: [github.com/go-sql-driver/mysql](https://github.com/go-sql-driver/mysql) or [github.com/lib/pq](https://github.com/lib/pq) or [github.com/mattn/go-sqlite3](https://github.com/mattn/go-sqlite3)

## Directory Structure

- `/conf` - configuration files
 - `/content` - global content
 - `/gitignore` - .gitignore files for supported languages
 - `/license` - license files for supported licenses
- `/models` -  business logics
- `/modules` - helper modules
 - `/auth` - authorization and forms
 - `/avatar` - avatar cache service
 - `/base` - base functions and types
 - `/cron` - cron tasks
 - `/log` - log wrapper of gogits/log
 - `/mailer` - mail service
 - `/middleware` - custom middlewares  
- `public`   -  static web elements: CSS, JS, images, fonts
- `routers` - controller logics
- `templates`    -  web templates
