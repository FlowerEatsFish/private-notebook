# Manjaro Linux

Manjaro Linux is a new linux distribution which is based on Arch linux.

<!-- TOC -->

- [Manjaro Linux](#Manjaro-Linux)
  - [Partitions](#Partitions)
    - [Legacy boot mode](#Legacy-boot-mode)
    - [UEFI boot mode](#UEFI-boot-mode)
  - [Install packages by Pacman](#Install-packages-by-Pacman)
    - [Docker](#Docker)
    - [gcin Tools (Chinese input method)](#gcin-Tools-Chinese-input-method)
    - [Vim](#Vim)
    - [Visual Studio Code](#Visual-Studio-Code)
    - [Chromium](#Chromium)
    - [Hyper](#Hyper)
  - [Install packages by AUR](#Install-packages-by-AUR)
    - [Discord](#Discord)
    - [WPS Office](#WPS-Office)
  - [To remove packages with associated libraries](#To-remove-packages-with-associated-libraries)
    - [HP System Software Manager](#HP-System-Software-Manager)
    - [Microsoft Office Online](#Microsoft-Office-Online)

<!-- /TOC -->

## Partitions

### Legacy boot mode

```text
| No. | Priority | Path  | Format                    | Volumns (256 GB) |
|-----|----------|-------|---------------------------|------------------|
| 1   | Optional | x     | Legacy and BIOS boot area | 50 MB            |
| 2   | Required | /boot | ext4                      | 4,000 MB         |
| 3   | Required | /     | ext4                      | 248,000 MB       |
| 4   | Optional | /home | ext4                      | none             |
| 5   | Required | swap  | x                         | 4,000 MB         |
```

### UEFI boot mode

```text
| No. | Priority | Path      | Flag      | Format | Volumns (256 GB) |
|-----|----------|-----------|-----------|--------|------------------|
| 1   | Required | /boot/efi | boot, esp | fat32  | 50 MB            |
| 2   | Required | /         |           | ext4   | 252,000 MB       |
| 3   | Optional | /home     |           | ext4   | none             |
| 4   | Required | swap      | swap      | x      | 4,000 MB         |
```

## Install packages by Pacman

> The packages on Arch linux are always latest version by Pacman.

```shell
sudo pacman -S [package name]
```

### Docker

Installation

```shell
sudo pacman -S docker
```

Run docker with current user

  1. Add current user to "docker" group

      ```shell
      sudo usermod -aG docker $USER
      ```

  2. Auto-start docker when booting

      ```shell
      systemctl enable docker
      ```

  3. Restart computer

### gcin Tools (Chinese input method)

Installation

```shell
sudo pacman -S gcin
```

Run gcin when booting

  1. Open or create `~/.xprofile` file

  2. Add content as follows to `~/.xprofile` file

      ```text
      export GTK_IM_MODULE=gcin
      export QT_IM_MODULE=gcin
      export LC_CTYPE=zh_TW.UTF-8
      export XMODIFIERS="@im=gcin"
      gcin &
      ```

  3. Restart computer

### Vim

```shell
sudo pacman -S vim
```

### Visual Studio Code

```shell
sudo pacman -S code
```

### Chromium

```shell
sudo pacman -S chromium
```

### Hyper

```shell
sudo pacman -S hyper
```

## Install packages by [AUR](https://aur.archlinux.org/)

> AUR: Arch linux user reposotory.

### Discord

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

### WPS Office

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

### HP System Software Manager

```shell
sudo pacman -Rs hplip
```

### Microsoft Office Online

```shell
sudo pacman -Rs ms-office-online
```
