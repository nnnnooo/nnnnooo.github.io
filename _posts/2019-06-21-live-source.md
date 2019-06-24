---
layout: post
title:  "电视直播源"
date:   2019-06-21
---

## 直播源

* [恩山iptv 信源、TV 频道、网络机顶盒频道](https://www.right.com.cn/forum/forum.php?mod=forumdisplay&fid=182&page=1&filter=author&orderby=dateline)
* [freearhey - IPTV](https://github.com/freearhey/iptv)
* [EvilCult - iptv-m3u-maker](https://github.com/EvilCult/iptv-m3u-maker)

## 正则筛选

1. 网址筛选`(?<=://).*(?<=\.)([a-z]*)(\:\d*)*(?=\/)`
2. 网址去多余后缀`/.*$`
3. 一级域名筛选`[a-z0-9]*\.[a-z]*$`
4. IP 筛选`\d*(\.\d*){3}`
5. 去重`([a-z0-9]*\.[a-z0-9]*)(?=\n\1)` `(\d*(\.\d*){3})(?=\n\1)`
6. 去除空行`\n(?=\n)`

## 添加域名和 IP 到代理

* gfwlist 文件地址：/etc/dnsmasq.ssr/custom_forward.conf，可以通过LUCI添加
* ip 文件：没找到……暂时手动添加
