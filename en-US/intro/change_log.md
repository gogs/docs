---
name: Changelog
---

# Changelog

### Unreleased

#### Bug fixes

- Cannot install or start server without mail service
- Out of memory when push large content through HTTP [#636](https://github.com/gogits/gogs/issues/636)
- Cannot navigate to wiki page title contains `-` [#3754](https://github.com/gogits/gogs/issues/3754)
- Cannot edit wiki page title contains `#` [#3767](https://github.com/gogits/gogs/issues/3767)
- Crash when tabular spaces in title of wiki pages [#3916](https://github.com/gogits/gogs/issues/3916)
- Cannot close a milestone using API [#4102](https://github.com/gogits/gogs/issues/4102)
- Repository local copy stops working after force push [#4123](https://github.com/gogits/gogs/issues/4123)
- Cannot delete branch after merging pull request [#4128](https://github.com/gogits/gogs/issues/4128)

#### Improvements

- Add pagination to releases [#2164](https://github.com/gogits/gogs/issues/2164)
- Assign issue to user with read-only access [#3739](https://github.com/gogits/gogs/issues/3739)
- Support short-hash for download archives [#3834](https://github.com/gogits/gogs/issues/3834)

#### Features

- Support Discord webhook
- Support protected branches [#776](https://github.com/gogits/gogs/issues/776)
- Support MSSQL [#3772](https://github.com/gogits/gogs/pull/3772)

### v0.9.141 @ 2017-02-11

#### Bug fixes

- Cannot edit file after rename repository [#3641](https://github.com/gogits/gogs/issues/3641)
- mailto link incorrectly parsed in Markdown [#3790](https://github.com/gogits/gogs/issues/3790)
- Cannot include spaces inside LDAP DN field [#3791](https://github.com/gogits/gogs/issues/3791)
- Pull request on same repository shows 404 [#4074](https://github.com/gogits/gogs/issues/4074)
- Cannot delete branches with slashes in the name [#4089](https://github.com/gogits/gogs/issues/4089)

#### Improvements

- Able to redirect visitors to external issue tracker URL [#3645](https://github.com/gogits/gogs/issues/3645)
- Add Open Graph Meta tags [#3664](https://github.com/gogits/gogs/pull/3664)

#### Features

- Able to disable creation of organizations for non-admins [#1556](https://github.com/gogits/gogs/issues/1556)
- Support IPython Notebook rendering [#4070](https://github.com/gogits/gogs/pull/4070)
- Add Slack logger

#### Others

- Stop supporting network connection and email loggers

### v0.9.128 @ 2017-01-31

#### Bug fixes

- Changed branch not reflected when creating PR [#3604](https://github.com/gogits/gogs/issues/3604)
- Can not save release draft as draft again [#3669](https://github.com/gogits/gogs/issues/3669)
- README file without Markdown is showing empty [#3749](https://github.com/gogits/gogs/issues/3749)
- Incorrect composition when send notification emails [#3856](https://github.com/gogits/gogs/issues/3856)
- Wrong anchors for non-latin headings [#3981](https://github.com/gogits/gogs/issues/3981)
- Panic when try to get a file of bare repository [#3992](https://github.com/gogits/gogs/issues/3992)
- Ability to fork arbitrary repository [#4006](https://github.com/gogits/gogs/issues/4006)
- Users can register with used emails

#### Improvements

- View all issues assigned to me [#1820](https://github.com/gogits/gogs/issues/1820)
- Skip sending emails to inactive users [#3814](https://github.com/gogits/gogs/issues/3814)
- Add new config option `[http] ACCESS_CONTROL_ALLOW_ORIGIN` for custom `Access-Control-Allow-Origin` header [#3987](https://github.com/gogits/gogs/issues/3987)
- Add new config option `[repository] ENABLE_LOCAL_PATH_MIGRATION` to control local path migration (and disabled by default) [#4033](https://github.com/gogits/gogs/issues/4033)

#### Features

- Add 'Organizations' page to user settings [#3587](https://github.com/gogits/gogs/pull/3587)

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

**Older change logs can be found on [GitHub](https://github.com/gogits/gogs/releases?after=v0.9.71).**
