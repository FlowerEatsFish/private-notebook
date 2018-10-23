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

  # To build a package file for pacman package manager from these files.
  $ makepkg -s

  # To install Google Chrome.
  $ sudo pacman -U google-chrome-63.0.3239.108-1-x86_64.pkg.tar.xz
  ```

## To remove packages with associated libraries

```shell
sudo pacman -Rs [package name]
```
