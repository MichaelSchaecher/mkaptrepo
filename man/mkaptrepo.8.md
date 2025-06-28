---
title: mkaptrepo
section: 8
header: manual
author: Michael L. Schaecher <MichaelLeeSchaecher@gmail.com>
footer: mkaptrepo 0.1.2
version: 0.1.2
date: 2025-06-28
---

# NAME

mkaptrepo - create and maintain an APT repository

# SYNOPSIS

`mkaptrepo` [OPTIONS] _arg..._

# DESCRIPTION

`mkaptrepo` is a script that creates and maintains an APT repository. It can be used to create a new repository, add packages to an existing repository, and update the repository metadata. With local user _Systemd_ service, the local APT repository is automatically updated push to the remote repository.

_monitor_
: Monitor the local repository for changes and automatically update the remote repository when `deb` files are added, removed, or modified.

_daemon_
: Enable the _Systemd_ service to run the `mkaptrepo` script as a daemon. This will allow the script to run in the background and automatically update the repository when changes are detected. see _DAEMONIZE_ section below for more details.

_config_
: Open the configuration file for the `mkaptrepo` script. This file contains the settings for the script, such as the repository path, repository name, and remote repository URL.

_help_
: Display the help message for the `mkaptrepo` script. This will show the available

_version_
: Display the version of the `mkaptrepo` script.

# DAEMONIZE

To run `mkaptrepo` as a daemon, you need to enable the _Systemd_ service. This can be done by running the following command:

```bash
systemctl enable --user --now mkaptrepo.service
```

The above command is ran with the `mkaptrepo daemon` command. This will enable the _Systemd_ service to run the `mkaptrepo` script as a daemon. The daemon will monitor the local repository for changes and automatically update the remote repository when `deb` files are added, removed, or modified.

By using user _Systemd_ service, the `mkaptrepo` script is only run when the user is logged in. This means that the script will not run when the system is booted, but only when the user is logged in. This is useful for users who do not want to run the script as a system service, but still want to keep their local APT repository up to date.

# SEE ALSO

`mkaptrepo.conf(8)` `systemd(1)`

# COPYRIGHT

Copyright (c) under the terms of the [GPL-3.0](https://www.gnu.org/licenses/gpl-3.0.en.html) license.
