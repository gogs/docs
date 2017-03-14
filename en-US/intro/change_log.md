---
name: Changelog
---

# Changelog

### Unreleased

#### Bug fixes

- Last updated is not changed after syncing for mirror repositories [#2807](https://github.com/gogits/gogs/issues/2807)
- **Regression** Cannot edit or view draft release [#4262](https://github.com/gogits/gogs/issues/4262)

#### Improvements

- More webhook events
- Send notification emails to all issue participants [#2929](https://github.com/gogits/gogs/issues/2929)
- Whitelist users can bypass require pull request check for protected branches [#4207](https://github.com/gogits/gogs/issues/4207)

#### Features

- Able to view repository size in admin panel
- Support add attachments to releases [#1614](https://github.com/gogits/gogs/issues/1614)
- Repository branches page [#2310](https://github.com/gogits/gogs/issues/2310)
- Support Smartypants with config section `[smartypants]` [#4162](https://github.com/gogits/gogs/issues/4162)

### 0.10.8 @ 2017-03-07

#### Bug fixes

- Git hooks do not work on Windows `mws` version
- link contains an image does not point to the correct URL [#2636](https://github.com/gogits/gogs/issues/2636)
- Web editor cannot create branch with slash [#3568](https://github.com/gogits/gogs/issues/3568)
- Cannot clone a repository without `.git` suffix [#4189](https://github.com/gogits/gogs/issues/4189)
- Git hook working directory is not repository directory [#4225](https://github.com/gogits/gogs/issues/4225)
- Regression on `go get` support [#4226](https://github.com/gogits/gogs/issues/4226)
- Webhook Skip TLS Verify setting doesn't take effect [#4228](https://github.com/gogits/gogs/issues/4228)

#### Improvements

- Use `text/html` as default email content encoding and use `[mailer] USE_PLAIN_TEXT` to disable it
- Able to perform initial commit on behave of actual user
- Support Gogs-related environment variables for Git hooks [#4094](https://github.com/gogits/gogs/issues/4094)

### 0.10.1 @ 2017-02-28

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

**Older change logs can be found on [GitHub](https://github.com/gogits/gogs/releases?after=v0.9.128).**
