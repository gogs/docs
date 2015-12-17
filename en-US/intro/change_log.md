---
name: Change Log
---

# Change Log

### v0.8.x (unreleased)

#### Bug fixes

- Wiki preview does not work on Firefox [#2171](https://github.com/gogits/gogs/issues/2171)
- 500 when view repository watchers and stargazers with PostgreSQL [#2176](https://github.com/gogits/gogs/issues/2176)
- Cannot detect correct file encoding [#2185](https://github.com/gogits/gogs/issues/2185) 
- Huge diff hangs 
- Cannot handle non-commit tag

#### Features

- Add more APIs: user emails

### v0.8.0 @ 2015-12-13

#### Bug fixes

- Cannot push repository with massive commits like Linux kernel [#279](https://github.com/gogits/gogs/issues/279) 
- SMTP authentication makes invalid assumption on protocol [#2152](https://github.com/gogits/gogs/issues/2152) 

#### Improvements

- Send email when a new pull request is submitted [#1612](https://github.com/gogits/gogs/issues/1612) 
- Auto login after install if admin is configured [#1627](https://github.com/gogits/gogs/issues/1627) 
- Disable change username and password for non-local users [#1374](https://github.com/gogits/gogs/issues/1374)  [#1938](https://github.com/gogits/gogs/issues/1938) [#2154](https://github.com/gogits/gogs/issues/2154) 
- Able to config `git fsck` timeout [#1943](https://github.com/gogits/gogs/issues/1943) 
- Able to show and edit mirror address on repository pages [#1984](https://github.com/gogits/gogs/issues/1984)
- Do not show content of issue in activity timeline [#2029](https://github.com/gogits/gogs/issues/2029)
- Show author email in commit diff [#2035](https://github.com/gogits/gogs/issues/2035) 
- Able to change mirror source address
- Add "New Mirror" button on dashboard [#2037](https://github.com/gogits/gogs/issues/2037) 
- Able to set external URL for wiki [#2114](https://github.com/gogits/gogs/issues/2114) 

#### Features

- Able to limit repository creation per user [#1575](https://github.com/gogits/gogs/issues/1575) 
- Able to select branch in commits page [#1846](https://github.com/gogits/gogs/issues/1846) 

#### Others

- Drop `0.5.x` support, minimum auto-migration version is `0.6.0`

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

**Older change logs can be found on [GitHub](https://github.com/gogits/gogs/releases).**
