---
name: Change Log
sort: 1
---

# Change Log

### v0.6.0

#### Bug fixes

- Check template version before loading custom configuration [#954](https://github.com/gogits/gogs/issues/954)
- Didn't check if attachments and avatars path in configuration is a absolutely path

### v0.5.13 @ 2015-2-13

#### Bug fixes

- Email addresses treated as at-mentions [#737](https://github.com/gogits/gogs/issues/737)
- Add Team Repository error in SQLite3 [#739](https://github.com/gogits/gogs/issues/739)
- Migrated repository does not have update hook [#789](https://github.com/gogits/gogs/issues/789)
- `num_watchers` not updated when adding a bare repository [#819](https://github.com/gogits/gogs/issues/819)
- Data racing when shoot webhook through SSH [#827](https://github.com/gogits/gogs/issues/827)
- XSS attacks in commit messages [#828](https://github.com/gogits/gogs/issues/828)
- User auto-completion fails [#832](https://github.com/gogits/gogs/issues/832)
- Choose wrong README sometimes [#877](https://github.com/gogits/gogs/issues/877)
- Problem in LDAP UTF-8 string decoding [#916](https://github.com/gogits/gogs/issues/916)
- Panic when try to watch as non-logged user [#929](https://github.com/gogits/gogs/issues/929)

#### Improvements

- Parse user information with the Go tools when migrate [#822](https://github.com/gogits/gogs/pull/822)
- Flexible SSH key format support: OpenSSH, SSH2 and base64 encoded key [#825](https://github.com/gogits/gogs/pull/825)
- Able to use `./gogs web -port 3001` to prevent first time run port conflict
- Able to disable SSH feature [#883](https://github.com/gogits/gogs/issues/883)
- Add option for hiding "Sign Up" when register is disabled [#884](https://github.com/gogits/gogs/issues/884)
- Optionally do not verify certificate for webhooks [#891](https://github.com/gogits/gogs/issues/891)
- Link to previous committed source file instead of returning 404 for deleted files [#911](https://github.com/gogits/gogs/pull/911)
- Able to select-on-click clone URL then copy in case Flash is disabled [#937](https://github.com/gogits/gogs/pull/937)

#### Features

- Able to control issues in commit message [#668](https://github.com/gogits/gogs/issues/668)
- Able to rewrite full `.ssh/authorized_key` from database [#818](https://github.com/gogits/gogs/pull/818)
- Able to regenerate new update hook file for repositories
- Add Russian and Japanese language support.
- Highlighting selected code in diff view [@makhov](https://github.com/makhov)
- Allow HTTP(S) Git actions using application token [#842](https://github.com/gogits/gogs/issues/842)

### v0.5.11 @ 2015-1-5

#### Bug fixes

- Git SubModules result 500 error [#741](https://github.com/gogits/gogs/issues/741)
- Showing activities for private repositories in user profile [#751](https://github.com/gogits/gogs/issues/751)
- User who made activities no longer exists result 500 error [#754](https://github.com/gogits/gogs/issues/754)
- Auto-input username in organization invite page includes full name
- Mirror repository does not work with SQLite3 [#805](https://github.com/gogits/gogs/issues/805)
- Wrong image address when rendering Markdown files [#808](https://github.com/gogits/gogs/issues/808)

#### Improvements

- Able to skip verification when send mails and use TLS when port is 465 [#761](https://github.com/gogits/gogs/pull/761)
- Optmize git-fsck config options [#820](https://github.com/gogits/gogs/issues/820)

#### Features

- Able to send mails with CRAM-MD5 authentication [#762](https://github.com/gogits/gogs/pull/762)

### v0.5.9 @ 2014-12-13

#### Bug fixes

- Invalid links to user profile page in admin panel
- Templating error on settings page of bare repository [#643](https://github.com/gogits/gogs/issues/643)
- Panic when no SSH authorized_keys file exists for command `gogs fix location` [#659](https://github.com/gogits/gogs/issues/659)
- Commits list doesn't show the oldest page [#664](https://github.com/gogits/gogs/issues/664)
- User home links in issue page no longer invalid [#682](https://github.com/gogits/gogs/issues/682)
- Avatar email addresses with uppercase resolve to wrong Gravatar hash [#700](https://github.com/gogits/gogs/issues/700)
- Markdown table requires padding [#703](https://github.com/gogits/gogs/issues/703)
- Cannot display GBK content in diff page [#711](https://github.com/gogits/gogs/issues/711)
- HTTP basic authentication failed when password contains `:` [#723](https://github.com/gogits/gogs/issues/723)

#### Improvements

- Expose `full_name` in user search API [#677](https://github.com/gogits/gogs/issues/677)
- Added issue link rendering in commit messages [#712](https://github.com/gogits/gogs/issues/712)

#### Features

- Able to upload custom avatar [#139](https://github.com/gogits/gogs/issues/139)
- Able to set explore page as non-logged users' landing page through config option `[server] LANDING_PAGE` [#543](https://github.com/gogits/gogs/issues/543)
- Run `git fsck` as cron job and `git gc` as admin operation [#580](https://github.com/gogits/gogs/issues/580)
- Able to view public key list of user by `/:username.keys` [#652](https://github.com/gogits/gogs/issues/652)
- Add Latvian language support.

### v0.5.8 @ 2014-11-19

#### Bug fixes

- Fix vulnerabilities CVE-2014-8681 CVE-2014-8682 CVE-2014-8683
- Branch/tag name cannot contain `/` [#101](https://github.com/gogits/gogs/issues/101) [#255](https://github.com/gogits/gogs/issues/255)
- `ENABLE_GZIP` options does not work [#412](https://github.com/gogits/gogs/issues/412)
- Line numbers are misaligned on Firefox [#457](https://github.com/gogits/gogs/issues/457)
- Git hook does't filter `\r` character [#546](https://github.com/gogits/gogs/issues/546)
- File view raw and history buttons don't show [#550](https://github.com/gogits/gogs/issues/550)
- Some small problems about the alignment [#554](https://github.com/gogits/gogs/issues/554)
- Redis as cache adapter does not work
- Cannot show relative path image in Markdown files
- UI break when commit message is very long [#570](https://github.com/gogits/gogs/issues/570)
- HTTP/HTTPS clone does not handle GZIP encoding [#572](https://github.com/gogits/gogs/issues/572)
- Cannot see private repositories when view own profile page [#605](https://github.com/gogits/gogs/issues/605)
- Wrong MIT LICENSE content file [#608](https://github.com/gogits/gogs/issues/608)

#### Improvements

- Allow collaborators to see private repositories in profile page

#### Features

- Able to fork repository [#5](https://github.com/gogits/gogs/issues/5)
- Drone CI integration [#12](https://github.com/gogits/gogs/issues/12)
- Able to view comparison page for 2 commits
- Able to set `[picture] GRAVATAR_SOURCE = duoshuo` to use Chinese mirror of Gravatar
- Able to delete all repositories archives through admin panel [#635](https://github.com/gogits/gogs/issues/635)

### v0.5.5 @ 2014-10-10

#### Bug fixes

- Cannot download repository archive [#495](https://github.com/gogits/gogs/issues/495)
- Cannot view repository by tag
- Cannot transfer repository from organization to individual
- Error occurs when owner transfers repository to its collaborator
- Does not support annotated tag [#515](https://github.com/gogits/gogs/issues/515)
- Broken authentication logic

#### Improvements

- Improve e-mail security [#249](https://github.com/gogits/gogs/issues/249)
- Fix missing inline code Markdown style [#491](https://github.com/gogits/gogs/issues/491)
- Add directory level commit message in repository list view
- Change issue title length limitation to 255 characters [#522](https://github.com/gogits/gogs/issues/522)
- Allow mail with self-signed certificates
- Allow custom locale files

#### Features

- Add support for Git hooks [#264](https://github.com/gogits/gogs/issues/264)
- Allow Gogs to run from a suburl behind a reverse proxy [#463](https://github.com/gogits/gogs/pull/463)
- Add `gogs cert` command to generate files for self-signed HTTPS [#487](https://github.com/gogits/gogs/issues/487)
- Add support for custom `robots.txt`
- Add basic support for submodule
- Add Franch, Dutch and Traditional Chinese languages.
- Add system notices for admin.

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
