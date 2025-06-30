---
title: mkaptrepo
section: 8
header: General Commands Manual
author: Michael L. Schaecher <MichaelLeeSchaecher@gmail.com>
footer: Manual(mkaptrepo) 0.3.9
version: 0.3.9
date: 2025-06-29
---

# NAME

_mkaptrepo_ - create and maintain an APT repository

# SYNOPSIS

_mkaptrepo_ [OPTIONS] _arg..._

# DESCRIPTION

_mkaptrepo_ is a script that creates and maintains an APT repository. It can be used to create a new repository, add packages to an existing repository, and update the repository metadata. With local user _systemd_ service, the local APT repository is automatically updated push to the remote repository.

_update_
: Update the local APT repository metadata.

_monitor_
: Monitor the local repository for changes and automatically update the remote repository when `deb` files are added, removed, or modified.

_daemonize_
: Enable the _systemd_ service to run the _mkaptrepo_ script as a daemon. This will allow the script to run in the background and automatically update the repository when changes are detected. see _DAEMONIZE_ section below for more details.

_create_
: Create a new APT repository. This will create the necessary directory structure and files for the (see _CREATE_ section below for )

_config_
: Open the configuration file for the _mkaptrepo_ script. This file contains the settings for the script, such as the repository path, repository name, and remote repository URL.

_help_
: Display the help message for the _mkaptrepo_ script. This will show the available

_version_
: Display the version of the _mkaptrepo_ script.

# CREATE

The structure of the APT repository is important for having a functional repository. The _mkaptrepo_ script will create the necessary directory structure and files for the APT repository. This is done mostly according to the Debian/Ubuntu APT repository structure. In general there really is no difference between a Debian and Ubuntu APT repository structure.

---

Universal APT repository structure:

```console
repository/
├── dists/
│   └── stable/
│       └── main/
│           └── binary-amd64/
│               └── Package
│               └── Packages.gz
│               └── Packages.xz
│       └── Release.gpg (optional for signed repositories)
│       └── InRelease (optional for signed repositories)
├── pool/
    └── main/
        └── (alphabetical subdirectories/libraries types)
            └── package-name/
                └── package-version.deb
```

Debian/Ubuntu APT repository structure:

```console
repository/
├── dists/
│   └── codename/
│       └── main/
│           └── binary-amd64/
│               └── Packages
│               └── Packages.gz
│               └── Packages.xz
|       └── Release
│       └── Release.gpg (optional for signed repositories)
│       └── InRelease (optional for signed repositories)
├── pool/
    └── main/
        └── (alphabetical subdirectories/libraries types)
            └── package-name/
                └── package-version.deb
```

_mkaptrepo_ is able follow the Debian/Ubuntu APT repository structure if directed to do so. However, the default structure is the the _Universal APT repository structure_. This helps the repository to be more enabled for for any distribution that use _APT_ as the package manager.

## OPTIONS

_-a_, _--arch_ <architecture>
: Specify the architecture for the repository. This is useful for creating a repository that supports multiple architectures. The default is set by the `dpkg --print-architecture` command, which is usually `amd64` for most modern systems.

_-r_, _--release_ <release-codename>
: Specify the release codename for the repository. This is useful for creating a repository that supports a particular distribution release. Default: `stable`.

_-n_, _--name_ <repository-name>
: Specify the name of the repository. This is not an optional argument and is required to create a new repository. The name will be used to create the directory for the _GIT_ repository.

_-p_, _--populate_
: Populate the repository with the necessary directory structure and files. The will create the the alphabetical subdirectories in the `pool/` directory.

_-l_, _--license_ <license>
: Specify the license for the repository. _mkaptrepo_ make available the most common licenses for application development, such as `GPL-3.0`, `MIT`, `Apache-2.0`, and `BSD-3-Clause`. The license will be used to create the `LICENSE` file in the root of the repository.

# DAEMONIZE

To run _mkaptrepo_ as a daemon, you need to enable the _systemd_ service. This can be done by running the following command:

```bash
systemctl enable --user --now mkaptrepo.service
```

The above command is ran with the _mkaptrepo daemon_ command. This will enable the _systemd_ service to run the _mkaptrepo_ script as a daemon. The daemon will monitor the local repository for changes and automatically update the remote repository when `deb` files are added, removed, or modified.

By using user _systemd_ service, the _mkaptrepo_ script is only run when the user is logged in. This means that the script will not run when the system is booted, but only when the user is logged in. This is useful for users who do not want to run the script as a system service, but still want to keep their local APT repository up to date.

# SEE ALSO

_mkaptrepo.conf(8)_, _systemd(1)_, _apt(8)_, _dpkg(1)_, _dpkg-scanpackages(1)_, _gpg(1)_

# COPYRIGHT

Copyright (c) under the terms of the [GPL-3.0](https://www.gnu.org/licenses/gpl-3.0.en.html) license.
