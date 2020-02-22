---
name: Run As Windows Service
---

# Run As Windows Service

### Prerequisites

To run Gogs as a service, you will need one of:

1. Use `minwinsvc` build tags to have builtin Windows service support.
2. Do not use `minwinsvc` build tags and use [NSSM](http://nssm.cc/).

First of all, you may choose to lock down file and directory permissions. Just keep in mind the paths to which Gogs requires write access, which includes the Gogs repository `ROOT`.

The following changes are made in `C:\gogs\custom\conf\app.ini`:

```
RUN_USER = COMPUTERNAME$
```

Sets Gogs to run as the local system user.

`COMPUTERNAME` is whatever the response is from `echo %COMPUTERNAME%` on the command line. If the response is `USER-PC` then `RUN_USER = USER-PC$`:

```
[server]
DOMAIN = gogs
PROTOCOL = http
HTTP_ADDR = 127.0.1.1
HTTP_PORT = 80
OFFLINE_MODE = true
EXTERNAL_URL = http://gogs/
```

Moves Gogs' listen port to 80 on the local interface subnet, and tells the Gogs HTTPd that its virtual host is the "gogs" domain.
This lets you forgo including a port number when browsing, and prevents collision with other localhost services.
The IP address can be anything in the range `127.0.0.2 - 127.254.254.254`, so long as it's unique to Gogs.

To complete that network route, open Notepad.exe as administrator and include the following in `C:\Windows\System32\drivers\etc\hosts`:

```
# Gogs local HTTPd
127.0.1.1        gogs
```

The hosts file entry will guarantee that all requests to the "gogs" domain are captured by your localhost interface.
In a web browser, generally, `gogs/` in the address bar is sufficient to trigger that route.

### Use Builtin Functionality

Open a command prompt (`cmd.exe`) as an Administrator. Run the following command:

```
C:\> sc create gogs start= auto binPath= "\"C:\gogs\gogs.exe\" web --config \"C:\gogs\custom\conf\app.ini\""
```

Ensure there is a space after each `=`. You can choose to add additional Arguments to further modify your service, or modify it manually in the service management console.

To start the service run following command:

```
C:\> net start gogs
```

You should see following output:

```
The gogs service is starting.
The gogs service was started successfully.
```

#### :warning: Use absolute paths

Windows services usualy run with under ``%WINDIR%\System32``, and to ensure correct function, specify absolute paths for server data, database files, and other paths in ``app.ini``. For example:

Update where Gogs stores server data and cache:

```
[server]
APP_DATA_PATH = c:/gogs/data
```

If you use sqlite3, change the ``PATH`` to include the full path:
```
[database]
PATH     = c:/gogs/data/gogs.db
```

### Use NSSM

Get the [nssm.exe](http://nssm.cc/download) needed for your machine (32 or 64 bit; they're packaged together in Iain's zip file), and place it in a directory that is in (or will be added to) your ``%PATH%`` environment variable.

Open a command line as administrator and do following command to configure Gogs as a service:

```
C:\>nssm install gogs
```

"NSSM service installer" will appear. Configure it as follows:

Application tab:

- Path: `C:\gogs\gogs.exe`
- Startup directory: `C:\gogs`
- Arguments: `web`

![](/docs/images/install_gogs_on_windows_nssm_1.png)

Details tab:

- Display name: `Gogs`
- Description: `Gogs is a painless self-hosted Git service.`
- Startup type: `Automatic (Delayed Start)`

Note that we've chosen [delayed start](http://stackoverflow.com/a/11015576), so that the service will not impact the early boot time. Gogs will start two minutes after the non-delayed services.

![](/docs/images/install_gogs_on_windows_nssm_2.png)

I/O tab:

- Output (stdout): `C:\gogs\log\gogs-nssm.txt`
- Error (stderr): `C:\gogs\log\gogs-nssm.txt`

That will capture all text output that you would normally receive from Gogs on the command line console, and log it to that file instead.

![](/docs/images/install_gogs_on_windows_nssm_3.png)

File rotation tab:

- Check: `Rotate files`
- Restrict rotation to files bigger than: `1000000 bytes`

![](/docs/images/install_gogs_on_windows_nssm_4.png)

Environment tab:

- Environment variables: `PATH=%PATH%;C:\gogs;C:\Program Files (x86)\Git\bin`

That is a guarantee that both `gogs.exe` and `git.exe` will be on the Gogs service's path variable during runtime.

![](/docs/images/install_gogs_on_windows_nssm_5.png)

Click "Install service", and you should be confirmed that it succeeded.

If it failed, refer back to the command line console you started, for the error message. When it succeeds, go to command line and do:

```
nssm start gogs
```

You should see:

```
gogs: START: The operation completed successfully.
```

Check that this is true by opening `C:\gogs\log\gogs-nssm.txt`. You should see Gogs' start up procedures, ending with:

```
timestamp [I] Run Mode: Production
timestamp [I] Listen: http://127.0.1.1:80
```

Now point your web browser at `http://gogs/` and log in.

Gogs is running as a service, and will not need to be run manually, unless something goes wrong. NSSM will attempt to restart the service for you, if the Gogs server crashes.

When you need to restart it after `app.ini` changes, go to an administrator command line after the changes, and do:

```
nssm restart gogs
```

See the [configuration cheat sheet](/docs/advanced/configuration_cheat_sheet.html) for reference of the `custom\conf\app.ini` settings.

An example of the logging and error handling in action:

```
[log]
ROOT_PATH = C:\gogs\log
```

At the time of writing this line, it will cause the following to print in `C:\gogs\log\gogs-nssm.txt`:

```
timestamp [T] Custom path: C:/gogs/custom
timestamp [T] Log path: C:\gogs\log
timestamp [I] Gogs x.y.z
timestamp [log.go:294 Error()] [E] Fail to set logger(file): invalid character 'g' in string escape code
```

This is what was expected in `C:\custom\conf\app.ini`:

```
ROOT_PATH = C:/gogs/log
```

And this was the `nssm` interaction while solving it:

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
