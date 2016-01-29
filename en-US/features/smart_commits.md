---
name: Smart Commits
---

# Smart Commits

Gogs supports few syntaxes in your commit messages to control issues. This feature only supports commits and issues are in the same repository currently.

## Referencing an issue

To reference an issue in your commit message, simple use syntax `#18`, and then there will be a reference message in the corresponding issues. 

Multiple references to the same issue in single commit message will only produce one reference message.

## Closing and reopening an issue

To close or reopen an issue, you must use the syntax `<action keyword> #<issue id>`. For example, to simply close an issue by using `fix #18`, or reopen it in the next commit by using `reopen #18`.

The following list shows all available keywords for closing and reopening an issue:

- Close: `close`, `closes`, `closed`, `fix`, `fixes`, `fixed`, `resolve`, `resolves`, `resolved`
- Reopen: `reopen`, `reopens`, `reopened`

