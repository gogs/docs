---
name: Changelog
---

# Changelog

### Unreleased

#### Bug fixes

- Wrong anchors for non-latin headings [#3981](https://github.com/gogits/gogs/issues/3981)

#### Improvements

- View all issues assigned to me [#1820](https://github.com/gogits/gogs/issues/1820)

### v0.9.113 @ 2016-12-24

#### Bug fixes

- HTTP push consumes a lot of RAM [#636](https://github.com/gogits/gogs/issues/636)
- Dashboard feeds has unexpected line break on Mac OS X Safari [#2875](https://github.com/gogits/gogs/issues/2875)
- Wrong avatar link for user [#3577](https://github.com/gogits/gogs/issues/3577)
- 404 on release draft edition [#3590](https://github.com/gogits/gogs/issues/3590)
- 500 when issue poster has deleted account
- Ability to delete other people's secondary emails and application's tokens [#3959](https://github.com/gogits/gogs/issues/3959)
- Ability to delete arbitrary repository's releases [#3962](https://github.com/gogits/gogs/issues/3962)
- Ability to use labels from arbitrary repositories

#### Improvements

- Add config option `[other] SHOW_FOOTER_TEMPLATE_LOAD_TIME` to hide template load time [#3492](https://github.com/gogits/gogs/issues/3492)

#### Features

- Support search organizations on explore page [#2951](https://github.com/gogits/gogs/issues/2951)
- Provide button to delete merged pull request branch [#3225](https://github.com/gogits/gogs/pull/3225)
- Support disable HTTP operations of repository [#3667](https://github.com/gogits/gogs/pull/3667)
- Support for video files using the HTML5 video tag [#3967](https://github.com/gogits/gogs/pull/3967)

#### Others

- Add Korean and Galician support

### v0.9.97 @ 2016-09-01

#### Bug fixes

- Only user with repository write access can make comments 
- Diff signs (+/-) are not showing [#3464](https://github.com/gogits/gogs/pull/3464)
- Archive includes full path on Windows [#3535](https://github.com/gogits/gogs/pull/3535)

#### Improvements

- Add git-daemon-export-ok support [#2940](https://github.com/gogits/gogs/issues/2940)
- Redirect to landing page after login [#3089](https://github.com/gogits/gogs/issues/3089)
- Use user name as email FROM value [#3279](https://github.com/gogits/gogs/issues/3279)

#### Features

- Support lable templates [#1562](https://github.com/gogits/gogs/issues/1562)
- Support sync mirror repository on UI [#2018](https://github.com/gogits/gogs/issues/2018)
- Support webhooks for pull requests [#2246](https://github.com/gogits/gogs/pull/2246)
- Support listen on unix socket [#2852](https://github.com/gogits/gogs/pull/2852)
- Support PostgreSQL with unix socket [#3013](https://github.com/gogits/gogs/issues/3013)
- Support migrate wiki with repository when available [#3233](https://github.com/gogits/gogs/pull/3233)
- Support web editor for repository files [#3460](https://github.com/gogits/gogs/issues/3460)

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

**Older change logs can be found on [GitHub](https://github.com/gogits/gogs/releases?after=v0.9.46).**
