---
layout: post
title:  "XPath Position()"
date:   2019-06-24
---

> [我的高清之旅](http://instantmove-hdtravel.lofter.com/post/1cc1d49b_3745d48)
> [Transmission Web Control](https://github.com/ronggang/transmission-web-control)

## 更改 Transmission 密码

之前使用的默认密码，因为懒癌一直没有修改，因为安装 qBittorrent需要设置密码，所以就想起把 Tr 的登录密码也修改了。

修改密码前需要将 Tr 停止运行，否则修改无效。ssh 到 NAS 后，以 root 身份修改文件 Transmission 的配置文件，在 NAS 中存放的路径为：(假定 transmission 安装在磁盘 1 空间中)

```ini
/volume1/@appstore/transmission/var/settings.json
```

 打开 settings.json 文件，修改如下内容:

```json
"rpc-authentication-required": true,
"rpc-enabled": true, 
"rpc-password": "密码", 
"rpc-username":"admin",
```

在 DSM 的套件中心中重新启动 Transmission即可。

## Transmission Web Control

安装前如果想保留保留原版 Web UI，将原有的文件夹内 `index.html` 修改为 `index.original.html`。

### 手动安装
把压缩包中解压出的 web 文件夹拷贝到 Transmission 路径下。
Transmission 的 Web 控制器存放路径为:

```
/volume1/@appstore/transmission/share/transmission/web
```

### 脚本安装

* wget

```sh
wget https://github.com/ronggang/transmission-web-control/raw/master/release/install-tr-control-cn.sh --no-check-certificate
```

* curl

```
curl -o install-tr-control-cn.sh https://github.com/ronggang/transmission-web-control/raw/master/release/install-tr-control-cn.sh
```

因为我的 NAS 不支持 https，同时也不支持 `--no-check-certificate` 选项，所以使用了 `curl`，同时脚本中的几处需要将 `wget` 修改为 `curl`。

