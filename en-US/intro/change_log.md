---
name: Changelog
---

# Changelog

### Unreleased

#### Bug fixes

- Wrong redirect after updated protect branch setting whose name contains `#` [#5442](https://github.com/gogs/gogs/issues/5442)
- Large issue comment exceeds dashboard section [#5502](https://github.com/gogs/gogs/issues/5502)

#### Others

- Security fixes

### 0.11.66 @ 2018-09-16

#### Bug fixes

- Web editor doesn't execute hooks after commit [#4338](https://github.com/gogs/gogs/issues/4338)
- Release attachments are deleted when delete any random comment [#4627](https://github.com/gogs/gogs/issues/4627)
- Private repository with public wiki or issue does not show in search result [#4973](https://github.com/gogs/gogs/issues/4973)
- Cannot start with MySQL 8.0 [#5187](https://github.com/gogs/gogs/issues/5187)
- Webhook and its tasks are not cleaned up when delete repository [#5229](https://github.com/gogs/gogs/issues/5229)
- Time set to current after restored from backup [#5264](https://github.com/gogs/gogs/issues/5264)
- Delete branch after merged pull request does no trigger webhook [#5331](https://github.com/gogs/gogs/issues/5331)
- Fork repository does not check of the limit of users [#5345](https://github.com/gogs/gogs/issues/5345)
- Unable to delete user with PostgreSQL [#5376](https://github.com/gogs/gogs/issues/5376)

#### Features

- Able to add avatar for repository [#2340](https://github.com/gogs/gogs/issues/2340)
- Add basic Go runtime metrics provided by Prometheus [#4141](https://github.com/gogs/gogs/issues/4141)

#### Improvements

- Ignore configuration inline comment by default
- Add deletion of an empty line at the end of file in file view [#5270](https://github.com/gogs/gogs/pull/5270)
- Able to set default authentication method for login [#5274](https://github.com/gogs/gogs/issues/5274)
- Able to add custom merge commit description [#5276](https://github.com/gogs/gogs/pull/5276)

#### Others

- Security fixes

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

**Older change logs can be found on [GitHub](https://github.com/gogs/gogs/releases?after=v0.11.29).**
