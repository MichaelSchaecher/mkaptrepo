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

Example: `REPOSITORY_NAME="my-repo"`

---

Default: `REPOSITORY_NAME=none`

## ORIGIN

The origin of the APT repository. This is used to identify the source of the packages in the repository. In general you want this to be the name of the repository (e.g. the domain without the `www.` prefix and without the `.com` or `.org` suffix).

---

Example: `ORIGIN="howtonebie"

---

Default: `ORIGIN="repository"`

## LABEL

The label of the APT repository. This is used to identify the repository in the package manager. In general you want this to be the name of the repository (e.g. the domain without the `www.` prefix and without the `.com` or `.org` suffix). However, it any word you want can be used here.

---

Example: `LABEL="my-repo"`

---

Default: `LABEL="same as ORIGIN"`

## SUITE

The suite of the APT repository. This is used to identify the version of the packages in the repository. In general you want this to be the name of the distribution (e.g. `stable`, `testing`, `unstable`, etc.).

---

Example: `SUITE="stable"`

---

Default: `SUITE="stable"`

## CODENAME

The codename of the APT repository. This is used to identify the version of the packages in the repository. This can be anything but, in most cases, it is either set with 'stable', 'testing', or 'unstable'. However, if you are looking to create a repository for a specific distribution, you can set with the codename found in the `/etc/os-release` file of that distribution.

---

Example: `CODENAME="stable"`

---

Default: `CODENAME="stable"`

## ARCHITECTURE

The architecture of the APT repository. This is used to identify the architecture of the packages in the repository (e.i. `amd64`, `arm64`, `i386`, etc.). The is set by the `dpkg --print-architecture` command out of the box and you not want to change this if you are uploading compiled packages. However, if you are creating a repository for a specific architecture, you can set this to the desired architecture.

---

Example: `ARCHITECTURE="amd64"`

---

Default: `ARCHITECTURE="$(dpkg --print-architecture)"`

## COMPONENTS

The components of the APT repository. This is used to identify the components of the packages in the repository (e.i. `main`, `contrib`, `non-free`, etc.). The default is set to `main` but you can set this to any component you want.

---

Example: `COMPONENTS="main contrib non-free"`

---

Default: `COMPONENTS="main"`

## MAINTAINER

The maintainer of the APT repository. This is used to identify the maintainer of the repository in the package manager. This is usually set to your name and email address. In some cases this my differ from the application developer/maintainer weather it a single person or an organization.

---

Example: `MAINTAINER="John Doe <johndoe@email.com>"`

---

Default: `MAINTAINER="$(git config user.name) <$(git config user.email)>"`

## DIR_PATH

The directory path is where the local APT repository is stored. this must be set as a full path and without '~'.

---

Example: `DIR_PATH="$HOME/repositories/my-repo"`

---

Default: `DIR_PATH=none`

# SEE_ALSO

mkaptrepo(8), apt(8), dpkg(1) dpkg-scanpackages(1)

# COPYRIGHT

Copyright (c) under the terms of the [GPL-3.0](https://www.gnu.org/licenses/gpl-3.0.en.html) license.
