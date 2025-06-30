---
title: mkaptrepo.conf
section: 8
header: Configuration Manual
author: Michael L. Schaecher <MichaelLeeSchaecher@gmail.com>
footer: Manual(mkaptrepo.conf) 0.3.9
version: 0.3.9
date: 2025-06-2
---

# NAME

_mkaptrepo.conf_ - configuration file for the mkaptrepo script.

# SYNOPSIS

_mkaptrepo_ [OPTIONS] flag ARG...

# DESCRIPTION

The _mkaptrepo.conf_ file is used to configure the _mkaptrepo_ script. It contains settings for the APT repository, such as the repository path, repository name, and remote repository URL. The configuration file is located at `~/.config/mkaptrepo/mkaptrepo.conf` by default.

# CONFIGURATION FILE

## REPOSITORY_NAME

The name of the APT repository. This is used to identify the repository in the package manager. There is no default value, so this must be set in the configuration file.

---

Example: _REPOSITORY_NAME=my-repo_

---

Default: _REPOSITORY_NAME=none_

## ORIGIN

The origin of the APT repository. This is used to identify the source of the packages in the repository. In general you want this to be the name of the repository (e.g. the domain without the `www.` prefix and without the `.com` or `.org` suffix).

---

Example: _ORIGIN=howtonebie_

---

Default: _ORIGIN=repository_

## LABEL

The label of the APT repository. This is used to identify the repository in the package manager. In general you want this to be the name of the repository (e.g. the domain without the `www.` prefix and without the `.com` or `.org` suffix). However, it any word you want can be used here.

---

Example: _LABEL=my-repo_

---

Default: _LABEL=same as ORIGIN_

## SUITE

The suite of the APT repository. This is used to identify the version of the packages in the repository. In general you want this to be the name of the distribution (e.g. `stable`, `testing`, `unstable`, etc.).

---

Example: _SUITE=stable_

---

Default: _SUITE=stable_

## CODENAME

The codename of the APT repository. This is used to identify the version of the packages in the repository. This can be anything but, in most cases, it is either set with 'stable', 'testing', or 'unstable'. However, if you are looking to create a repository for a specific distribution, you can set with the codename found in the `/etc/os-release` file of that distribution.

---

Example: _CODENAME=stable_

---

Default: _CODENAME=stable_

## ARCHITECTURE

The architecture of the APT repository. This is used to identify the architecture of the packages in the repository (e.i. `amd64`, `arm64`, `i386`, etc.). The is set by the `dpkg --print-architecture` command out of the box and you not want to change this if you are uploading compiled packages. However, if you are creating a repository for a specific architecture, you can set this to the desired architecture.

---

Example: _ARCHITECTURE=amd64_

---

Default: _ARCHITECTURE=$(dpkg --print-architecture)_

## COMPONENTS

The components of the APT repository. This is used to identify the components of the packages in the repository (e.i. `main`, `contrib`, `non-free`, etc.). The default is set to `main` but you can set this to any component you want.

---

Example: _COMPONENTS=main contrib non-free_

---

Default: _COMPONENTS=main_

## MAINTAINER

The maintainer of the APT repository. This is used to identify the maintainer of the repository in the package manager. This is usually set to your name and email address. In some cases this my differ from the application developer/maintainer weather it a single person or an organization.

---

Example: _MAINTAINER=John Doe <johndoe@email.com>_

---

Default: _MAINTAINER=$(git config user.name) \<$(git config user.email)\>_

## DIR_PATH

The directory path is where the local APT repository is stored. this must be set as a full path and without '~'.

---

Example: _DIR_PATH=$HOME/repositories/my-repo_

---

Default: _DIR_PATH=none_

# SEE_ALSO

_mkaptrepo(8)_, _apt(8)_, _dpkg(1)_, _dpkg-scanpackages(1)_

# COPYRIGHT

Copyright (c) under the terms of the [GPL-3.0](https://www.gnu.org/licenses/gpl-3.0.en.html) license.
