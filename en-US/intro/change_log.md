---
name: Change Log
sort: 1
---

# Change Log

### v0.7.0 (unrelease)

#### Bug fixes

- Wrong commits reference order on issue page [#1602](https://github.com/gogits/gogs/issues/1602)
- Huge diff causes out of memory [#1790](https://github.com/gogits/gogs/issues/1790)

#### Improvements

- Able to trigger mailer for admin created accounts [#1525](https://github.com/gogits/gogs/issues/1525)

#### Features

- Support pull requests [#5](https://github.com/gogits/gogs/issues/5)

#### Others

- Drop Go 1.2.x support, minimum requirement of Go is 1.3

### v0.6.15

#### Bug fixes

- 404 when Repository name contains "git" [#1593](https://github.com/gogits/gogs/issues/1593)
- Collaborative repositories missing suburl on dashboard [#1594](https://github.com/gogits/gogs/issues/1594)
- Duplicate commit references when push a new branch [#1595](https://github.com/gogits/gogs/issues/1595)
- Upload image does not handle suburl [#1603](https://github.com/gogits/gogs/issues/1603)
- New SSH keys with comments including whitespace are truncated [#1622](https://github.com/gogits/gogs/issues/1622)
- Change label title resets color [#1659](https://github.com/gogits/gogs/issues/1659)

#### Improvements

- Able to use `GOGS_WORK_DIR` environment variable to specify work directory 
- Enable login type conversion after account creation [#748](https://github.com/gogits/gogs/issues/748)
- Sort owners list by last changed time when create and migrate repositoriy [#1585](https://github.com/gogits/gogs/issues/1585)

#### Features

- Add TiDB backend database support
- Add Emoji support [#633](https://github.com/gogits/gogs/issues/633)
- Able to disable captcha by config option `[service] ENABLE_CAPTCHA = false` [#697](https://github.com/gogits/gogs/issues/697)
- Able to restrict SMTP authentication to specific domains [#1620](https://github.com/gogits/gogs/issues/1620)

#### Others

- Drop social account login support

### v0.6.9

#### Bug fixes

- File name with double quotation mark makes the repository inaccessible [#966](https://github.com/gogits/gogs/issues/966)
- Time zone trouble [#1500](https://github.com/gogits/gogs/issues/1500)
- Removing deploy key does not remove key [#1535](https://github.com/gogits/gogs/issues/1535)

#### Improvements

- Add webhook last delivery status, recent deliveries and new events
- Auto-remember visibility of last created repository [#965](https://github.com/gogits/gogs/issues/965)
- Support BindDN and TLS in LDAP [#1145](https://github.com/gogits/gogs/issues/1145)
- Significantly enhanced LDAP support [#1476](https://github.com/gogits/gogs/pull/1476)
- Support 'AUTH LOGIN' in mailer [#1517](https://github.com/gogits/gogs/pull/1517)
- Add `[markdown] ENABLE_HARD_LINE_BREAK` to enable Markdown hard line break extension

#### Features

- Add dashboard issues page for organization
- Allow editing of past comments [#1280](https://github.com/gogits/gogs/issues/1280)
- Support README template [#1487](https://github.com/gogits/gogs/issues/1487)

#### Others

- Add [official Docker images](https://hub.docker.com/r/gogs/gogs/)
- Change minimum password length to 1
- Change minimum size of RSA to 1024 [#1519](https://github.com/gogits/gogs/pull/1519)
- Change maximum size of e-mail to 254 [#1579](https://github.com/gogits/gogs/pull/1579)

### v0.6.5

#### Bug fixes

- Does not allow anonymous SSH clone
- Private repository cannot trigger webhook by pushing through SSH
- Owners cannot assign any issue to themselves [#747](https://github.com/gogits/gogs/issues/747)
- Issue assignee doesn't show organisation members [#839](https://github.com/gogits/gogs/issues/839)
- Can send multiple requests when create issue [#1051](https://github.com/gogits/gogs/issues/1051)
- Attachments a file said "Could not parse JSON" [#1233](https://github.com/gogits/gogs/issues/1233)
- Did not remove the temporary directory after initialized new repository [#1331](https://github.com/gogits/gogs/issues/1331)
- Rename organization doesn't restrict Chinese [#1439](https://github.com/gogits/gogs/issues/1439)

#### Improvements

- Allow custom avatar source [#1457](https://github.com/gogits/gogs/pull/1457)

#### Features

- Add deploy key support [#334](https://github.com/gogits/gogs/issues/334)
- Generate random avatar based on e-mail when disable Gravatar
- Able to sort issues

### v0.6.3

#### Bug fixes

- Label disappeared after edited a label [#542](https://github.com/gogits/gogs/issues/542)
- Filename cut off in DIFF when containing spaces [#985](https://github.com/gogits/gogs/issues/985)
- Migrate repository requires HTTPS address [#1000](https://github.com/gogits/gogs/issues/1000)
- Private repositories issues included in "Public Activity" [#1112](https://github.com/gogits/gogs/issues/1112)
- All users email are public [#1127](https://github.com/gogits/gogs/issues/1127)
- API calls are not hidden behind sign in [#1128](https://github.com/gogits/gogs/issues/1128)
- 404 on files with url-encoded names [#1137](https://github.com/gogits/gogs/issues/1137)
- It is possible to access user profiles using organization URL [#1169](https://github.com/gogits/gogs/issues/1169)
- Didn't check blank user name on LDAP [#1207](https://github.com/gogits/gogs/issues/1207)
- Generated certificate doesn't have CN with the hostname [#1231](https://github.com/gogits/gogs/issues/1231)
- Removing user from organization collaboration removes repositiory [#1279](https://github.com/gogits/gogs/issues/1279)
- Create repo for other users by hacking uid field [#1289](https://github.com/gogits/gogs/issues/1289)

#### Improvements

- Clearer error message for illegal characters [#1070](https://github.com/gogits/gogs/issues/1070)
- Add full name field to admin's user edit page [#1130](https://github.com/gogits/gogs/issues/1130)
- Hide organization email for non logged-in users [#1204](https://github.com/gogits/gogs/issues/1204)
- Visit Repository home page with ".git" appended URL [#1227](https://github.com/gogits/gogs/issues/1227)

#### Features

- Support realtime webhook [#835](https://github.com/gogits/gogs/issues/835)

#### Others

- Add Italian language support.
- Disable Macaron color log in production mode to improve performance
- Show repository owner name in explore page [#1150](https://github.com/gogits/gogs/issues/1150)

### v0.6.1

#### Bug fixes

- Inline code markdown with leading hash is rendered as issue index [#637](https://github.com/gogits/gogs/issues/637)
- Non-logged users can view organization page when `REQUIRE_SIGNIN_VIEW = true` [#1101](https://github.com/gogits/gogs/issues/1101)
- New release button is always available to everyone [#1114](https://github.com/gogits/gogs/issues/1114)
- Cannot update mirror repository after transfer ownership [#1120](https://github.com/gogits/gogs/issues/1120)
- Other member of teams in same organization get access to repository when teams do not have relations to the repository
- LDAP add and edit forms are misleading [#1124](https://github.com/gogits/gogs/issues/1124)
- Team member access lost when adding repository collaborator [#1143](https://github.com/gogits/gogs/issues/1143)

#### Improvements

- Hide Gravatar e-mail setting field when Gravatar is disabled [#1098](https://github.com/gogits/gogs/issues/1098)
- Allow to migrate through `git://` protocol [#1105](https://github.com/gogits/gogs/pull/1105)
- Add config option `[service] DISABLE_MINIMUM_KEY_SIZE_CHECK` to not check minimum key size with corresponding type [#1133](https://github.com/gogits/gogs/pull/1133)
- Do not exposure database password when it's not first time launch installation [#1140](https://github.com/gogits/gogs/issues/1140)
- Able to use `[mailer] DISABLE_HELO` config option to disable HELO operation
- Able to use `[mailer] HELO_HOSTNAME` config option to set custom hostname for HELO operation

#### Others

- Use `fake@gogs.local` as default Git `user.email` setting rather than private e-mail [#1089](https://github.com/gogits/gogs/issues/1089)
- Improved UI for some pages.

### v0.6.0

#### Bug fixes

- Edit Account does not take into consideration password rules [#851](https://github.com/gogits/gogs/issues/851)
- Person in multiple teams has incorrect access [#858](https://github.com/gogits/gogs/issues/858)
- Issue label amount not updated on issue removal [#933](https://github.com/gogits/gogs/issues/933)
- Can push to mirror repository [#948](https://github.com/gogits/gogs/issues/948)
- Check template version before loading custom configuration [#954](https://github.com/gogits/gogs/issues/954)
- Didn't check if attachments and avatars path in configuration is a absolutely path
- Duplicated suburl prefix in feeds [#988](https://github.com/gogits/gogs/issues/988)
- Cannot delete repository with LDAP account [#1006](https://github.com/gogits/gogs/issues/1006)
- Cannot handle SubModule without a .gitmodules entry [#1023](https://github.com/gogits/gogs/issues/1023)
- HTTP/HTTPS push update function call panic [#1037](https://github.com/gogits/gogs/issues/1037)
- Missing suburl prefix on admin panel [#1043](https://github.com/gogits/gogs/pull/1043)
- Landing page setting does not consider suburl prefix [#1055](https://github.com/gogits/gogs/pull/1055)
- Missing link in bare repository page for Help [#1082](https://github.com/gogits/gogs/issues/1082)

#### Improvements

- Allow MySQL socket connection instead of TCP [#872](https://github.com/gogits/gogs/issues/872)
- Able to use TLS client certificate for SMTP [#943](https://github.com/gogits/gogs/pull/943)
- Fix: 504 5.5.2 <localhost>: Helo command rejected [#973](https://github.com/gogits/gogs/pull/973)

#### Features

- Able to import local Git repositories [#99](https://github.com/gogits/gogs/issues/99)
- Allow multiple e-mail addresses [#755](https://github.com/gogits/gogs/pull/755)

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

**Older change logs can be found on [GitHub](https://github.com/gogits/gogs/releases).**