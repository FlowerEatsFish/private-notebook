# To install Golang in CentOS 6

## Introduction

- [CentOS v6 is in EOL](https://wiki.centos.org/About/Product)

  ![CentOS v6 is in EOL][centos-v6-is-in-eol]

  [centos-v6-is-in-eol]: https://raw.githubusercontent.com/FlowerEatsFish/private-repository/master/image/centos-6-is-in-eol.png "CentOS v6 is in EOL"

- [Transforming the development experience within CentOS](https://www.redhat.com/en/blog/transforming-development-experience-within-centos)

## Steps

### 1. Create a container using image `centos:6.10`

```shell
$ docker run --name centos-6 centos:6.10
```

### 2. Update installed repo source

```shell
# Enter the container
$ docker exec -it centos-6 bash
# [Optional] backup configs
$ mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup
# Update repo configs from https://archive.kernel.org to http://vault.centos.org
$ vim /etc/yum.repos.d/CentOS-Base.repo
```

```txt
# CentOS-Base.repo
#
# The mirror system uses the connecting IP address of the client and the
# update status of each mirror to pick mirrors that are updated to and
# geographically close to the client.  You should use this for CentOS updates
# unless you are manually picking other mirrors.
#
# If the mirrorlist= does not work for you, as a fall back you can try the
# remarked out baseurl= line instead.
#
#

[base]
name=CentOS-$releasever - Base
# mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=os&infra=$infra
baseurl=http://vault.centos.org/6.10/os/$basearch/
# baseurl=https://archive.kernel.org/centos-vault/6.10/os/$basearch/
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-6
enabled=1
metadata_expire=never

#released updates
[updates]
name=CentOS-$releasever - Updates
# mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=updates&infra=$infra
baseurl=http://vault.centos.org/6.10/updates/$basearch/
# baseurl=https://archive.kernel.org/centos-vault/6.10/updates/$basearch/
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-6
enabled=1
metadata_expire=never

#additional packages that may be useful
[extras]
name=CentOS-$releasever - Extras
# mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=extras&infra=$infra
baseurl=http://vault.centos.org/6.10/extras/$basearch/
# baseurl=https://archive.kernel.org/centos-vault/6.10/extra/$basearch/
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-6
enabled=1
metadata_expire=never

#additional packages that extend functionality of existing packages
[centosplus]
name=CentOS-$releasever - Plus
# mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=centosplus&infra=$infra
baseurl=http://vault.centos.org/6.10/centosplus/$basearch/
# baseurl=https://archive.kernel.org/centos-vault/6.10/centosplus/$basearch/
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-6
enabled=0
metadata_expire=never

#contrib - packages by Centos Users
[contrib]
name=CentOS-$releasever - Contrib
# mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=contrib&infra=$infra
baseurl=http://mirror.centos.org/6.10/contrib/$basearch/
# baseurl=https://archive.kernel.org/centos-vault/6.10/contrib/$basearch/
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-6
enabled=0
metadata_expire=never
```

### 3. Install Golang

```shell
$ yum update
$ yum install epel-release -y
$ yum install golang -y
```

### 4. Install Git to install Golang's modules

```shell
$ yum install http://opensource.wandisco.com/centos/6/git/x86_64/wandisco-git-release-6-1.noarch.rpm -y
$ yum install git -y
```
