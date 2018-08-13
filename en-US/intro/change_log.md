---
name: Changelog
---

# Changelog

### Unreleased

#### Bug fixes

- Private repository with public wiki or issue does not show in search result [#4973](https://github.com/gogs/gogs/issues/4973)
- Cannot start with MySQL 8.0 [#5187](https://github.com/gogs/gogs/issues/5187)
- Webhook and its tasks are not cleaned up when delete repository [#5229](https://github.com/gogs/gogs/issues/5229)
- Time set to current after restored from backup [#5264](https://github.com/gogs/gogs/issues/5264)

#### Improvements

- Ignore configuration inline comment by default
- Able to add custom merge commit description [#5276](https://github.com/gogs/gogs/pull/5276)

### 0.11.53 @ 2018-06-05

#### Bug fixes

- The branch name contains '#' not work correctly [#4601](https://github.com/gogs/gogs/issues/4601)
- Issue mention does not render with square brackets [#4706](https://github.com/gogs/gogs/issues/4706)
- 500 when merge branch when the base branch is not the default branch [#5138](https://github.com/gogs/gogs/issues/5138)
- Gravatar URLs are badly generated [#5157](https://github.com/gogs/gogs/issues/5157)
- Able to reuse two factor passcode
- Config option `[git] GC_ARGS` does not take effect

#### Features

- Show mirror updates in activity timeline [#2017](https://github.com/gogs/gogs/issues/2017)
- Support authentication source config file [#3142](https://github.com/gogs/gogs/issues/3142)
- Trigger webhook after mirror sync [#4528](https://github.com/gogs/gogs/issues/4528)

#### Others

- Changed import path from "gogits/gogs" to "gogs/gogs"
- Security fixes
- Add new languages support: Vietnamese

### 0.11.43 @ 2018-03-31

#### Bug fixes

- Protected branch can be deleted from the web after merge request [#4514](https://github.com/gogs/gogs/issues/4514)
- Does not recognise SYSNAME datatype in MSSQL [#4642](https://github.com/gogs/gogs/issues/4642)
- Quick guide is only showed for repository admin [#4646](https://github.com/gogs/gogs/issues/4646)
- Wrong branch URL for name contains `#` in branches view [#4874](https://github.com/gogs/gogs/issues/4874)
- Commits not merged after accepting pull request using rebase [#5051](https://github.com/gogs/gogs/issues/5051)
- Once branch was protected "Lock" icon will never be removed [#5053](https://github.com/gogs/gogs/issues/5053)
- SVG support in IPython notebook [#5077](https://github.com/gogs/gogs/issues/5077)

#### Improvements

- Support HTTP HEAD requests [#2857](https://github.com/gogs/gogs/issues/2857)
- Add option to rewrite authorized_keys file at start [#4435](https://github.com/gogs/gogs/issues/4435)
- Add option to prepend global prefix to the email subject [#4524](https://github.com/gogs/gogs/issues/4524)
- Disable federated avatar lookup by default [#5126](https://github.com/gogs/gogs/pull/5126)

#### Others

- Add new languages support: Indonesian, Persian 

### 0.11.34 @ 2017-11-22

#### Bug fixes

- *Regression*: Pull request is not working between different repositories [#4890](https://github.com/gogs/gogs/issues/4890)

### 0.11.33 @ 2017-11-19

#### Bug fixes

- Some security fixes
- Wrong commit ID in webhook payload after merging pull request [#4442](https://github.com/gogs/gogs/issues/4442)
- Meta tag go-import does not response correct value [#4832](https://github.com/gogs/gogs/issues/4832)

#### Features

- Add Dingtalk webhook support [#4773](https://github.com/gogs/gogs/pull/4773)
- Allow rebase and merge pull request [#4798](https://github.com/gogs/gogs/issues/4798)

#### Improvements

- Add placeholder '%s' for username in LDAP BindDN [#2526](https://github.com/gogs/gogs/issues/2526)
- Allow UID for git user in Docker container to be specified via ENV variable [#3520](https://github.com/gogs/gogs/issues/3520)
- Add repository setting to ignore whitespace when check pull request conflict [#4834](https://github.com/gogs/gogs/issues/4834)

#### Others

- Add new language support: Slovak

### 0.11.29 @ 2017-08-15

#### Bug fixes

- Private repository activity shown in "Public activity" tab, if the repository was once public [#4414](https://github.com/gogs/gogs/issues/4414)
- Webhooks refuse IPv6 URLs as invalid [#4428](https://github.com/gogs/gogs/issues/4428)
- No email notification if issue closed by commit [#4430](https://github.com/gogs/gogs/issues/4430)
- Explore page incorrect paging [#4441](https://github.com/gogs/gogs/issues/4441)
- `/api/v1/repos/search` returns empty values [#4522](https://github.com/gogs/gogs/issues/4522)
- Panic after created a pull request [#4572](https://github.com/gogs/gogs/issues/4572)

### 0.11.19 @ 2017-06-10

#### Bug fixes

- Unable to go get subpkg [#1878](https://github.com/gogs/gogs/issues/1878)
- Does not set as admin after first LDAP login [#2855](https://github.com/gogs/gogs/issues/2855)
- Panic when login via PAM [#4216](https://github.com/gogs/gogs/issues/4216)
- Unique constraint violation after backup restored for PostgreSQL [#4357](https://github.com/gogs/gogs/issues/4357)
- Images in IPython notebook are not displayed [#4366](https://github.com/gogs/gogs/issues/4366)
- Broken relative path for image link in edit file preview [#4368](https://github.com/gogs/gogs/issues/4368)
- Emoji not rendered on commits view [#4439](https://github.com/gogs/gogs/issues/4439)
- High CPU when view single commit contains file mode change [#4475](https://github.com/gogs/gogs/issues/4475)
- Cannot change permissions of collaborators [#4512](https://github.com/gogs/gogs/issues/4512)

#### Features

- Support two-factor authentication [#945](https://github.com/gogs/gogs/issues/945)
- Support filter by group membership for LDAP [#4398](https://github.com/gogs/gogs/pull/4398)

#### Improvements

- Installation checks port for SMTP host [#2243](https://github.com/gogs/gogs/issues/2243)
- Remain updated time unchanged if no new commits fetched for mirrors [#4341](https://github.com/gogs/gogs/issues/4341)
- Support IPython notebook as README [#4367](https://github.com/gogs/gogs/issues/4367)
- Configurable TLS Support [#4450](https://github.com/gogs/gogs/issues/4450)

**Older change logs can be found on [GitHub](https://github.com/gogs/gogs/releases?after=v0.11.19).**
