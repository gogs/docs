---
name: 已知问题
sort: 2
---

# 已知问题

本文档告知了所有在最新版本 **release(v0.4.2)** 中存在的问题。了解这些问题可以避免不必要的异常并提升用户体验。其中一些问题可能会在最新的源码中被修复，您可以通过查看 [变更日志](change_log.md) 来进行追踪。

任何提到与版本有关的叙述（如：`v0.4.0`）都不是绝对的，但是是最可能被修复的版本。

### 兼容性

### 仓库

#### Tag

- 当 tag 名称包含 `/` 时会发生 panic [#101](https://github.com/gogits/gogs/issues/101)。

### Git

#### `git push` with error `cannot find parent commit of XXX`

根据我们目前的测试结果来看，这个问题是由于使用指定深度的克隆操作 `git clone --depth=XX` 导致的。

### 用户界面

#### 仓库浏览器(URL：`/:username/:reponame`)

- SSH/HTTPS 面板切换和单击复制在火狐浏览器下无法工作。