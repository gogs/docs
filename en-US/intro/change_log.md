---
name: Change Log
sort: 1
---

# Change Log

### v0.6.0

#### Bug fixes

- Cannot download repository archive [#495](https://github.com/gogits/gogs/issues/495)
- Cannot view repository by tag

#### Improvements

- Improve e-mail security [#249](https://github.com/gogits/gogs/issues/249)
- Fix missing inline code Markdown style [#491](https://github.com/gogits/gogs/issues/491)

#### Features

- Allow Gogs to run from a suburl behind a reverse proxy [#463](https://github.com/gogits/gogs/pull/463)
- Add `gogs cert` command to generate files for self-signed HTTPS [#487](https://github.com/gogits/gogs/issues/487)
- Add support for custom `robots.txt`
- Add basic support for submodule

### v0.5.2 @ 2014-9-18

#### Bug fixes

- Incorrect permission check of `~/.ssh/` [#458](https://github.com/gogits/gogs/issues/458)
- Can access some pages without signin with `REQUIRE_SIGNIN_VIEW=true` [#464](https://github.com/gogits/gogs/issues/464)
- Templating error `html/template: "user/activate" is undefined` [#465](https://github.com/gogits/gogs/issues/465)
- Missing arguments in `TimeSince` [#473](https://github.com/gogits/gogs/issues/473)
- Wrong action permission check in organization dashboard [#474](https://github.com/gogits/gogs/pull/474)
- Cannot add new SSH Key in Windows [#475](https://github.com/gogits/gogs/issues/475)
- Cannot transfer repository ownership [#481](https://github.com/gogits/gogs/issues/481)

#### Improvements

- Downgrade Git requirement to 1.7.1 [#476](https://github.com/gogits/gogs/issues/476)
- Add French translation [#479](https://github.com/gogits/gogs/pull/479)
- Add `git -> MAX_GITDIFF_LINES` option to set max show line numbers of Git Diff page

#### Others

- Demo site use HTTPS with new domain [https://try.gogs.io](https://try.gogs.io)

### v0.5.0 @ 2014-9-15

#### Bug fixes

- Panic when view releases that were created by Gogs [#197](https://github.com/gogits/gogs/issues/197)
- Content lost if user changes milestone or assignee [#216](https://github.com/gogits/gogs/issues/216)
- Webhook doesn't deliver for SSH pushes [#242](https://github.com/gogits/gogs/issues/242)
- Mirror repositories are not updated at all [#258](https://github.com/gogits/gogs/issues/258)
- Not able to serve static files in Windows [#271](https://github.com/gogits/gogs/issues/271)
- Dashboard issue link is incomplete [#273](https://github.com/gogits/gogs/issues/273)
- Collaborators are able to change repository settings
- Edit issue label does not require repository owner or collaborator [#303](https://github.com/gogits/gogs/issues/303)
- Milestone issue stats not update when reopening/closing issue [#340](https://github.com/gogits/gogs/pull/340)
- Incorrect max/min limitation error message [#340](https://github.com/gogits/gogs/pull/340)
- Missing trailing '/' in `ROOT_URL` causes problems [#367](https://github.com/gogits/gogs/issues/367)
- SSH keys that include new lines can't be deleted from authorized_keys [#370](https://github.com/gogits/gogs/issues/370)

#### Improvements

- Add `webhook` section for configuring web hook **task interval** and **deliver timeout**
- Add download TAR.GZ button in repository viewer
- Sort releases by created time if they have same number of commits [#199](https://github.com/gogits/gogs/issues/199)
- Add Git installation and version check in start
- Able to show precise time on commit page [#281](https://github.com/gogits/gogs/pull/281)
- Make possible for administrators to change user's password [#291](https://github.com/gogits/gogs/pull/291)
- Add more SSH key type verification support [#293](https://github.com/gogits/gogs/pull/293)
- Allow clickable links in the repository description [#300](https://github.com/gogits/gogs/pull/300)
- Allow `/:username` as user home page route 
- Change passoword length limitation to 255 [#340](https://github.com/gogits/gogs/pull/340)
- Add `.mkd` as Markdown file extension [#362](https://github.com/gogits/gogs/issues/362)
- Allow `.` in repository name [#453](https://github.com/gogits/gogs/issues/453)

#### Features

- Add command `gogs fix location <old path>` to handle Gogs app location change
- Support edit release and save as draft
- Add cron task and running process monitor panel
- Add database adapter for logging
- Add delete all inactivate accounts operation in admin panel
- Add reverse proxy authentication support [#165](https://github.com/gogits/gogs/issues/165)
- Add application level GZIP support by `server -> ENABLE_GZIP` config option.
- Closing issues through commits [#302](https://github.com/gogits/gogs/issues/302)
- Able to star/unstar a repository
- Ability to attach files to issues (attachments) [#307](https://github.com/gogits/gogs/pull/307)
- Able to create/manage/delete organization with team management
- Add Slack webhook integration [#379](https://github.com/gogits/gogs/pull/379)
- Add Organization-level Webhooks [#442](https://github.com/gogits/gogs/pull/442)

#### Others

- Official website brand new design([gogs.io](http://gogs.io))
- Whole site new UI design
- Most of pages implement multiple languages
- Add Ubuntu install package [#455](https://github.com/gogits/gogs/pull/455)

### v0.4.2 @ 2014-6-6

#### Bug fixes

- System mail didn't use `mailer -> FROM` as sender name [#214](https://github.com/gogits/gogs/issues/214)
- Verbose prefix of gitignore and license files in create repository page [#230](https://github.com/gogits/gogs/issues/230)
- Comment length is limited to 255 [#232](https://github.com/gogits/gogs/issues/232)
- Cannot create repository with custom gitignore or license files [#237](https://github.com/gogits/gogs/issues/237)

### v0.4.1 @ 2014-6-2

#### Bug fixes

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

#### Improvements

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

#### Features

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


#### Others

- Official website online([gogs.io](http://gogs.io))
- Support install with Vagrant([note](https://github.com/geerlingguy/ansible-vagrant-examples/tree/master/gogs))
- Support install from AUR packages [#176](https://github.com/gogits/gogs/issues/176)

### v0.3.1 @ 2014-4-28

#### Bug fixes

- Panic when try to get author of tag when there isn't one [#92](https://github.com/gogits/gogs/issues/92)
- Problems with Docker setup scripts [#124](https://github.com/gogits/gogs/pull/124) [#129](https://github.com/gogits/gogs/pull/129)
- Picture overflows when size is extremely large in single file page

#### Improvements

- Remember database option status in install page

#### Features

- Basic support for LDAP/Microsoft Active Directory [#112](https://github.com/gogits/gogs/pull/112)
- Offline mode to disable fetch static resources from CDN
- Support log in by e-mail

#### Others

- Batch of typo and grammar fix
- Solution for MySQL initialization error when use wrong engine([note](https://github.com/gogits/gogs/wiki/Troubleshooting#error-1071-specified-key-was-too-long-max-key-length-is-1000-bytes))
- Make SQLite3 as default database option when enabled

### v0.3.0 @ 2014-4-23

#### Bug fixes

- One-click copy button of clone URL in repository viewer doesn't work([note](https://github.com/gogits/gogs/wiki/Known-Issues#repository-viewerurl-usernamereponame))
- Doesn't delete corresponding accesses, watches when delete user
- Server log doesn't log into correct file

#### Improvements

- Add corresponding issue link to create issue notify mail
- Add salt for every single user
- Use PBKDF2 and user salt for encoding user password([note](https://github.com/gogits/gogs/wiki/Troubleshooting#upgrade-from-v020))
- Huge time, CPU and memory reduction of getting repository files 
- Show commits list by page, not all at once
- Use build tag to enable SQLite3 support([note](https://github.com/gogits/gogs/wiki/Install-from-source#install))

#### Features

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

#### Others

- Support deploy with Docker([note](https://github.com/gogits/gogs/tree/master/dockerfiles))
- Git version requirement for both server and client sides become v1.6.6(Smart HTTP support).

### v0.2.0 @ 2014-4-1

- First public release.
