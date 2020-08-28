---
name: Config and run
---

# Configuration and run

## Configuration

### Default configuration

The default configuration is saved in `conf/app.ini`, you do **NOT** need to edit it at all. Since `v0.6.0`, this file is embedded into the binary.

### Custom configuration

So how do you create a custom configuration if you are not allowed to edit `conf/app.ini`? Well, create `custom/conf/app.ini` then! Corresponding keys in corresponding sections in `custom/conf/app.ini` will overwrite the values set in `conf/app.ini`.

For example, to change the root path of where raw repository data is being stored, add something like follows:

```
[repository]
ROOT = /home/jiahuachen/gogs-repositories
```

Of course, you want to change the database setting as well:

```
[database]
PASSWORD = `root`
```

Note: please quote passwords using `` ` ``

### Why are we doing this?

Yes, why don't you just edit `conf/app.ini`? The reason is to keep your custom configuration safe:

- For people who install from binary, every time after you ship the program, you can just simply copy and paste without re-configuring anything.
- For people who install from source, we've ruled out the `custom/conf/app.ini` in `.gitignore`, so it will not cause changes in version control as a result of re-applying old configurations to the new version.

## Run Gogs server

### For Developers

- You need to set key `security -> INSTALL_LOCK` to be `true` in the file `custom/conf/app.ini` in order to run from source.
- You can use the famous `make` command:

```sh
$ make
$ ./gogs web
```

### For Deployment

**Scripts are in the `scripts` directory, but execute them at the root of the repository**

- There are many ways to start:
	- Plain: just use `./gogs web`
	- Daemons: see [scripts](https://github.com/gogs/gogs/tree/main/scripts) folder
- Go to `/install` to do your first-time run configuration.

### Running as daemon via init (eg. openrc)

- Create a file named `/etc/init.d/gogs` as follows, assuming gogs is installed in the `/home/git` user:

```
#!/sbin/openrc-run

SVCNAME=gogs
GOGS_PIDFILE=/var/run/gogs.pid
GOGS_USER=git
GOGS_HOME=/home/$GOGS_USER
GOGS_PATH=$GOGS_HOME/go/src/github.com/gogs/gogs
COMMAND="${GOGS_PATH}/gogs"
ARGS="web"

depend() {
    need net
    use dns logger mysql
}

checkconfig() {
    if [ ! -d "$GOGS_PATH" ] ; then
        eerror "gogs not installed" || return 1
    fi
    return 0
}

start() {
    checkconfig || return 1

    ebegin "Starting ${SVCNAME}"
    start-stop-daemon --start --quiet --background \
        --make-pidfile --pidfile "${GOGS_PIDFILE}" \
        --user "${GOGS_USER}" \
        -d ${GOGS_PATH} \
        --exec "${COMMAND}" "${ARGS}"
    eend $?
}

stop() {
    ebegin "Stopping ${SVCNAME}"
    start-stop-daemon --stop --quiet --pidfile $GOGS_PIDFILE
    eend $?
}
```
