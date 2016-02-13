---
name: Config and run
---

# Configuration and run

## Configuration

### Default configuration

The default configuration is saved in `conf/app.ini`, you do **NOT** need to edit it at all. Since `v0.6.0`, this file is embedded into the binary.

### Custom configuration

So how do you create a custom configuration if you are not allowed to edit `conf/app.ini`? Well, create `custom/conf/app.ini` then! Corresponding keys in corresponding sections in `custom/conf/app.ini` will overwrite the values set in `conf/app.ini`.

For example, to change the root path of where repository raw data is being stored, add something like follows:

```
[repository]
ROOT = /home/jiahuachen/gogs-repositories
```

Of course, you want to change the database setting as well:

```
[database]
PASSWD = `root`
```

Note: please quote passwords using `` ` ``

### Why are we doing this?

Yes, why don't you just edit `conf/app.ini`? The reason is to keep your custom configuration safe:

- For people who install from binary, every time after you ship the program, you can just simply copy and paste without re-configuring anything.
- For people who install from source, we've ruled out the `custom/conf/app.ini` in `.gitignore`, so it will not cause changes in version control which you have to do batch of other stuff before updating.

## Run Gogs server

### For Developers

- You need to set key `security -> INSTALL_LOCK` to be `true` in file `custom/conf/app.ini` in order to run from source.
- You can use famous `make` command:

	```sh
$ make
$ ./gogs web
	```

- You can enable live compile by executing `bra run` in the Gogs source folder
	- To install [bra](https://github.com/Unknwon/bra): `go get -u github.com/Unknwon/bra`

### For Deployment

**Scripts are in the `scripts` directory, but execute them at root of the repository**

- There are many ways to start:
	- Plain: just use `./gogs web`
	- Daemons: see [scripts](https://github.com/gogits/gogs/tree/master/scripts) folder
- Go to `/install` to do your first-time run configuration.
