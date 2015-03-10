---
name: On Windows
sort: 6
---

## Binary install Gogs on Windows 7

> Contrbutied by [@victorsegall](https://github.com/victorsegall)

### Run as current local user

Gogs is able to run as local user immediately, with no configuration. Simply unpack the [Windows binary](http://gogs.io/docs/installation/install_from_binary.html) zip file somewhere, go to command line, and do:

```
C:>cd C:\path\to\gogs
C:\path\to\gogs>gogs web
```

We'll assume you chose `C:\gogs`

At this point, Gogs should be available at `http://127.0.0.1:3000`, and the first-run installer will guide you through the rest. 

Gogs will be using both `C:\Users\your_username` and `C:\gogs` for file operations.

In `C:\gogs`, Gogs will need write access to:

```
C:\gogs\custom\conf
C:\gogs\data
C:\gogs\log
```

Those are made during its first run, which assumes it then had write access to `C:\gogs`. Create them before first run if that is not true.

If it doesn't exist, Gogs will create `C:\Users\your_username\.gitconfig` with the following:

```
[user]
	name = Gogs
	email = gogitservice@gmail.com
```

That [can be changed to whatever you like](http://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup), and it should be. It is the user to which all of your git operations will be attributed to. It can also be overridden per-repository, through `C:\path\to\repo\.git\config`

By default, Gogs managed repositories are in C:\Users\your_username\gogs-repositories

These will be bare repositories, with no working directory. You can clone them locally through the filesystem, with git.exe (which was required in [installation](http://gogs.io/docs/installation/)), or with [TortoiseGit](https://code.google.com/p/tortoisegit/) if you prefer working through Windows Explorer.


