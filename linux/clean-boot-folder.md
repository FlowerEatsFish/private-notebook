# Commands for cleaning boot folder

Check current version of Linux kernel:

```shell
uname -r
```

List all versions of Linux kernel images:

```shell
dpkg --list 'linux-image*'
```

Remove specific versions of Linux kernel images:

```shell
sudo rm -rf /boot/*-4.4.0-{53..83}-*
# Remove versions from 4.4.53 to 4.4.83.
```

Clean files in boot folder:

```shell
sudo apt-get -f install
sudo apt-get autoremove --purge
```