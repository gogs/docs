---
name: From source
---

# Install from source

## Installing Go

Gogs requires Go 1.14 to compile, please refer to the [official documentation](https://golang.org/doc/install) for how to install Go in your system.

## Set Up the Environment

We are going to create a new user called `git` and set up everything under that user:

```sh
sudo adduser --disabled-login --gecos 'Gogs' git
```

## Compile Gogs

```sh
# Clone the repository to the "gogs" subdirectory
git clone --depth 1 https://github.com/gogs/gogs.git gogs
# Change working directory
cd gogs
# Compile the main program, dependencies will be downloaded at this step
go build -o gogs
```

## Test Installation

To make sure Gogs is working:

```sh
./gogs web
```

If you do not see any error messages, hit `Ctrl-C` to stop Gogs.

## Build with Tags

A couple of things do not come with Gogs automatically, you need to compile Gogs with corresponding [build tags](https://golang.org/pkg/go/build/#hdr-Build_Constraints).

Available build tags are:

- `pam`: PAM authentication support
- `cert`: Generate self-signed certificates support
- `minwinsvc`: Builtin windows service support (or you can use NSSM to create a service)

```sh
go build -tags "pam cert" -o gogs
```

If you get error: `fatal error: security/pam_appl.h: No such file or directory`, then install missing package via `sudo apt-get install libpam0g-dev`.

## Next steps

- See [Configuration and run](/docs/installation/configuration_and_run) to go further.
