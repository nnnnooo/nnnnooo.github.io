---
layout: post
title:  "Rime 配置"
date:   2019-06-18
---

# Rime 配置
1. 配置

    * 当前使用的配置从这里下载的，做了一些改动：
    https://github.com/cnfeat/Rime
    **发现上面参考的出处应该是：**
    https://github.com/placeless/squirrel_config
    
    * 定制配置方法参考：
    https://blog.dwx.io/my-rime/
    https://scomper.me/gtd/-shu-xu-guan-de-diao-jiao-bi-ji
    
    * 官方 Rime 定制指南：
    https://github.com/rime/home/wiki/CustomizationGuide
    
    * Rime 輸入方案創作：
    https://github.com/rime/home/wiki/RimeWithSchemata

1. 数据文件位置

    共享资料夹：`”/Library/Input Methods/Squirrel.app/Contents/SharedSupport/”`  
    用户资料夹：`”~/Library/Rime/”`

1. 用户资料夹内的文件说明

    * 〔全局设定〕 default.yaml
    * 〔发行版设定〕 weasel.yaml
    * 〔预设输入方案副本〕 <方案标识>.schema.yaml
    * ※〔安装信息〕 installation.yaml
    * ※〔用户状态信息〕 user.yaml
    
    1. 用户自己设定的：
    
        * ※〔用户对全局设定的定制信息〕 default.custom.yaml
        * ※〔用户对预设输入方案的定制信息〕 <方案标识>.custom.yaml
        * ※〔用户自制输入方案〕及配套的词典源文件
    
    2. 编译输入方案所产生的二进制文件：
    
        * 〔Rime 棱镜〕 <方案标识>.prism.bin
        * 〔Rime 固态词典〕 <词典名>.table.bin
        * 〔Rime 反查词典〕 <词典名>.reverse.bin
        
    3. 记录用户写作习惯的文件：
    
        * ※〔用户词典〕 <词典名>.userdb.kct
        * ※〔用户词典快照〕 <词典名>.userdb.txt、<词典名>.userdb.kct.snapshot 见于同步文件夾
        
    * 注：以上标有「※ 号」和「粗体」的文件，包含用户资料，您在清理文件时要注意备份！

1. 我自己修改过的配置文件

 > 以下几个以 .custom.yaml 作为后缀的文件，意味着是以补丁的方式来实现个性化定制的，输入法后续升级不会覆盖这些文件。所以自定义的文件配置中起始部分都会有patch:的字段，每个配置文件中有且只需要一行这个代码段。
 
    * squirrel.custom.yaml
    自定义皮肤
    * default.custom.yaml
    设定备选词数量，定义输入方案
    * double_pinyin_flypy.custom.yaml
    定义扩充词库、加载符号库、模糊拼音
    * installation.yaml
    定义配置文件保存到 Documen 文件夹下
    
1. 鼠须管 Emoji 表情输入
来源：https://scomper.me/gtd/shu-xu-guan-de-pei-zhi-diao-zheng

1. 同步
在 `installation.yaml` 文件，添加一行：

    ```
    sync_dir: '/Users/forste/Document/ConfigurationFile/Rime'
    ```