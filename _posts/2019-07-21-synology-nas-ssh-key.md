---
layout: post
title:  "Synology NAS 使用 SSH 密钥"
date:   2019-07-21
---

> [使用密钥登陆群晖 NAS SSH](https://gblog.sherlocky.com/shi-yong-ssh-zheng-shu-deng-lu-qun-hui-nas/)
> [SSH 小技巧](https://limboy.me/tech/2010/08/28/ssh-tips.html)
> [设置群晖 6.1 以及 6.2 使用证书免密登录](https://soulteary.com/2018/07/20/synology-passwordless-ssh.html)

## 两个坑

1. ~~在本地使用 `ssh-keygen` 生成密钥，使用 `ssh-copy-id` 上传密钥，返回权限不允许。~~（今天测试之后发现又可以了，无法复现问题）
2. 一直尝试在 NAS 使用 SSH 密钥，但是多次尝试在本地生成密钥，直接复制 pub 到 authorized_keys，依然需要密码。

看到上面那篇文章后，测试在 NAS 生成密钥，传到本地。测试后可以使用。

## 步骤

##### `ssh` 登录 NAS

使用 root 账户，可以直接进入到 `/var/services/homes/admin/.ssh/` 目录，方便生成密钥后管理。

##### 生成密钥

```sh
ssh-keygen -t rsa -b 2048 -C "NASCert" -f nas
```

##### pub 复制到 authorized_keys，直接覆盖原数据

```sh
cat nas.pub > /var/services/homes/admin/.ssh/authorized_keys
```

##### 修改 sshd 配置文件

```sh
// 开启RSA证书验证  
RSAAuthentication yes
// 开启公钥证书验证
PubkeyAuthentication yes
// 公钥证书就放在这个文件里
AuthorizedKeysFile  .ssh/authorized_keys
// 测试后没有问题可以禁用密码验证
PasswordAuthentication no
```

##### 重启 sshd

```sh
synoservicectl --reload sshd
synoservicectl --restart sshd
```

## 本地配置文件

配置 .ssh/config 文件


```ini
Host bob
    HostName bob.example.com
    Port 2222
    User wdaher
    IdentityFile ~/.ssh/nas
```

连接时，使用：

```
ssh bob
```

