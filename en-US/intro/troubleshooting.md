---
name: Troubleshooting
---

# Troubleshooting

## Installation

- Error: `../gosrc/src/github.com/gogits/gogs/cmd/cert.go:79: undefined: elliptic.P224`
- Causes: golang package in RHEL/CentOS does not support Elliptic Curve cryptography (because it's patented) and it's specifically removed from CentOS/RHEL.
- Solution: download and install Go from [golang.org/dl](http://golang.org/dl).

## SSH

#### SSH connection hangs for 60 seconds

- Causes: Gogs will request itself (web service) after every SSH push, and your server firewall or ISP does not allow that happen

#### Incorrect binary path for update hook

- Causes: you moved Gogs binary to a different location from previous installation. 
- Solution: go to admin dashboard (`/admin`) and run two tasks:
	- `Rewrite '.ssh/authorized_keys' file`
	- `Rewrite all update hook of repositories`

## Git

#### Public key conflict

- Error:
	- `fatal: 'XX/XX.git' does not appear to be a git repository`
	- Pushed commits but still shows as a bare repository
- Causes: there are duplicated SSH keys in `~/.ssh/authorized_keys` file, possibly you are/were using GitLab for same system user.
- Solution: delete the old one and keep the one that was added by Gogs only.

#### Cannot call 'git' command by Gogs

- Error: `repo.NewRepoContext(fail to set git user.email):`
- Causes: it happens when Windows users install Git Bash without enabling the `cmd` option
- Solution: reinstall and enable `cmd` option.

## Form Validation

- Error: `Repository/User name contains illegal characters`
- Causes: in order to prevent unexpected exceptions, your user/repository name will be considered as illegal if they match any of the following rules:
	- Name equals to any word of `"debug", "raw", "install", "api", "avatar", "user", "org", "help", "stars", "issues", "pulls", "commits", "repo", "template", "admin", "new"`.
	- Name has suffix `".git", ".keys"`.

## Cache

- Error: `cache: unknown adaptername "memcache" (forgotten import?)`
- Causes: To prevent unnecessary import of package, we use build tags to specify when needed
- Solution:
	- Download: `go get -tags memcache github.com/gogits/gogs`
	- Build: `go build -tags memcache`
	- Same steps for `redis` when you want it to be the cache adapter.

## Database 

#### Incorrect MySQL storate engine

- Error: `Error 1071: Specified key was too long; max key length is 1000 bytes`
- Causes: it is caused by MyISAM.
- Solution: Once you import the `config/mysql.sql` then login into mysql and run:

	```sql
	use gogs;
	set global storage_engine=INNODB;
	```

After that, go to [http://localhost:3000/install](http://localhost:3000/install) and everything works fine(thanks [@linc01n](https://github.com/linc01n)).

#### Outdated MySQL password setting

- Error: `Database setting is not correct: This server only supports the insecure old password authentication. If you still want to use it, please add 'allowOldPasswords=1' to your DSN. See also https://github.com/go-sql-driver/mysql/wiki/old_passwords`
- Causes: only updated the password for @localhost -- there was a second entry in the user table where @% still had the old password.
- Solution: [GitHub comments](https://github.com/gogits/gogs/issues/385#issuecomment-54357073)

#### Connect to wrong SQLite3 database

- Error: Push to repository shows owner is not registered.
- Causes: You might start Gogs as service and it is using different SQLite3 file that you expect.
- Solution: Use absolute path to config SQLite3 database path.

## Mailer

- Error: Gmail with Error 534: `Please log in via your web browser and then try again`
- Causes: this is because Google does not trust your server
- Solution:
	- Visit https://accounts.google.com and log in.
	- Go to https://accounts.google.com/DisplayUnlockCaptcha click `continue`.
	- Now copy the link looks like this(prompt in Gogs server log): https://accounts.google.com/ContinueSignIn?sarp=1&scc=1&plt=AKgnsbvPPN_E_25__nyS*******f18O9uuLNtz0Imw and log in again.
	- Things should work now. Last but not the least, check your `spam` box in case your mail service provider thinks your gmail is a spammer.

## Windows

- Error:

```
2014/09/18 15:04:40 [repo.go:115 CreatePost()] [E] CreatePost: initRepository: initRepository(git clone): cygwin warning:
MS-DOS style path detected: C:\Users\user\gogs-repositories\unos\test3.git/.git
Preferred POSIX equivalent is: /cygdrive/c/Users/user/gogs-repositories/unos/test3.git/.git
CYGWIN environment variable option "nodosfilewarning" turns off this warning.
Consult the user's guide for more details about POSIX paths:
http://cygwin.com/cygwin-ug-net/using.html#using-pathnames
Cloning into 'C:\Users\user\AppData\Local\Temp\484264900'...
fatal: '/cygdrive/d/svnroot/research/gogs/C:\Users\user\gogs-repositories\unos\test3.git' does not appear to be a git repository
fatal: Could not read from remote repository.
```

- Causes: you installed the another shell in system, and has different path style.
- Solution: please try to start Gogs through default CMD.

-----

- Error: `Resource interpreted as Stylesheet but transferred with MIME type application/x-css`
- Causes: wrong value in the Windows registry
- Solution: Find `.css` in `HKEY_CLASSES_ROOT` in registry and change its `Content Type` to `text/css`.

## Other

- Error: extremely slow page response but time show on the bottom looks normal(under 100ms)
- Causes: it may be caused by Nginx try to resolve IPv4 address as IPv6.
- Solution: use explicit hostname `127.0.0.1` instead of `localhost`.

-----

- Error: `Error 1062: Duplicate entry 'Unknown-Mac' for key 'UQE_public_key_name'`
- Causes: it is led by legacy code, `public_key` table used to have `UQE_public_key_name` unique rule for SSH key name in very early version.
- Solution: you can delete that unique rule manually to fix this problem.

-----

- Error: `GLIBC_2.14 not found`
- Solution: try `sudo apt-get -t testing install libc6-dev`.

-----

- Error: `[Macaron] PANIC: session(start): mkdir data: permission denied`
- Causes: Gogs creates `data` subdirectory at the same directory where Gogs binary is located.
- Solution: make sure Gogs has permission to create subdirectory at that directory.

-----
- Error: `! [remote rejected] master -> master (hook declined)`
- Causes: Git fails to execute the update script for some reason.
- Solution: make sure you have the `bash` shell available in your system, all the hook scripts needs it.
