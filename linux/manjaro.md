# Manjaro Linux

Manjaro Linux is a new linux distribution which is based on Arch linux.

<!-- TOC -->

- [Manjaro Linux](#manjaro-linux)
  - [Partitions](#partitions)
  - [Install packages by Pacman](#install-packages-by-pacman)
  - [Install packages by [AUR](https://aur.archlinux.org/)](#install-packages-by-aurhttpsaurarchlinuxorg)
  - [To remove packages with associated libraries](#to-remove-packages-with-associated-libraries)

<!-- /TOC -->

## Partitions

```text
| No. | Priority | Path  | Format                    | Volumns (256 GB) |
|-----|----------|-------|---------------------------|------------------|
| 1   | Optional | x     | Legacy and BIOS boot area | 50 MB            |
| 2   | Required | /boot | ext4                      | 4,000 MB         |
| 3   | Required | /     | ext4                      | 248,000 MB       |
| 4   | Optional | /home | ext4                      | none             |
| 5   | Required | swap  | x                         | 4,000 MB         |
```

## Install packages by Pacman

> The packages on Arch linux are always latest version by Pacman.

- Docker

  ```shell
  sudo pacman -S docker
  ```

- gcin Tools (Chinese input method)

  ```shell
  sudo pacman -S gcin
  ```

- Git

  ```shell
  sudo pacman -S git
  ```

- Vim

  ```shell
  sudo pacman -S vim
  ```

- Visual Studio Code

  ```shell
  sudo pacman -S code
  ```

## Install packages by [AUR](https://aur.archlinux.org/)

> AUR: Arch linux user reposotory.

- Google Chrome

  ```shell
  # Reference: https://linuxhint.com/install-google-chrome-on-arch-linux/
  $ git clone https://aur.archlinux.org/google-chrome.git
  $ cd google-chrome/

  # To build and install a package file for pacman package manager from these files.
  $ makepkg -si
  
  # To set Google Chrome as default browser.
  # KDE Plasma -> System Settings -> Applications -> File Associations -> application/xhtml+xml
  # Set "Google Chrome" as primary order.
  ```

- Discord

  ```shell
  # To install its dependencies.
  $ git clone https://aur.archlinux.org/libc++.git
  $ cd libc++
  
  # To make validation.
  $ gpg --recv-keys 0FC3042E345AD05D

  $ makepkg -si

  # Main package.
  $ git clone https://aur.archlinux.org/discord.git
  $ cd discord
  $ makepkg -si
  ```

- WPS Office

  ```shell
  # Main package.
  $ git clone https://aur.archlinux.org/wps-office.git
  $ cd wps-office
  $ makepkg -si

  # To install Microsoft-related fonts.
  $ git clone https://aur.archlinux.org/ttf-wps-fonts.git
  $ cd ttf-wps-fonts
  $ makepkg -si
  ```

## To remove packages with associated libraries

```shell
sudo pacman -Rs [package name]
```

- Microsoft Office Online

  ```shell
  sudo pacman -Rs ms-office-online
  ```

- Libre Office - Fresh Edition

  ```shell
  sudo pacman -Rs libreoffice-fresh
  ```
