---
layout: post
title:  "修改 Torrent 文件"
date:   2019-07-15
---

> [R 酱小窝 - 通过编辑修改 torrent 文件来辅种](https://blog.rhilip.info/archives/1059/)

### 三种类型

[@DXV5](https://github.com/DXV5 "@DXV5") 将修改情况大致分为以下3种情况：

1. 只修改了announce字段，或添加announce-list的list  
2. 修改了announce、announce-list、source字段  
3. 除了常规的修改announce、announce-list、source字段，还会添加或者修改一些字段ttg_tag,publisher-url,comment或者一些特殊的检验字段什么的。  

### 编辑文件

* 工具：Torrent File Editor

##### 新种

![未下载验证前的种子-c600]({{ "/images//15631784826411.jpg" }})

![未下载验证前的种子-c600]({{ "/images//15631786736900.jpg" }})

该文件为未上传的种子，上传后需要将文件下载验证，部分数据会被修改和添加，如 info 下的 source 会被添加，Tracker 会被修改。

如果是将一个文件上传多给站用，只需要修改 tracker，annouce 会自动修改。

##### 旧种

![旧种-c600]({{ "/images//15631791649577.jpg" }})

![旧种-c600]({{ "/images//15631792595879.jpg" }})

该文件就是上传后重新下载的种子，服务器将 annouce-list 删除，添加了source，annouce、tracker 也修改了。

如果需要重新上传到其他站点，修改 tracker 和 source。
