---
name: On Windows
sort: 6
---

## Binary install Gogs on Windows 7

> Contributed by [@victorsegall](https://github.com/victorsegall)

### Prerequisites

Check the main [installation page](http://gogs.io/docs/installation/) to confirm before you go on. You need [git for Windows](http://git-scm.com/download/win).

An SSH server is not needed on your Windows machine, if this Gogs instance will be for you alone, or if you only need the HTTP(S) service that Gogs provides.

To run Gogs as a service, you will need one of:

* Iain Patterson's [nssm.exe](http://nssm.cc/)
* Nick Rozanski's [SRVSTART.EXE](http://rozanski.org.uk/software)
* Microsoft's [Srvany.exe](https://support.microsoft.com/kb/137890)

This guide covers nssm.exe, which is [open source](https://git.nssm.cc/?p=nssm.git) and [public domain](https://git.nssm.cc/?p=nssm.git;a=blob_plain;f=README.txt;hb=HEAD).

During setup, you will run Gogs as current local user, and then reconfigure to run as a service.

### Run as current local user

Gogs is able to run as local user immediately, with no configuration. Simply unpack the [Windows binary](http://gogs.io/docs/installation/install_from_binary.html) zip file somewhere, go to command line, and do:

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
ROOT = C:\path\to\repositories
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

Get the [nssm.exe](http://nssm.cc/download) needed for your machine (32 or 64 bit; they're packaged together in Iain's zip file), and place it in a directory that is in (or will be added to) your %PATH% environment variable.

Open a command line as administrator and do `nssm install gogs` to configure Gogs as a service.

```
C:\>nssm install gogs
```

"NSSM service installer" will appear. Configure it as follows:

Application tab:

* Path: C:\gogs\gogs.exe
* Startup directory: C:\gogs
* Arguments: web

![](/docs/images/install_gogs_on_windows_nssm_1.png)

Details tab:

* Display name: Go Gits Service
* Description: Gogs (Go Git Service) is a painless self-hosted Git service written in Go.
* Startup type: Automatic (Delayed Start)

Note that we've chosen [delayed start](http://stackoverflow.com/a/11015576), so that the service will not impact the early boot time. Gogs will start two minutes after the non-delayed services.

![](/docs/images/install_gogs_on_windows_nssm_2.png)

I/O tab:

* Output (stdout): C:\gogs\log\gogs-nssm.txt
* Error (stderr): C:\gogs\log\gogs-nssm.txt

That will capture all text output that you would normally receive from Gogs on the command line console, and log it to that file instead.

![](/docs/images/install_gogs_on_windows_nssm_3.png)

File rotation tab:

* Check: Rotate files
* Restrict rotation to files bigger than: 1000000 bytes

![](/docs/images/install_gogs_on_windows_nssm_4.png)

Environment tab:

* Environment variables: PATH=%PATH%;C:\gogs;C:\Program Files (x86)\Git\bin

That is a guarantee that both gogs.exe and git.exe will be on the Gogs service's path variable during runtime.

![](/docs/images/install_gogs_on_windows_nssm_5.png)

Click "Install service", and you should be confirmed that it succeeded. If it failed, refer back to the command line console you started, for the error message. When it succeeds, go to command line and do:

```
nssm start gogs
```

You should see:

```
gogs: START: The operation completed successfully.
```

Check that this is true by opening `C:\gogs\log\gogs-nssm.txt`. You should see Gogs' start up procedures, ending with:

```
timestamp [I] SQLite3 Enabled
timestamp [I] Run Mode: Production
timestamp [I] Listen: http://127.0.1.1:80
```

Now point your web browser at `http://gogs/` and log in.

Gogs is running as a service, and will not need to be run manually, unless something goes wrong. NSSM will attempt to restart the service for you, if the Gogs server crashes.

When you need to restart it after `app.ini` changes, go to an administrator command line after the changes, and do:

```
nssm restart gogs
```

See the [configuration cheat sheet](http://gogs.io/docs/advanced/configuration_cheat_sheet.html) for reference of the `custom\conf\app.ini` settings.

An example of the logging and error handling in action:

```
[log]
ROOT_PATH = C:\gogs\log
```

Don't do that (at time of writing this line, for Go Git Service 0.5.13.0212 Beta). It will cause the following to print in `C:\gogs\log\gogs-nssm.txt`:

```
timestamp [T] Custom path: C:/gogs/custom
timestamp [T] Log path: C:\gogs\log
timestamp [I] Gogs: Go Git Service 0.5.13.0212 Beta
timestamp [log.go:294 Error()] [E] Fail to set logger(file): invalid character 'g' in string escape code
```

This is what it expected in `C:\custom\conf\app.ini`:

```
ROOT_PATH = C:/gogs/log
```

And this is what the command line looks like:

```
C:\>nssm restart gogs
gogs: STOP: The operation completed successfully.
gogs: Unexpected status SERVICE_PAUSED in response to START control.

C:\>nssm start gogs
gogs: START: An instance of the service is already running.

C:\>nssm stop gogs
gogs: STOP: The operation completed successfully.

C:\>nssm start gogs
gogs: Unexpected status SERVICE_PAUSED in response to START control.

C:\>nssm restart gogs
gogs: STOP: The operation completed successfully.
gogs: START: The operation completed successfully.
```
