---
name: Changelog
---

# Changelog

### Unreleased

#### Added

- Allow admin to remove observers from the repository [#5803](https://github.com/gogs/gogs/pull/5803)
- Use `Last-Modified` HTTP header for raw files [#5811](https://github.com/gogs/gogs/issues/5811)
- Support syntax highlighting for SAS code files (`.r`, `.sas`, `.tex`, `.yaml`) [#5856](https://github.com/gogs/gogs/pull/5856)

#### Changed

#### Fixed

- [Security] Potential RCE on mirror repositories [#5767](https://github.com/gogs/gogs/issues/5767)
- Disallow multiple tokens with same name [#5587](https://github.com/gogs/gogs/issues/5587) [#5820](https://github.com/gogs/gogs/pull/5820)
- Enable Federated Avatar Lookup could cause server to crash [#5848](https://github.com/gogs/gogs/issues/5848)

#### Others

### 0.11.91 @ 2019-08-11

#### Bug fixes

- MySQL: invalid connection [#5532](https://github.com/gogs/gogs/issues/5532)
- Docker: Deprecation Notice OpenSSH [#5647](https://github.com/gogs/gogs/issues/5647)
- Copyright is behind the times [#5674](https://github.com/gogs/gogs/issues/5674)
- [Security] Incorrect API access control [#5764](https://github.com/gogs/gogs/issues/5764)

#### Improvements

- Assignee receives email updates of issue thread [#4220](https://github.com/gogs/gogs/issues/4220)
- Render Markdown in emails [#4552](https://github.com/gogs/gogs/issues/4552)
- Add `rsync` to the Docker image [#5773](https://github.com/gogs/gogs/pull/5773)

### 0.11.86 @ 2019-01-30

#### Bug fixes

- Layout misalignment in Firefox for Linux [#5299](https://github.com/gogs/gogs/issues/5299)
- Unexpected issue index parsing error while using external issue tracker [#5551](https://github.com/gogs/gogs/issues/5551)
- [Security] Remote Code execution or/and Denial of Service [#5558](https://github.com/gogs/gogs/issues/5558)

#### Features

- Support GitHub (Enterprise) authentication source [#5340](https://github.com/gogs/gogs/pull/5340)
- Add API endpoint to get commit details by SHA [#5546](https://github.com/gogs/gogs/pull/5546)

#### Others

- Add new languages support: Portuguese

### 0.11.79 @ 2018-12-11

#### Bug fixes

- LDAP group verification doesn't work when using 'dn' as user attribute [#4684](https://github.com/gogs/gogs/issues/4684)
- LDAP group verification fails [#4792](https://github.com/gogs/gogs/issues/4792)
- Emoji's do not work in wiki [#4869](https://github.com/gogs/gogs/issues/4869)
- Log level not applied from configuration [#5007](https://github.com/gogs/gogs/issues/5007)
- Not able to go get a repository with non-80 port [#5305](https://github.com/gogs/gogs/issues/5305)
- Fix critical CSRF vulnerabilities on API routes [#5355](https://github.com/gogs/gogs/issues/5355)
- Wrong redirect after updated protect branch setting whose name contains `#` [#5442](https://github.com/gogs/gogs/issues/5442)
- Clear labels not working [#5445](https://github.com/gogs/gogs/issues/5445)
- [Security] Remote command execution [#5469](https://github.com/gogs/gogs/issues/5469)
- Push event webhook is not triggered when new branch fetched to mirror repository [#5473](https://github.com/gogs/gogs/issues/5473)
- Large issue comment exceeds dashboard section [#5502](https://github.com/gogs/gogs/issues/5502)
- List collaborator API does not contain permission information [#5538](https://github.com/gogs/gogs/issues/5538)
- [Security] Log out only deletes browser cookies [#5540](https://github.com/gogs/gogs/issues/5540)
- [Security] Some routes need to be POST [#5541](https://github.com/gogs/gogs/issues/5541)
- [Security] Stored XSS in external issue tracker URL format [#5545](https://github.com/gogs/gogs/issues/5545)

#### Improvements

- Support prefilling the title and body of new issues using query parameters [#5302](https://github.com/gogs/gogs/issues/5302)
- Support data URL of base64 encoded images in Markdown [#5391](https://github.com/gogs/gogs/pull/5391)
- Allow non logged in users to call repository information API `/repos/:username/:reponame` [#5475](https://github.com/gogs/gogs/issues/5475)

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

**Older change logs can be found on [GitHub](https://github.com/gogs/gogs/releases?after=v0.11.33).**
