---
name: Changelog
---

# Changelog

### Unreleased

#### Bug fixes

- Wrong branch URL for name contains `#` in branches view [#4874](https://github.com/gogits/gogs/issues/4874)
- SVG support in IPython notebook [#5077](https://github.com/gogits/gogs/issues/5077)

#### Improvements

- Support HTTP HEAD requests [#2857](https://github.com/gogits/gogs/issues/2857)

#### Others

- Add new languages support: Indonesian, Persian 

### 0.11.34 @ 2017-11-22

#### Bug fixes

- *Regression*: Pull request is not working between different repositories [#4890](https://github.com/gogits/gogs/issues/4890)

### 0.11.33 @ 2017-11-19

#### Bug fixes

- Some security fixes
- Wrong commit ID in webhook payload after merging pull request [#4442](https://github.com/gogits/gogs/issues/4442)
- Meta tag go-import does not response correct value [#4832](https://github.com/gogits/gogs/issues/4832)

#### Features

- Add Dingtalk webhook support [#4773](https://github.com/gogits/gogs/pull/4773)
- Allow rebase and merge pull request [#4798](https://github.com/gogits/gogs/issues/4798)

#### Improvements

- Add placeholder '%s' for username in LDAP BindDN [#2526](https://github.com/gogits/gogs/issues/2526)
- Allow UID for git user in Docker container to be specified via ENV variable [#3520](https://github.com/gogits/gogs/issues/3520)
- Add repository setting to ignore whitespace when check pull request conflict [#4834](https://github.com/gogits/gogs/issues/4834)

#### Others

- Add new language support: Slovak

### 0.11.29 @ 2017-08-15

#### Bug fixes

- Private repository activity shown in "Public activity" tab, if the repository was once public [#4414](https://github.com/gogits/gogs/issues/4414)
- Webhooks refuse IPv6 URLs as invalid [#4428](https://github.com/gogits/gogs/issues/4428)
- No email notification if issue closed by commit [#4430](https://github.com/gogits/gogs/issues/4430)
- Explore page incorrect paging [#4441](https://github.com/gogits/gogs/issues/4441)
- `/api/v1/repos/search` returns empty values [#4522](https://github.com/gogits/gogs/issues/4522)
- Panic after created a pull request [#4572](https://github.com/gogits/gogs/issues/4572)

### 0.11.19 @ 2017-06-10

#### Bug fixes

- Unable to go get subpkg [#1878](https://github.com/gogits/gogs/issues/1878)
- Does not set as admin after first LDAP login [#2855](https://github.com/gogits/gogs/issues/2855)
- Panic when login via PAM [#4216](https://github.com/gogits/gogs/issues/4216)
- Unique constraint violation after backup restored for PostgreSQL [#4357](https://github.com/gogits/gogs/issues/4357)
- Images in IPython notebook are not displayed [#4366](https://github.com/gogits/gogs/issues/4366)
- Broken relative path for image link in edit file preview [#4368](https://github.com/gogits/gogs/issues/4368)
- Emoji not rendered on commits view [#4439](https://github.com/gogits/gogs/issues/4439)
- High CPU when view single commit contains file mode change [#4475](https://github.com/gogits/gogs/issues/4475)
- Cannot change permissions of collaborators [#4512](https://github.com/gogits/gogs/issues/4512)

#### Features

- Support two-factor authentication [#945](https://github.com/gogits/gogs/issues/945)
- Support filter by group membership for LDAP [#4398](https://github.com/gogits/gogs/pull/4398)

#### Improvements

- Installation checks port for SMTP host [#2243](https://github.com/gogits/gogs/issues/2243)
- Remain updated time unchanged if no new commits fetched for mirrors [#4341](https://github.com/gogits/gogs/issues/4341)
- Support IPython notebook as README [#4367](https://github.com/gogits/gogs/issues/4367)
- Configurable TLS Support [#4450](https://github.com/gogits/gogs/issues/4450)

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

**Older change logs can be found on [GitHub](https://github.com/gogits/gogs/releases?after=v0.11rc).**
