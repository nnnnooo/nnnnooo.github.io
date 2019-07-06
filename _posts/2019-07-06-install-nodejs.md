
---
layout: post
title:  "Synology 安装 qBittorrent"
date:   2019-07-06
---

### 安装 Node

#### 安装步骤：

##### 使用 Homebrew 安装

```sh
brew link node
brew uninstall node
brew install node
```

##### 使用安装包

[官网](https://nodejs.org/dist/)下载的安装包。

安装包会一键同时安装 Node 和 npm，无需再额外安装 npm，但是 cnpm 还需要手动安装。

#### 验证是否安装成功

`npm -v`、`node -v`，能正确显示版本号即表示node安装成功。

#### 安装 cnpm

npm 由于源服务器在国外下载 Node 包经常超时，cnpm 使用国内镜像，通过以下命令安装 cnpm。

```sh
npm install -g cnpm --registry=https://registry.npm.taobao.org
```

> cnpm 参考：[淘宝 NPM 镜像](http://npm.taobao.org/)

### npm 权限

```sh
sudo chown -R $USER /usr/local
或
sudo chown -R $(whoami) /usr/local
```

### 删除 Node

1. 如果是通过 Homebrew 安装的，下发命令`brew uninstall node`即可。
2. 如果是通过安装包安装的，下发命令`cnpm -v`，可以查看 Node 的安装位置（一般位于 `/usr/local/lib`)，手动删除安装目录即可。