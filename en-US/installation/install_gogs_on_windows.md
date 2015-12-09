---
name: On Windows
---

## Binary install Gogs on Windows 7

### Run as the current local user

Gogs is able to run as the local user immediately, with no configuration. Simply unpack the [Windows binary](http://gogs.io/docs/installation/install_from_binary.html) zip file somewhere, go to command line, and do:

```
C:>cd C:\path\to\gogs

C:\path\to\gogs>gogs web
```

We'll assume you chose `C:\gogs`

At this point, Gogs should be available at `http://127.0.0.1:3000`, and the first-run installer will guide you through completing a basic and functional setup.

### First run

By default, Gogs will be using both `C:\Users\your_username` and `C:\gogs` for file operations.

In `C:\gogs`, Gogs will need write access to:

```
C:\gogs\custom\conf
C:\gogs\data
C:\gogs\log
```

Those are made during its first run, which assumes it then had write access to `C:\gogs`. Create them before first run if that is not true.

See [Configuration and Run](http://gogs.io/docs/installation/configuration_and_run.html) to learn about `C:\gogs\custom\conf\app.ini`. It will be written during first run.

Gogs will create `C:\Users\your_username\.gitconfig` with the following:

```
[user]
	name = Gogs
	email = gogitservice@gmail.com
```

That [can be changed to whatever you like](http://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup), and it should be. It is the user to which all of your git operations will be attributed to. It can also be overridden per-repository, through `C:\path\to\repo\.git\config`.

### Database

If you're using a remote database server, the [Ubuntu](http://gogs.io/docs/installation/install_gogs_on_ubuntu.html) and [Mac OS](http://gogs.io/docs/installation/install_gogs_on_mac.html) guides cover the SQL needed to create your tables.

For a local single-user Gogs instance, you may simply allow Gogs to create an SQLite database, by configuring nothing else before doing first run. The result of that in `C:\Gogs\custom\conf\app.ini` will look like this:

```
[database]
DB_TYPE = sqlite3
HOST = 127.0.0.1:3306
NAME = gogs
USER = root
PASSWD =
SSL_MODE = disable
PATH = data/gogs.db
```

This is where all Gogs data will be stored, but not git data. Git data (repository files, history, et. al.) lives outside of Gogs, on the file system, while Gogs provides a middleware layer for creating an issue queue, viewing the history, configuring the repository, etc.

Therefore, user authentication and authorization that you configure in Gogs will have no effect upon git operations done through the file system.

### Working locally

By default, Gogs managed repositories are in `C:\Users\your_username\gogs-repositories`

This is set in `C:\Gogs\custom\conf\app.ini` with:

```
[repository]
ROOT = C:/path/to/repositories
```

These will be bare repositories, with no working directory. You can clone them locally through the file system, with git.exe (which was required in [installation](http://gogs.io/docs/installation/), or with [TortoiseGit](https://code.google.com/p/tortoisegit/) if you prefer working through Windows Explorer.

On the command line, you might do:

```
C:>cd C:\Users\your_username\Documents\repos

C:\Users\your_username\Documents\repos>md repo_name

C:\Users\your_username\Documents\repos>cd repo_name

C:\Users\your_username\Documents\repos\repo_name>git.exe clone --progress -v "C:\Users\your_username\gogs-repositories\your_gogs_username\repo_name.git" "C:\Users\your_username\Documents\repos\repo_name"

Cloning into 'C:\Users\your_username\Documents\repos\repo_name'...

done.
```

When working locally, it's not necessary to pass git operations through the Gogs service. Gogs will update when you `git push` your working directory clone from `C:\Users\your_username\Documents\repos\repo_name` back to its origin at `C:\Users\your_username\gogs-repositories`. Do clone the repository when you need a working directory—even when flying solo. It allows you to very easily move Gogs and your origin repositories later, without that process touching your working directories.

### Run Gogs as a service

At this point, you may choose to lock down file and directory permissions. Just keep in mind the paths to which Gogs requires write access, which includes the Gogs repository `ROOT`.

The following changes are made in `C:\Gogs\custom\conf\app.ini`:

```
RUN_USER = COMPUTERNAME$
```

Sets Gogs to run as the local system user.

`COMPUTERNAME` is whatever the response is from `echo %COMPUTERNAME%` on the command line. If the response is `USER-PC` then `RUN_USER = USER-PC$`

```
[server]
DOMAIN = gogs
PROTOCOL = http
HTTP_ADDR = 127.0.1.1
HTTP_PORT = 80
OFFLINE_MODE = true
ROOT_URL = http://gogs/
```

Moves Gogs' listen port to 80 on the local interface subnet, and tells the Gogs HTTPd that its virtual host is the "gogs" domain. This lets you forgo including a port number when browsing, and prevents collision with other localhost services. The IP address can be anything in the range 127.0.0.2 - 127.254.254.254, so long as it's unique to Gogs.

To complete that network route, open Notepad.exe as administrator and include the following in `C:\Windows\System32\drivers\etc\hosts`:

```
# Go Git Service local HTTPd
127.0.1.1        gogs
```

The hosts file entry will guarantee that all requests to the "gogs" domain are captured by your localhost interface. In a web browser, generally, `gogs/` in the address bar is sufficient to trigger that route.

Open a command prompt (cmd.exe) as an Administrator. Run the following command:
```
C:\> sc create gogs start= auto binPath= """C:\gogs\gogs.exe"" web --config ""C:\gogs\conf\app.ini"""
```
Ensure there is a space after each "=". You can choose to add additional Arguments
to further modify your service, or modify it manually in the service management console.

To start the service run
```
C:\> net start gogs
```
You should see
```
The gogs service is starting.
The gogs service was started successfully.
```
