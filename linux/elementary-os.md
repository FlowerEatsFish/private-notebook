# Elementary OS - Getting Started

<!-- TOC -->

- [Elementary OS - Getting Started](#elementary-os---getting-started)
  - [Partitions](#partitions)
  - [First step (required)](#first-step-required)
  - [Dark theme](#dark-theme)
  - [To install packages as follows by "AppCenter"](#to-install-packages-as-follows-by-appcenter)
  - [Install packages by terminal](#install-packages-by-terminal)
  - [.deb package commands](#deb-package-commands)
  - [To remove leftover "emacs" app after press "sudo apt autoremove --purge emacs"](#to-remove-leftover-emacs-app-after-press-sudo-apt-autoremove---purge-emacs)

<!-- /TOC -->

## Partitions

```text
| No. | Priority | Path  | Format                  | Type    | Volumns (256 GB) |
|-----|----------|-------|-------------------------|---------|------------------|
| 1   | Optional | x     | Reserved BIOS boot area | Primary | 50 MB            |
| 2   | Required | /boot | ext4                    | Primary | 4,000 MB         |
| 3   | Required | /     | ext4                    | Primary | 124,000 MB       |
| 4   | Optional | /home | ext4                    | Primary | 124,000 MB       |
| 5   | Required | swap  | x                       | Logical | 4,000 MB         |
```

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

## To install packages as follows by "AppCenter"

- Bottles (To run Windows program if it is required)

- Eddy (Simple debian package installer)

- gcin Tools (Chinese input method)

  - Command to set input method:

    ```shell
    im-config
    ```

- NVIDIA X Server Settings (Graphics card)

- Steam (Games center)

- Vim (Text editor in terminal)

## Install packages by terminal

- Git:

  ```shell
  # if you want to get the latest stable version
  $ add-apt-repository ppa:git-core/ppa
  $ sudo apt-get update

  $ sudo apt-get install git
  ```

- Node v8.x

  - Commands to get Node on version 8:

    ```shell
    curl -sL https://deb.nodesource.com/setup_8.x
    sudo -E bash -
    sudo apt-get install nodejs
    ```

- New cursor (breeze cursor theme)

  1. To install "Tweaks" app following [dark theme](#dark-theme) steps.

  2. Commands to get "Breeze Cursor Theme" cursor:

      ```shell
      sudo apt-get install breeze-cursor-theme
      ```

  3. To go to "Settings" -> "Tweaks" -> "Cursor".

## .deb package commands

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

- Skype: [https://www.skype.com/en/get-skype/](https://www.skype.com/en/get-skype/)

- Visual Studio Code: [https://code.visualstudio.com/download](https://code.visualstudio.com/download)

## To remove leftover "emacs" app after press "sudo apt autoremove --purge emacs"

> Version 24 on 2018-06-23.

- Method 1:

  Reference: [Ubuntu: how to remove emacs 23 data files](https://superuser.com/questions/927795/ubuntu-how-to-remove-emacs-23-data-files)

  ```shell
  sudo apt-get autoremove --purge ^emacs24
  ```

- Method 2:

  Reference: [談談Ubuntu的apt-get remove](http://falldog7.blogspot.com/2007/10/ubuntuapt-get-remove.html)

  1. To check how many emacs-related packages stay:

     ```shell
     $ dpkg -l | grep emacs
     ii  emacs                    46.1               all    GNU Emacs editor (metapackage)
     ii  emacs24                  24.5+1-6ubuntu1.1  amd64  GNU Emacs editor (with GTK+ GUI support)
     ii  emacs24-bin-common       24.5+1-6ubuntu1.1  amd64  GNU Emacs editor's shared, architecture dependent files
     ii  emacs24-common           24.5+1-6ubuntu1.1  all    GNU Emacs editor's shared, architecture independent infrastructure
     ii  emacs24-common-non-dfsg  24.4+1-2           all    GNU Emacs common non-DFSG items, including the core documentation
     ii  emacs24-el               24.5+1-6ubuntu1.1  all    GNU Emacs LISP (.el) files
     ii  emacsen-common           2.0.8              all    Common facilities for all emacsen
     ```

  2. To remove these packages:

     ```shell
     sudo dpkg -P [package name]
     ```
