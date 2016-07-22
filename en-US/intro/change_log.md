---
name: Changelog
---

# Changelog

### v0.9.48 @ 2016-07-22

#### Bug fixes

- 500 when create pull request with SQLite3 [#3291](https://github.com/gogits/gogs/issues/3291)
- Wrong LDAP username vaildation logic [#3295](https://github.com/gogits/gogs/issues/3295)
- Rewrite update hook operation does not fix wrong permission of script [#3302](https://github.com/gogits/gogs/issues/3302)

### v0.9.46 @ 2016-07-17

#### Bug fixes

- Crash with huge size text file [#1513](https://github.com/gogits/gogs/issues/1513)
- Emojis are removed when issue is edited [#2458](https://github.com/gogits/gogs/issues/2458)
- Did not validate attributes fetched from LDAP [#2709](https://github.com/gogits/gogs/issues/2709)
- Raw file link broken when filename contains spaces [#2842](https://github.com/gogits/gogs/issues/2842)
- No mail notification when issue is closed/reopened [#2854](https://github.com/gogits/gogs/issues/2854)
- Possible to get webhooks from arbitrary repositories [#3057](https://github.com/gogits/gogs/issues/3057)
- When repository name are `.` and `..` cause browser automatic behaviors [#3229](https://github.com/gogits/gogs/issues/3229)

#### Improvements

- Create archives with parent directory in repository name [#518](https://github.com/gogits/gogs/issues/518)
- Use `text/plain` as default email content type [#1496](https://github.com/gogits/gogs/issues/1496)
- Ask user to confirm before leaving page with unsaved changes [#2881](https://github.com/gogits/gogs/issues/2881)
- Private forks will become independent repositories after upstream deletion [#3232](https://github.com/gogits/gogs/pull/3232)

#### Features

- Support prohibit user login [#2937](https://github.com/gogits/gogs/issues/2937)
- Support alphanumeric issue style (ABC-1234) for external issue tracker [#2992](https://github.com/gogits/gogs/issues/2992)
- Support PDF preview [#2993](https://github.com/gogits/gogs/issues/2993)

#### Others

- Add Turkish support

### v0.9.13 @ 2016-03-19

#### Bug fixes

- Site admin cannot see private repositories on organization home page [#2372](https://github.com/gogits/gogs/issues/2372)
- Non-local users can reset their password [#2811](https://github.com/gogits/gogs/issues/2811)
- 500 when compare branches with name contains '#' [#2822](https://github.com/gogits/gogs/issues/2822)
- Potential concurrency issue with builtin SSH server [#2850](https://github.com/gogits/gogs/issues/2850)

#### Improvements

- Set HTML meta values for repository [#2670](https://github.com/gogits/gogs/issues/2670)
- Able to search user with username and full name [#2792](https://github.com/gogits/gogs/issues/2792)

#### Features

- Support search user and repository on both explore page and admin panel [#13](https://github.com/gogits/gogs/issues/13)

### v0.9.0 @ 2016-03-06

#### Bug fixes

- Panic when close issue through commit message [#2697](https://github.com/gogits/gogs/issues/2697)
- Panic when create issue with two or more labels using SQLite3 [#2700](https://github.com/gogits/gogs/issues/2700)

#### Improvements

- Able to test mail settings in admin panel [#1531](https://github.com/gogits/gogs/issues/1531)
- Improve issue lable readability [#2033](https://github.com/gogits/gogs/issues/2033)
- Add config options for Git operation timeout [#2653](https://github.com/gogits/gogs/issues/2653) [#2701](https://github.com/gogits/gogs/issues/2701) [#2704](https://github.com/gogits/gogs/issues/2704)
- Able to delete current avatar of user and organization

#### Features

- More refined collaboration access rights [#1146](https://github.com/gogits/gogs/issues/1146)
- Able to create pull requests between branches in same repository [#1597](https://github.com/gogits/gogs/issues/1597)
- Able to checkout pull requests locally [#1655](https://github.com/gogits/gogs/issues/1655)
- Able to delete Wiki page and entire data [#2183](https://github.com/gogits/gogs/issues/2183)

#### Others

- Add Finnish support

### v0.8.43 @ 2016-02-24

#### Bug fixes

- Old activities still visible for repositories that lost access [#2148](https://github.com/gogits/gogs/issues/2148)
- Issue references have bad links behind a reverse proxy sub-path [#2229](https://github.com/gogits/gogs/issues/2229)
- Line breaks in email is not in HTML format [#2332](https://github.com/gogits/gogs/issues/2332)
- Long webhook URL is truncated [#2465](https://github.com/gogits/gogs/issues/2465)
- Multiple Webhooks with Slack type send wrong payloads [#2485](https://github.com/gogits/gogs/issues/2485)
- Image path breaks when it contains space [#2556](https://github.com/gogits/gogs/issues/2556)
- 500 when edit wiki after transfer the repository [#2558](https://github.com/gogits/gogs/issues/2558)
- 500 after delete user when view releases [#2596](https://github.com/gogits/gogs/issues/2596)
- Wrong `avatar_url` field in webhook payload [#2630](https://github.com/gogits/gogs/issues/2630)

#### Improvements

- Able to config log path on install page [#691](https://github.com/gogits/gogs/issues/691)
- Add `default_branch` field to repository object in webhooks [#1059](https://github.com/gogits/gogs/issues/1059)
- Display activities for close and reopen issues [#1821](https://github.com/gogits/gogs/issues/1821)
- Able to fork mirror repository [#2505](https://github.com/gogits/gogs/issues/2505)
- Highlight code blocks in issue page [#2538](https://github.com/gogits/gogs/pull/2538)

#### Features

- Add config option `[markdown] CUSTOM_URL_SCHEMES` to allows Markdown render custom URL schemes [#2406](https://github.com/gogits/gogs/pull/2406)
- Support syntax highlight on diff view [#2528](https://github.com/gogits/gogs/pull/2528)
- Support convert mirror repository to regular type [#2607](https://github.com/gogits/gogs/issues/2607)

**Older change logs can be found on [GitHub](https://github.com/gogits/gogs/releases?after=v0.8.43).**
