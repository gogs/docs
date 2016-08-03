---
name: Changelog
---

# Changelog

### v0.9.60 @ 2016-08-03

#### Bug fixes

- Diff split view not working on pull requests [#2790](https://github.com/gogits/gogs/issues/2790)
- 500 when creating a release with an invalid tag name [#3076](https://github.com/gogits/gogs/issues/3076)
- Cannot mention user name contains dash [#3107](https://github.com/gogits/gogs/issues/3107)
- 500 after delete base branch of pull request [#3181](https://github.com/gogits/gogs/issues/3181)
- Wrong link of new pull request of fork repositories [#3186](https://github.com/gogits/gogs/issues/3186)
- 500 when filtering issues by label [#3327](https://github.com/gogits/gogs/issues/3327)

#### Improvements

- Add pagination for repositories [#1384](https://github.com/gogits/gogs/issues/1384)
- Use different reversed word and pattern list for repository and user [#2903](https://github.com/gogits/gogs/issues/2903)

#### Features

- Add issue labels APIs 
- Support delete issue comment [#1601](https://github.com/gogits/gogs/issues/1601)
- Support download diff as patch [#2641](https://github.com/gogits/gogs/issues/2641)

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

**Older change logs can be found on [GitHub](https://github.com/gogits/gogs/releases?after=v0.9.0).**
