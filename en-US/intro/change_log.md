---
name: Change Log
---

# Change Log

### v0.7.x (unreleased)

#### Bug fixes

- Bad syntax highlighting [#670](https://github.com/gogits/gogs/issues/670) [#1315](https://github.com/gogits/gogs/issues/1315) [#1549](https://github.com/gogits/gogs/issues/1549) [#1712](https://github.com/gogits/gogs/issues/1712)
- Broken copy link button [#1168](https://github.com/gogits/gogs/issues/1168)  [#1396](https://github.com/gogits/gogs/issues/1396) 
- Broken download archive UI [#1668](https://github.com/gogits/gogs/issues/1668)
- Pull request does not support merge BIN diff [#1922](https://github.com/gogits/gogs/issues/1922)
- Test patch does not checkout correct base branch [#1931](https://github.com/gogits/gogs/issues/1931) 
- Branch/tag selection has wrong z-index [#1942](https://github.com/gogits/gogs/issues/1942) 
- Huge image does not display correctly in file view
- No links in email for admin created account [#1979](https://github.com/gogits/gogs/issues/1979) 
- Repository description is not copied after forked [#1981](https://github.com/gogits/gogs/issues/1981) 
- Forked repository's visibility is changed itself when update settings [#1987](https://github.com/gogits/gogs/issues/1987) 

#### Improvements

- Sort collaborative repositories by last updated time in dashboard [#1302](https://github.com/gogits/gogs/issues/1302) 
- Update default branch in Git repository while change in web view [#1742](https://github.com/gogits/gogs/issues/1742)
- Show issue title and content in news feeds [#1854](https://github.com/gogits/gogs/issues/1854) 
- Show custom avatar for pushed commits list in news feeds
- Able to use config option `[other] SHOW_FOOTER_VERSION = true` disable version display on non-admin pages' footer [#1957](https://github.com/gogits/gogs/issues/1957) 

#### Features

- Admin can now view and edit settings of private repositories [#493](https://github.com/gogits/gogs/issues/493) [#1401](https://github.com/gogits/gogs/issues/1401) 

### v0.7.6 @ 2015-11-12

#### Bug fixes

- Images in subdirectory does not have correct relative links [#1904](https://github.com/gogits/gogs/issues/1904) 
- SSH operations do not handle mixed cases URL
- Wrong redirection after deleting system notice with sub-path [#1930](https://github.com/gogits/gogs/issues/1930) 

#### Improvements

- Show current branch in commit overview [#1572](https://github.com/gogits/gogs/issues/1572) 
- Allow tab to button in issue view page and use `enter` or space bar to trigger click [#1824](https://github.com/gogits/gogs/issues/1824) [#1917](https://github.com/gogits/gogs/issues/1917) 

#### Features

- Able to start builtin SSH server by config option `[server] START_SSH_SERVER = true`

### v0.7.0 @ 2015-11-08

#### Bug fixes

- Admin e-mail does not allow `root@localhost` when install [#470](https://github.com/gogits/gogs/issues/470)
- Wrong commits reference order on issue page [#1602](https://github.com/gogits/gogs/issues/1602)
- Inconsistent link of e-mail URL after sign up [#1697](https://github.com/gogits/gogs/issues/1697)
- Migrated repository incompatible with `--all` flag [#1705](https://github.com/gogits/gogs/issues/1705)
- Members of team has admin access can't close/reopen issues [#1748](https://github.com/gogits/gogs/issues/1748)
- Huge diff causes out of memory [#1790](https://github.com/gogits/gogs/issues/1790)
- Push returns fail message when no actual update needed [#1896](https://github.com/gogits/gogs/issues/1896) 
- Wrong image link is rendered for relative links [#1904](https://github.com/gogits/gogs/issues/1904) 

#### Improvements

- Detect file renames/moves in diffs [#1078](https://github.com/gogits/gogs/issues/1078)
- Dashboard issues add sorting [#1459](https://github.com/gogits/gogs/issues/1459)
- Allow import local repositories only for admin or permitted users [#1511](https://github.com/gogits/gogs/issues/1511)
- Able to trigger mailer for admin created accounts [#1525](https://github.com/gogits/gogs/issues/1525)
- Show clone URL with original cases [#1895](https://github.com/gogits/gogs/issues/1895)

#### Features

- Support pull requests [#5](https://github.com/gogits/gogs/issues/5)
- Auto-render clickable links for images [#1433](https://github.com/gogits/gogs/issues/1433)
- Add config option `[repository] FORCE_PRIVATE` that allows forcing all new repositories to be private [#1657](https://github.com/gogits/gogs/issues/1657)

#### Others

- Drop Go 1.2.x support, minimum requirement of Go is 1.3
- 0.5.x will no longer be supported in 0.8

### v0.6.15 @ 2015-09-26

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

### v0.6.9 @ 2015-09-05

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

### v0.6.5 @ 2015-08-16

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

### v0.6.3 @ 2015-08-02

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

### v0.6.1 @ 2015-03-26

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

### v0.6.0 @ 2015-03-19

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

### v0.5.13 @ 2015-02-13

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

**Older change logs can be found on [GitHub](https://github.com/gogits/gogs/releases).**
