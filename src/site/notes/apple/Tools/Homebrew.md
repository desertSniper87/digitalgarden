---
{"dg-publish":true,"permalink":"/apple/tools/homebrew/"}
---

[Homebrew](https://brew.sh/) is a free and open-source package manager used for macOS systems and is an essential tool for developers or penetration testers using macOS. It allows easy installation of many standard tools without the hustle of manually compiling open-source tools or downloading their requirements. For example, `php` used to come built-in with macOS but has been removed from recent versions for 'security concerns'. Installing `php` without Homebrew requires the manual compilation of the `php` tool, which can take some time and be quite problematic. This is why PHP [officially recommends using Homebrew](https://www.php.net/manual/en/install.macosx.packages.php) to install it on recent versions of macOS. The same applies to many other developer tools.

## Installation

1. [How to install homebrew on M1 mac - Stack Overflow](https://stackoverflow.com/questions/66666134/how-to-install-homebrew-on-m1-mac)

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

To update brew:

```bash
brew update-reset
```

To check which packages are installed


```bash
brew list
```

Source: https://mkyong.com/mac/how-to-find-all-packages-installed-using-homebrew/


## List of Homebrew packages

- https://apple.stackexchange.com/questions/101090/list-of-all-packages-installed-using-homebrew

## Get info about package

```shell
brew info transmission
```


## Search for package


```shell-session
brew search firefox
```