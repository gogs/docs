---
name: Troubleshooting
sort: 2
---

# Troubleshooting

### Git

#### `git push` through SSH get error `bash /path/to/gogs: no such file or directory`

That's because you change the location of Gogs server after a while and the old path was hard coded into `~/.ssh/authorized_keys` file.

#### `repo.NewRepoContext(fail to set git user.email):`

It happens when Windows users install Git Bash without enabling the `cmd` option, please reinstall and enable it.

#### Cannot access repository through SSH

- You use same `authorized_keys` file for both GitLab and Gogs.

### Register/create user/repository

#### `Repository/User name contains illegal characters`

In order to prevent unexpected exceptions, your user/repository name will be considered as illegal if they match any of the following rules: 

- Name equals to any word of `"raw", "install", "api", "avatar", "user", "help", "stars", "issues", "pulls", "commits", "repo", "template", "admin"`.
- Name has suffix `".git"`.

### Cache

#### `cache: unknown adaptername "memcache" (forgotten import?)`

To prevent unnecessary import of package, we use build tags to specify when needed:

- Download: `go get -tags memcache github.com/gogits.gogs`
- Build: `go build -tags memcache`

Same steps for `redis` when you want it to be the cache adapter.

### MySQL

#### `Error 1071: Specified key was too long; max key length is 1000 bytes`

It is caused by MyISAM. Once you import the `config/mysql.sql` then login into mysql and run:

```sql
use gogs;
set global storage_engine=INNODB;
```

After that, go to [http://localhost:3000/install](http://localhost:3000/install) and everything works fine(thanks [@linc01n](https://github.com/linc01n)).

### Mailer

#### Cannot send e-mail

Currently golang does not support send e-mail through SSL, so please choose a port that does not require SSL for sending e-mails. If you know how to send e-mail through SSL in Go, please contact us!

#### Gmail with Error 534: `Please log in via your web browser and then try again`

This is because Google does not trust your server, so first you need to visit https://accounts.google.com and log in, then go to https://accounts.google.com/DisplayUnlockCaptcha click `continue`. Now copy the link looks like this(prompt in Gogs server log): https://accounts.google.com/ContinueSignIn?sarp=1&scc=1&plt=AKgnsbvPPN_E_25__nyS*******f18O9uuLNtz0Imw and log in again. Things should work now. Last but not the least, check you `spam` box in case your mail service provider thinks your gmail is a spammer.

### Other

#### `Error 1062: Duplicate entry 'Unknown-Mac' for key 'UQE_public_key_name'`

It is led by legacy code, `public_key` table used to have `UQE_public_key_name` unique rule for SSH key name in very early version. You can delete that unique rule manually to fix this problem.

#### `GLIBC_2.14 not found`

Try `sudo apt-get -t testing install libc6-dev`.

#### Cannot parse `custom/conf/app.ini`

You got error message like follows in start:

```
[FATAL][github.com/gogits/gogs/modules/base] conf.go:287: Cannot load config file(/Users/.../gogits/gogs/custom/conf/app.ini): could not parse line: ; App name that shows on every page title
```

It may because you save the file as `UTF8 with BOM`(normally happens in Windows), please change it to `UTF8`.

#### Upgrade from `v0.2.0`

- More secure way to encode user password, so all old users are asked to reset password(URL:`/user/forget_password`).