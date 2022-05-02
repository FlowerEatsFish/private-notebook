# EndeavourOS

EndeavourOS is an Arch Linux based Linux distribution.

- [EndeavourOS](#endeavouros)
  - [Partitions](#partitions)
    - [Legacy boot mode](#legacy-boot-mode)
    - [UEFI boot mode](#uefi-boot-mode)
  - [Install packages by Pacman](#install-packages-by-pacman)
    - [Docker](#docker)
  - [Install packages by AUR](#install-packages-by-aur)
  - [Remove packages with associated libraries](#remove-packages-with-associated-libraries)

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

> `man pacman`
>
> Ref: <https://man.archlinux.org/man/pacman.8.en>

```shell
sudo pacman --sync --refresh --sysupgrade [package name]
```

### Docker

1. Install Docker

    ```shell
    sudo pacman -S docker
    ```

2. Run docker with current user

    1. Add current user to "docker" group

        ```shell
        sudo usermod -aG docker $USER
        ```

    2. Auto-start docker when booting

        ```shell
        systemctl enable docker
        ```

    3. Restart computer

## Install packages by [AUR](https://aur.archlinux.org/)

> AUR: Arch linux user repository.
>
> `man makepkg`
>
> Ref: <https://man.archlinux.org/man/makepkg.8.en>

```shell
git clone https://aur.archlinux.org/google-chrome.git
```

```shell
makepkg --syncdeps --install [package name]
```

## Remove packages with associated libraries

```shell
sudo pacman --remove --recursive [package name]
```
