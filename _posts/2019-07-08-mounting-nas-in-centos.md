---
layout: post
title:  "CentOS 挂载 Synology NAS"
date:   2019-07-08
---

> [icodding愛程式 - CentOS 掛載 samba storage](http://icodding.blogspot.com/2015/09/centos-samba-storage.html)
> [Mounting NAS Storage in Linux](https://cloud.ibm.com/docs/infrastructure/network-attached-storage?topic=network-attached-storage-mountNASLinux)

#### 1. 安装 smbclient 和 cifs-utils

```sh
yum install -y cifs-utils smbclient
```

#### 2. 检测连接

```sh
smbclient -U USERNAME -L //192.168.1.10
```

#### 3.挂载

```sh
mount -t -o username="USERNAME",password="PASSWORD" cifs //192.168.1.10/ /mnt/nas
```

#### 4. 查看磁盘空间

```sh
df -h
```

#### 5. 自动挂载

```sh
vim /etc/fstab
//192.168.1.10   /mnt  smbfs   defaults   0 0
```

检测一下

```sh
mount -a
```