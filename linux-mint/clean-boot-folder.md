Check current version of Linux kernel:
```linux
$ uname -r
```

List all versions of Linux kernel images:
```linux
$ dpkg --list 'linux-image*'
```

Remove specific versions of Linux kernel images:
```linux
$ sudo rm -rf /boot/*-4.4.0-{53..83}-*
# Remove versions from 4.4.53 to 4.4.83.
```

Clean files in boot folder:
```linux
$ sudo apt-get -f install
$ sudo apt-get autoremove --purge
```