---
name: Known Issues
sort: 2
---

# Known Issues

This sheet shows the known issues with latest **release(v0.3.1)** version, be aware of them will reduce exceptions and improve your user experience. Some of them might be fixed in up-to-date code. See [Change Log](change_log.md) for getting up-to-date information about what issue has been fixed since last release.

Anything that is related to some version(e.g. `v0.4.0`) is not a promise but a early stage plan.

### Compatibility

#### Go

Undetermined error in Go tip, please use Go 1.2 or Go 1.2.1.

#### Issue

We're going to add a new issue-user relation table for recording statistic information of an issue and a user in a repository in `v0.4.0`, so the current statistic system of issue will be replaced, which program still works with data that are created before `v0.4.0` but has wrong statistic information.

### Repository

#### Tag

- Panic when Tag name contains `/`.

### Git

#### `git push` with error `cannot find parent commit of XXX`

As we've testes so far, this error only occurs when your repository was cloned by something like `git clone --depth=XX` which specified the depth of clone.

### UI

#### Repository viewer(URL: `/:username/:reponame`)

- SSH/HTTPS switch and one-click copy button doesn't work under Firefox