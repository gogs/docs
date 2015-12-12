---
name: Change Log
---

# Change Log

### v0.8.0 (unreleased)

#### Bug fixes

- SMTP authentication makes invalid assumption on protocol [#2152](https://github.com/gogits/gogs/issues/2152) 

#### Improvements

- Send email when a new pull request is submitted [#1612](https://github.com/gogits/gogs/issues/1612) 
- Auto login after install if admin is configured [#1627](https://github.com/gogits/gogs/issues/1627) 
- Able to config `git fsck` timeout [#1943](https://github.com/gogits/gogs/issues/1943) 
- Able to show and edit mirror address on repository pages [#1984](https://github.com/gogits/gogs/issues/1984) 
- Show author email in commit diff [#2035](https://github.com/gogits/gogs/issues/2035) 
- Able to change mirror source address
- Add "New Mirror" button on dashboard [#2037](https://github.com/gogits/gogs/issues/2037) 

#### Features

- Able to limit repository creation per user [#1575](https://github.com/gogits/gogs/issues/1575) 
- Able to select branch in commits page [#1846](https://github.com/gogits/gogs/issues/1846) 

#### Others

- Drop `0.5.x` support, minimum auto-migration version is `0.6.0`.

### v0.7.33 @ 2015-12-06

#### Bug fixes

- LDAP search with non-ascii characters does not work [#1139](https://github.com/gogits/gogs/issues/1139) 
- Delete repository does not remove its stars [#2042](https://github.com/gogits/gogs/issues/2042) 
- Diff is not showing full content when has super long one line [#2071](https://github.com/gogits/gogs/issues/2071)
- Cannot create pull request on Windows [#2093](https://github.com/gogits/gogs/issues/2093) 

#### Improvements

- Able to disable wiki/issues/pull requests of repository [#1829](https://github.com/gogits/gogs/issues/1829) 
- Able to trigger test webhook in web UI [#1857](https://github.com/gogits/gogs/issues/1857) 
- Able to batch delete system notices [#2052](https://github.com/gogits/gogs/issues/2052) 
- Able to delete repository in admin panel [#2063](https://github.com/gogits/gogs/issues/2063) 

#### Features

- Support repository wiki [#270](https://github.com/gogits/gogs/issues/270) 
- Support issue links are rendered for external tracker [#890](https://github.com/gogits/gogs/issues/890) 
- Add more APIs: public keys [#976](https://github.com/gogits/gogs/issues/976) 

### v0.7.22 @ 2015-11-25

#### Bug fixes

- Panic when two links are nested in Markdown [#2019](https://github.com/gogits/gogs/issues/2019) 
- Builtin SSH server does not work on Windows 

#### Improvements

- Drop `org/` URL path prefix in organization home page [#1944](https://github.com/gogits/gogs/issues/1944) 
- More native supported Git hooks

#### Others

- All pages uses new Semantic UI theme [#650](https://github.com/gogits/gogs/issues/650) 

### v0.7.19 @ 2015-11-21

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
- Able to delete a release [#1383](https://github.com/gogits/gogs/issues/1383) 
- Update default branch in Git repository while change in web view [#1742](https://github.com/gogits/gogs/issues/1742)
- Show issue title and content in news feeds [#1854](https://github.com/gogits/gogs/issues/1854) 
- Show custom avatar for pushed commits list in news feeds
- Able to use config option `[other] SHOW_FOOTER_VERSION = true` disable version display on non-admin pages' footer [#1957](https://github.com/gogits/gogs/issues/1957) 

#### Features

- Admin can now view and edit settings of private repositories [#493](https://github.com/gogits/gogs/issues/493) [#1401](https://github.com/gogits/gogs/issues/1401) 

#### Others

- New discussion forum http://forum.gogs.io/

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

**Older change logs can be found on [GitHub](https://github.com/gogits/gogs/releases).**
