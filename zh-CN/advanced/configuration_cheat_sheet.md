---
name: 配置文件手册
sort: 1
---

# 配置文件手册

This is a cheat sheet for Gogs configuration file, it helps some if you want to fully understand how it powers Gogs.

Before we get started, make sure you know any change of configuration should be made in `custom/conf/app.ini` rather than `conf/app.ini`.

If you see anything like `%(X)s`, it's the feature powered by [goconfig](https://github.com/Unknwon/goconfig) for reading value recursively.

## Overall

- `APP_NAME`: Application name of server, change to whatever you want.
- `APP_LOGO`: The logo image path corresponding to `public` directory.
- `RUN_USER`: The system user requires to run, we recommend to be `git`; however, change to whatever your user name is if you run the server in your personal computer. Server may crash due to not set this value properly.
- `RUN_MODE`: For performance and other purpose, change this to `prod` when deploy to production environment.

## Repository

- `ROOT`: Root path of repositories that will be stored for all users.

## Server

- `DOMAIN`: Domain name of your server.
- `ROOT_URL`: Cut out the port number if you deploy Gogs in public domain.
- `HTTP_PORT`: HTTP port you want Gogs server to listen.

## Database

## Security

- `INSTALL_LOCK`: To indicate whether allow open install page(setting admin account involved so it's a very important value).
- `SECRET_KEY`: Global secret key for your server security, you'd better change it.

## Service

- `REGISTER_EMAIL_CONFIRM`: This enables mail confirmation of registration, requires enabled `Mailer`.
- `DISENABLE_REGISTERATION`: Disenables registration which only admin can create account for users.
- `REQUIRE_SIGNIN_VIEW`: This forces users to log in to view any page.
- `ENABLE_NOTIFY_MAIL`: This indicates whether send e-mail to watchers of repository when something happens like create issue, requires enabled `Mailer`.

## Mailer

- `ENABLED`: To indicate whether enable mail service of any.
- `HOST`: SMTP mail host address.
- `USER`: User name of system mailer(usually just your e-mail address).
- `PASSWD`: Password of you mailer.

## OAuth

## Cache

## Session

## Log
