---
name: Change Log
sort: 1
---

# Change Log

### V0.5.0(2014-8-12)

#### Bug fix

- Panic when view releases that were created by Gogs [#197](https://github.com/gogits/gogs/issues/197)
- Webhook doesn't deliver for SSH pushes [#242](https://github.com/gogits/gogs/issues/242)

#### Improvement

- Add `webhook` section for configuring web hook **task interval** and **deliver timeout**
- Add download TAR.GZ button in repository viewer
- Sort releases by created time if they have same number of commits [#199](https://github.com/gogits/gogs/issues/199)

#### Feature

- Add command `gogs fix location <old path>` to handle Gogs app location change
- Support edit release and save as draft
- Add cron task and running process monitor panel
- Add database adapter for logging
- Add delete all inactivate accounts operation in admin panel
- Add reverse proxy authentication support [#165](https://github.com/gogits/gogs/issues/165)

### V0.4.2(2014-6-6)

#### Bug fix

- System mail didn't use `mailer -> FROM` as sender name [#214](https://github.com/gogits/gogs/issues/214)
- Verbose prefix of gitignore and license files in create repository page [#230](https://github.com/gogits/gogs/issues/230)
- Comment length is limited to 255 [#232](https://github.com/gogits/gogs/issues/232)
- Cannot create repository with custom gitignore or license files [#237](https://github.com/gogits/gogs/issues/237)

### V0.4.1(2014-6-2)

#### Bug fix

- Cannot clone through SSH with non-default port(22) [#94](https://github.com/gogits/gogs/issues/94)
- Cannot migrate repository when use PostgreSQL [#141](https://github.com/gogits/gogs/issues/141)
- Show private repository activities on public activities list [#148](https://github.com/gogits/gogs/issues/148)
- Does not verify admin user name in install page [#149](https://github.com/gogits/gogs/issues/149)
- Does not update all accesses when change user name [#150](https://github.com/gogits/gogs/issues/150)
- Panic when no master branch
- Panic when delete a branch [#155](https://github.com/gogits/gogs/issues/155)
- Redirect to 404 page when commenter is not the repository owner [#159](https://github.com/gogits/gogs/issues/159)
- Show 500 page when poster of issue no longer exists [#167](https://github.com/gogits/gogs/issues/167)
- Using @ in code block tries to make a mention [#178](https://github.com/gogits/gogs/issues/178)

#### Improvement

- Able to unbind social account from database
- Add mail notification for new comment and mentioned in new comment
- Add comment on issue activity
- Add clean unbind OAuthes operation in admin panel
- Underlying system of issue tracker
- Able to log message to different adapters by level at same time
- Show collaborative repositories in dashboard
- Able to preview option for editing of issue [#204](https://github.com/gogits/gogs/issues/204)
- Able to set `GOGS_CUSTOM` envrionment variable to set global custom path [#209](https://github.com/gogits/gogs/issues/209)
- Add `log -> ROOT_PATH` option for custom log file path [#209](https://github.com/gogits/gogs/issues/209)

#### Feature

- Support SMTP authentication [#8](https://github.com/gogits/gogs/issues/8)
- Support user name contains dot `.` [#91](https://github.com/gogits/gogs/issues/91)
- Support add/remove repository collaborators
- Add `server -> DISABLE_ROUTER_LOG` option for disabling router log
- Add `picture -> DISABLE_GRAVATAR` option for disabling Gravatar
- Add command `gogs dump` for dumping files and database
- Support webhook services [#98](https://github.com/gogits/gogs/issues/98)
- Add read/unread status to issue
- Add assignee to issue
- Add history page for file [#166](https://github.com/gogits/gogs/issues/166)
- Support add custom .gitignore and license files by adding them to `custom/conf/gitignore` and `custom/conf/license` [#174](https://github.com/gogits/gogs/issues/174)
- Add milestone to issue tracker
- Support download tar.gz for releases [#186](https://github.com/gogits/gogs/issues/186)
- Add `server -> STATIC_ROOT_PATH` option for indicating custom template and static file path [#209](https://github.com/gogits/gogs/issues/209)


#### Other

- Official website online([gogs.io](http://gogs.io))
- Support install with Vagrant([note](https://github.com/geerlingguy/ansible-vagrant-examples/tree/master/gogs))
- Support install from AUR packages [#176](https://github.com/gogits/gogs/issues/176)

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