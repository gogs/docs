---
name: From binary
---

# Install from binary

All downloads come with support for **PostgreSQL**, **MySQL**, and **SQLite 3** as database backend.

The Windows downloads with "mws" suffix have built-in Windows service support; if you use NSSM, download the normal versions for Windows.

Downloads are available in [dl.gogs.io](https://dl.gogs.io) and [GitHub releases](https://github.com/gogs/gogs/releases).

## How to use downloads?

1. Check that [prerequisites are installed](/docs/installation)
2. Extract the archive.
3. `cd` into the directory that was just created.
4. Execute `./gogs web`.
5. Gogs will start up a HTTP service at port `3000` as default. Browse `/install` for initial configuration (e.g. http://localhost:3000/install).

To go further, see [Configuration and run](/docs/installation/configuration_and_run.html).
