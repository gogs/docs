---
name: Config and run
sort: 6
---

# Configuration and run

## Configuration

### Default configuration

The default configuration is saved in `conf/app.ini`, you do **NOT** need to edit it at all.

### Custom configuration

So how to do custom configuration if you are not allowed to edit `conf/app.ini`? Well, create `custom/conf/app.ini` then! Overwrite corresponding key in corresponding section in `custom/conf/app.ini`.

For example, to change the root path of where repository raw data being stored, add something like follows:

```
[repository]
ROOT = /home/jiahuachen/gogs-repositories
```

Of course, you want to change database setting as well:

```
[database]
PASSWD = root
```

### Why are we doing this?

Yes, why don't you just edit `conf/app.ini`? The reason is that to keep your custom configuration safe:

- For people who install from binary, every time after you ship the program, can just simply copy and paste without re-configuring anything.
- For people who install from source, we've ruled out the `custom/conf/app.ini` in `.gitignore` so it will not cause changes in version control which you have to do batch of other stuff before updating.

## Run Gogs server

### For Developers

- You need to set key `security -> INSTALL_LOCK` to be `true` in file `custom/conf/app.ini` in order to run from source.
- You can enable live compile by executing `bra run` in the Gogs source folder
	- Install [bra](https://github.com/Unknwon/bra): `go get -u github.com/Unknwon/bra`

### For Deployment

**Scripts are in `scripts` directory, but execute them at root of repository**

- There are 3 ways to start by default:
	- Plain: just use `./gogs web`
	- Supervisor:
		- Start: `./scripts/gogs_supervisord.sh start`
		- Stop: `./scripts/gogs_supervisord.sh stop`
		- Restart: `./scripts/gogs_supervisord.sh restart`
- Go to `/install` to do your first-time run configuration.
