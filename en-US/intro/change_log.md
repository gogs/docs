---
name: Changelog
---

# Changelog

### v0.9.71 @ 2016-08-10

#### Bug fixes

- Release date does not use tag's create date when exist [#3315](https://github.com/gogits/gogs/issues/3315)
- JavaScript line number breaks syntax highlighting element block [#3316](https://github.com/gogits/gogs/issues/3316)
- Images breaks when use reverse proxy [#3348](https://github.com/gogits/gogs/issues/3348)
- 500 when user leaves organization without relations to any repositories [#3379](https://github.com/gogits/gogs/issues/3379)
- Pull request conflict status not updating properly [#3396](https://github.com/gogits/gogs/issues/3396)
- Dashboard issues for organisations is limited to `num_repos` from the user [#3410](https://github.com/gogits/gogs/issues/3410)
- Wrong dashboard issue count for create by you category [#3417](https://github.com/gogits/gogs/issues/3417)

#### Improvements

- Always response with go-import metadata when `?go-get=1` [#2825](https://github.com/gogits/gogs/issues/2825)
- Add config option `[git.timeout] GC` for Git GC timeout [#3091](https://github.com/gogits/gogs/issues/3091)
- Skip `RUN_USER` check on Windows [#3158](https://github.com/gogits/gogs/issues/3158)
- Add config option `[mirror] DEFAULT_INTERVAL` for default interval of mirror checking [#3091](https://github.com/gogits/gogs/issues/3091)

#### Features

- Support federated avatars
- Allow use `?render=1` to set HTML rendered in raw mode [#2593](https://github.com/gogits/gogs/issues/2593)

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

**Older change logs can be found on [GitHub](https://github.com/gogits/gogs/releases?after=v0.9.13).**
