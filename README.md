<div align="right">
 <image
  src="images/logo.png"
  alt="MKrelease Logo"
  width="auto"
  height="360">
</div>

---

There are many tools to create Debian/Ubuntu DEB repositories, but most of them are too complex or not flexible enough. This tool is designed to be simple and flexible, the general or novice developer to create a DEB repository with minimal effort.

Why is the even a thing? Because I needed it for my own projects, and that I self-host a servers that I have made basic packages to manage a few services. As most of the servers are setup with a set-it-and-forget mentality, I needed a tool that would allow me to create a DEB repository with minimal effort that whey I use `unattended-upgrades` to update the servers from my own [repository](https://repository.howtonebie.com), I can be sure that the packages are up to date and secure.

## Features

- Simple to use, just run the script and it will create a DEB repository for you.
- Monitor for changes in the background v.i `inotifywait` when user daemon is enabled.
- Generate simple `git commit` messages based on the changes made to the repository.
- Push changes to a remote repository, such as GitHub, GitLab, or servers compatible with Git.
- Generate a `README.md` from a template, which can be customized to your needs.

## Installation

To install the tool, you can either clone the and run the `build` script, or you can use the provided, then install with `sudo dpkg -i mkaptrepo*.deb`.

```bash
git clone https://github.com/MichaelSchaecher/mkaptrepo.git
```

If you have `git-cli` installed, you can also use the `gh` command to clone the repository:

```bash
gh repo clone MichaelSchaecher/mkaptrepo
```

The preferred way to install `mkaptrepo` is to follow the [instructions](https://repository.howtonebie.com/mkaptrepo/) on the repository website, which will guide you through prossess adding the repository.

```console
sudo apt install --yes mkaptrepo
```

## Usage

To use the tool, you can run the `mkaptrepo` command with the desired options. The basic usage is as follows:

```console

Usage: ${_appName} [OPTION] flag ARG...

Options
    update                      Update the package list and generate the Release file.
    monitor                     Monitor the repository for changes and update the package list.
    daemonize                   Enable the systemd service for current user: see \`man mkaptrepo\`
                                for more information.
    create                      Create a new apt repository (for more information, add --help).
    config                      Install the configuration file to \`~/.config/mkaptrepo/mkaptrepo.conf\`
                                and exit.
    help                        Show this help message and exit.
    version                     Show version information and exit.
```

Read the `man mkaptrepo` page for more information on the available options and how to use them

## Contributing

If you want to contribute to the project, you can fork the repository and create a pull request. You can also report issues or suggest features on the [GitHub Issues page](https://github.com/MichaelSchaecher/mkaptrepo/issues).

## License

Copyright (c) 2025 Michael Schaecher \<MichaelLeeSchaecher@gmail.com\> under the [GPL-3.0 License](COPYING).
