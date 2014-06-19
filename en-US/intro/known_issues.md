---
name: Known Issues
sort: 2
---

# Known Issues

This sheet shows the known issues with latest **release(v0.4.2)** version, be aware of them will reduce exceptions and improve your user experience. Some of them might be fixed in up-to-date code. See [Change Log](change_log.md) for getting up-to-date information about what issue has been fixed since last release.

Anything that is related to some version(e.g. `v0.4.0`) is not a promise but a early stage plan.

### Compatibility

### Repository

#### Tag

- Panic when Tag name contains `/` [#101](https://github.com/gogits/gogs/issues/101).

### Git

#### `git push` with error `cannot find parent commit of XXX`

As we've testes so far, this error only occurs when your repository was cloned by something like `git clone --depth=XX` which specified the depth of clone.

### UI

#### Repository viewer(URL: `/:username/:reponame`)

- SSH/HTTPS switch and one-click copy button doesn't work under Firefox