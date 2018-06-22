# Elementary OS - Getting Started

<!-- TOC -->

- [Elementary OS - Getting Started](#elementary-os---getting-started)
  - [Partitions](#partitions)
  - [First step (required)](#first-step-required)
  - [Dark theme](#dark-theme)
  - [Input method (gcin)](#input-method-gcin)
  - [New cursor (breeze cursor theme)](#new-cursor-breeze-cursor-theme)
  - [Node v8.x](#node-v8x)
  - [Install packages by "apt-get" command](#install-packages-by-apt-get-command)
  - [.deb packages](#deb-packages)

<!-- /TOC -->

## Partitions

| No. | Priority     | Path  | Format                  | Type    | Volumns (256 GB) |
|-----|--------------|-------|-------------------------|---------|------------------|
| 1   | Optional     | x     | Reserved BIOS boot area | Primary | 50 MB            |
| 2   | **Required** | /boot | ext4                    | Primary | 4,000 MB         |
| 3   | **Required** | /     | ext4                    | Primary | 248,000 MB       |
| 4   | Optional     | /home | ext4                    | Primary | none             |
| 5   | **Required** | swap  | x                       | Logical | 4,000 MB         |

## First step (required)

- If you have never added a PPA on Loki before, you might need to run this command first:

  ```shell
  sudo apt-get install software-properties-common
  ```

## Dark theme

- Commands to get "Tweaks" app:

  ```shell
  sudo apt-get install elementary-tweaks
  ```

- Go to "Settings" -> "Tweaks" -> "Prefer darker variant".

## Input method (gcin)

- Command to get Chinese input "gcin":

  ```shell
  sudo apt-get install gcin
  ```

- Command to set input method:

  ```shell
  im-config
  ```

## New cursor (breeze cursor theme)

- Install "Tweaks" app following [dark theme](#dark-theme) steps.

- Commands to get "Breeze Cursor Theme" cursor:

  ```shell
  sudo apt-get install breeze-cursor-theme
  ```

- Go to "Settings" -> "Tweaks" -> "Cursor".

## Node v8.x

- Commands to get Node on version 8:

  ```shell
  curl -sL https://deb.nodesource.com/setup_8.x
  sudo -E bash -
  sudo apt-get install nodejs
  ```

## Install packages by "apt-get" command

- git

```shell
# if you want to get the latest stable version
$ add-apt-repository ppa:git-core/ppa
$ sudo apt-get update

$ sudo apt-get install git
```

## .deb packages

- Commands:

  ```shell
  # Install a package
  $ dpkg -i [package path].deb

  # List all the installed packages
  $ dpkg -l

  # Check the location of packages installed
  $ dpkg -L [package name]

  # Remove a package but not its configuration files
  $ dpkg -r [package name]

  # Remove a package along with configuration files
  $ dpkg -p [package name]
  ```

- Discord: [https://discordapp.com/download](https://discordapp.com/download)

- Google Chrome: [https://www.google.com/chrome/](https://www.google.com/chrome/)

- Steam: [https://store.steampowered.com/about/](https://store.steampowered.com/about/)

- Skype: [https://www.skype.com/en/get-skype/](https://www.skype.com/en/get-skype/)

- Visual Studio Code: [https://code.visualstudio.com/download](https://code.visualstudio.com/download)