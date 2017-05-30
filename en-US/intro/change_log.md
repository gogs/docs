---
name: Changelog
---

# Changelog

### Unreleased

#### Bug fixes

- Unique constraint violation after backup restored for PostgreSQL [#4357](https://github.com/gogits/gogs/issues/4357)
- Broken relative path for image link in edit file preview [#4368](https://github.com/gogits/gogs/issues/4368)

#### Features

- Support two-factor authentication [#945](https://github.com/gogits/gogs/issues/945)
- Support filter by group membership for LDAP [#4398](https://github.com/gogits/gogs/pull/4398)

#### Improvements

- Installation checks port for SMTP host [#2243](https://github.com/gogits/gogs/issues/2243)
- Remain updated time unchanged if no new commits fetched for mirrors [#4341](https://github.com/gogits/gogs/issues/4341)
- Support IPython notebook as README [#4367](https://github.com/gogits/gogs/issues/4367)

### 0.11.4 @ 2017-04-05

#### Bug fixes

- Client is not informed to provide credentials during HTTP/HTTPS push/pull
- Mirror credentials are not URL encoded [#4014](https://github.com/gogits/gogs/issues/4014)
- Create pull request buttons are showed on branches page when pull request is disabled [#4377](https://github.com/gogits/gogs/issues/4377)
- Panic if user has vaildation error on installation [#4383](https://github.com/gogits/gogs/issues/4383)

### 0.11 @ 2017-04-03

#### Bug fixes

- Profile editing looses changes on validation error [#1123](https://github.com/gogits/gogs/issues/1123)
- Wrong repository count in organization dashboard [#4351](https://github.com/gogits/gogs/issues/4351)
- Fail to migrate from version prior to 0.10 [#4355](https://github.com/gogits/gogs/issues/4355)
- Private repository with public issues didn't handle anonymous visit properly [#4359](https://github.com/gogits/gogs/issues/4359)

### 0.11 RC @ 2017-03-27

#### Bug fixes

- Incorrect file permission for session files [#3363](https://github.com/gogits/gogs/issues/3363)
- API: Repository Permission object returns incorrect values [#4309](https://github.com/gogits/gogs/issues/4309)
- Unable to update non-local user profile [#4313](https://github.com/gogits/gogs/issues/4313)
- Redirect to random issue if index does not exist [#4315](https://github.com/gogits/gogs/issues/4315)
- Unable to propose pull request from secondary fork [#4324](https://github.com/gogits/gogs/issues/4324)
- Unable to update protect branch whitelist [#4333](https://github.com/gogits/gogs/issues/4333)
- Repository size does not update for fork, migrate and mirror [#4336](https://github.com/gogits/gogs/issues/4336)

#### Features

- Support private repository with public issues [#649](https://github.com/gogits/gogs/issues/649)
- Support private repository with public wiki [#2157](https://github.com/gogits/gogs/issues/2157)
- Able to retrigger webhook history [#2187](https://github.com/gogits/gogs/issues/2187)
- API: Add sync for mirror repository [#2235](https://github.com/gogits/gogs/issues/2235)
- Able to load more feeds on dashboard [#2511](https://github.com/gogits/gogs/issues/2511)
- Add config option to set a cookie value indicates login status [#2885](https://github.com/gogits/gogs/issues/2885)
- Able to backup and restore [#2924](https://github.com/gogits/gogs/issues/2924)
- Able to use issues and wiki for bare repository [#4104](https://github.com/gogits/gogs/issues/4104)
- Custom page size for commits page [#4230](https://github.com/gogits/gogs/issues/4230)
- Add repositories panel to user settings [#4277](https://github.com/gogits/gogs/issues/4277)

#### Improvements

- Include private but accessible repositories in explore page [#3088](https://github.com/gogits/gogs/issues/3088)
- Able to choose console mode for logger [#3119](https://github.com/gogits/gogs/issues/3119)
- Able to config logger for XORM [#3183](https://github.com/gogits/gogs/issues/3183)
- Add config option for HTML render mode [#3608](https://github.com/gogits/gogs/issues/3608)
- Webhook push event provice details about added/removed/modified files [#3897](https://github.com/gogits/gogs/issues/3897)
- Able to config number of newsfeed showed on Dashboard [#4247](https://github.com/gogits/gogs/issues/4247)

### 0.10.18 @ 2017-03-14

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

**Older change logs can be found on [GitHub](https://github.com/gogits/gogs/releases?after=v0.10).**
