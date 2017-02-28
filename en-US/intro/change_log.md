---
name: Changelog
---

# Changelog

### 0.10.1 @ 2017-02-29

#### Bug fixes

- Non-organizational repository cannot save branch protection options

### 0.10 @ 2017-02-27

#### Bug fixes

- Unexpected removal of migrated repository when wiki is detected
- Cannot preview diff on web editor
- Organizational webhook last delivery status cannot be updated
- Admin cannot delete organizational repository
- Diff split view doesn't work on create pull reqeust [#3695](https://github.com/gogits/gogs/issues/3695)
- Cannot edit release of fork repository [#4174](https://github.com/gogits/gogs/issues/4174)

#### Improvements

- Able to add organization member as repository collaborator
- Able to add custom head/footer [#1286](https://github.com/gogits/gogs/issues/1286)
- Able to send test delivery for specific webhook [#3030](https://github.com/gogits/gogs/issues/3030)
- Able to enable webhook types on choice [#3356](https://github.com/gogits/gogs/issues/3356)
- Able to send SHA256 HMAC hex digest for webhooks [#3692](https://github.com/gogits/gogs/issues/3692)
- Add config option `[session] CSRF_COOKIE_NAME` for custom CSRF cookie name [#4172](https://github.com/gogits/gogs/issues/4172)
- Able to whitelist users and teams for protect branch of organizational repository [#4177](https://github.com/gogits/gogs/issues/4177)

### 0.10 RC @ 2017-02-21

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

- Able to fork own repository [#1791](https://github.com/gogits/gogs/issues/1791)
- Add pagination to releases [#2164](https://github.com/gogits/gogs/issues/2164)
- Assign issue to user with read-only access [#3739](https://github.com/gogits/gogs/issues/3739)
- Support short-hash for download archives [#3834](https://github.com/gogits/gogs/issues/3834)
- Highlight a line on diff view

#### Features

- Support Discord webhook
- Support protected branches [#776](https://github.com/gogits/gogs/issues/776)
- Support MSSQL [#3772](https://github.com/gogits/gogs/pull/3772)

#### Others

- Stop supporting 0.6.x

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

**Older change logs can be found on [GitHub](https://github.com/gogits/gogs/releases?after=v0.9.113).**
