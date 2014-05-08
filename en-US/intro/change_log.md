---
name: Change Log
sort: 1
---

# Change Log

### V0.4.0(2014-5-31)

#### Bug fix

- Cannot migrate repository when use PostgreSQL [#141](https://github.com/gogits/gogs/issues/141)
- Show private repository activities on public activities list [#148](https://github.com/gogits/gogs/issues/148)
- Does not verify admin user name in install page [#149](https://github.com/gogits/gogs/issues/149)
- Does not update all accesses when change user name [#150](https://github.com/gogits/gogs/issues/150)
- Panic when no master branch
- Panic when delete a branch [#155](https://github.com/gogits/gogs/issues/155)
- Redirect to 404 page when commenter is not the repository owner [#159](https://github.com/gogits/gogs/issues/159)

#### Improvement

- Able to set `GOGS_CONFIG` envrionment variable to load global configuration file before loading `custom/conf/app.ini` [#145](https://github.com/gogits/gogs/issues/145)
- Able to unbind social account from database
- Add mail notification for new comment and mentioned in new comment
- Add comment on issue activity
- Add clean unbind OAuthes operation in admin panel
- Underlying system of issue tracker

#### Feature

- Support user name contains dot `.` [#91](https://github.com/gogits/gogs/issues/91)
- Support add/remove repository collaborators
- Add `server -> DISABLE_ROUTER_LOG` option for disabling router log
- Add `picture -> DISABLE_GRAVATAR` option for disabling Gravatar
- Add command `gogs dump` for dumping files and database
- Support webhook services [#98](https://github.com/gogits/gogs/issues/98)
- Add read/unread status to issue

#### Other

- Official website online([gogs.io](http://gogs.io))
- Support install with Vagrant([note](https://github.com/geerlingguy/ansible-vagrant-examples/tree/master/gogs))

### V0.3.1(2014-4-28)

#### Bug fix

- Panic when try to get author of tag when there isn't one [#92](https://github.com/gogits/gogs/issues/92)
- Problems with Docker setup scripts [#124](https://github.com/gogits/gogs/pull/124) [#129](https://github.com/gogits/gogs/pull/129)
- Picture overflows when size is extremely large in single file page

#### Improvement

- Remember database option status in install page

#### Feature

- Basic support for LDAP/Microsoft Active Directory [#112](https://github.com/gogits/gogs/pull/112)
- Offline mode to disable fetch static resources from CDN
- Support log in by e-mail

#### Other

- Batch of typo and grammar fix
- Solution for MySQL initialization error when use wrong engine([note](https://github.com/gogits/gogs/wiki/Troubleshooting#error-1071-specified-key-was-too-long-max-key-length-is-1000-bytes))
- Make SQLite3 as default database option when enabled

### V0.3.0(2014-4-23)

#### Bug fix

- One-click copy button of clone URL in repository viewer doesn't work([note](https://github.com/gogits/gogs/wiki/Known-Issues#repository-viewerurl-usernamereponame))
- Doesn't delete corresponding accesses, watches when delete user
- Server log doesn't log into correct file

#### Improvement

- Add corresponding issue link to create issue notify mail
- Add salt for every single user
- Use PBKDF2 and user salt for encoding user password([note](https://github.com/gogits/gogs/wiki/Troubleshooting#upgrade-from-v020))
- Huge time, CPU and memory reduction of getting repository files 
- Show commits list by page, not all at once
- Use build tag to enable SQLite3 support([note](https://github.com/gogits/gogs/wiki/Install-from-source#install))

#### Feature

- Support rename repository/user
- Support transfer repository
- Support reset user password
- Support detect `@someone`, `#issueNum`, SHA1 and issue link in markdown render
- Support mail notify for someone is mentioned in creating issue
- Support `go get` in `meta` block
- Support setting default branch
- Support HTTP(S) push
- Support search commits by keyword in specific branch
- Support private repository
- Support migrate and mirror public/private repository
- Support social account login(GitHub, Google, QQ, Weibo)
- Support view and add new release(use existing tag or create a new one)
- Support download zip archive from any given commit
- Support browse code by tag

#### Other

- Support deploy with Docker([note](https://github.com/gogits/gogs/tree/master/dockerfiles))
- Git version requirement for both server and client sides become v1.6.6(Smart HTTP support).

### V0.2.0(2014-4-1)

- First public release.