---
layout: post
title:  "Rime 配置"
date:   2019-06-18
---

## 数据文件位置

- 共享资料夹

```
/Library/Input Methods/Squirrel.app/Contents/SharedSupport/
```

- 用户资料夹

```
~/Library/Rime/
```

## 用户资料夹内的文件说明

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

## 自用配置文件

以下几个以 .custom.yaml 作为后缀的文件，意味着是以补丁的方式来实现个性化定制的，输入法后续升级不会覆盖这些文件。

自定义的文件配置中起始部分都会有 patch: 的字段，每个配置文件中有且只需要一行这个代码段。
 
### 1. 自定义皮肤

```ini
# 文件：squirrel.custom.yaml
patch:
  style:
    # us_keyboard_layout: true                 # 键盘选项：应用美式键盘布局
    # 状态通知，适当，也可设为全开（always）全关（never）
    # show_notifications_when: appropriate

    color_scheme: regime

  preset_color_schemes:
    regime:
      name: Regime                                       # 24位色值，16进制，BGR顺序
      author: Forste, based on macOS 简体拼音输入法皮肤
      horizontal: true                                   # 水平排列
      inline_preedit: true                               # 单行显示，false双行显示
      candidate_format: "%c\u2005%@"                     # 用 1/6 em 空格 U+2005 来控制编号 %c 和候选词 %@ 前后的空间。
      corner_radius: 4                                   # 候选条圆角
      border_height: 4                                   # 窗口边界高度，大于圆角半径才生效
      border_width: 5                                    # 窗口边界宽度，大于圆角半径才生效
      back_color: 0xFFFFFF                               # 候选条背景色
      # border_color: 0x00FFFF                             # 边框色 （好像不起作用）
      font_face: "HYQiHei-55S Book,HanaMinA Regular"     # 候选词字体
      font_point: 16                                     # 候选字词大小
      text_color: 0x424242                               # 高亮选中词颜色
      label_font_face: "SimHei"                          # 候选词编号字体
      label_font_point: 11                               # 候选编号大小
      label_color: 0xcbcbcb                              # 预选栏编号颜色
      candidate_text_color: 0x474747                     # 预选项文字颜色
      # text_color: 0xFFFFFF                               # 拼音行文字颜色（没发现具体作用）
      # comment_text_color: 0xFFFFFF                       # 拼音等提示文字颜色（没发现具体作用）
      hilited_corner_radius: 3                           # 高亮圆角
      hilited_text_color: 0x9e9e9e                       # 高亮拼音 (需要开启内嵌编码)
      hilited_candidate_text_color: 0xFFFFFF             # 第一候选项文字颜色
      hilited_candidate_back_color: 0xFE7E1B             # 第一候选项背景背景色
      hilited_candidate_label_color: 0xFFFFFF            # 第一候选项编号颜色
      hilited_comment_text_color: 0x9e9e9e               # 注解文字高亮
```

### 2. 设定备选词数量，定义输入方案

```ini
# 文件：default.custom.yaml
patch:
  schema_list:
    - schema: double_pinyin_flypy
    - schema: luna_pinyin_simp
  menu/page_size: 5                     # 候选词数量
```

### 3. 定义扩充词库、加载符号库、模糊拼音

double_pinyin_flypy.custom.yaml

### 4. 定义配置文件保存到 Documen 文件夹下

installation.yaml
    
### 5. 鼠须管 Emoji 表情输入

来源：https://scomper.me/gtd/shu-xu-guan-de-pei-zhi-diao-zheng

### 6.同步

在 `installation.yaml` 文件，添加一行：

```
sync_dir: '/Users/forste/Document/ConfigurationFile/Rime'
```
    
-------

> [Placeless Squirrel Config](https://github.com/placeless/squirrel_config)

> [鼠须管 0.11 Mac 升级重装配置 2019](https://github.com/cnfeat/Rime)

> [我的 Rime](https://blog.dwx.io/my-rime/)

> [「鼠须管」的调教笔记](https://scomper.me/gtd/-shu-xu-guan-de-diao-jiao-bi-ji)
    
> [官方 Rime 定制指南](https://github.com/rime/home/wiki/CustomizationGuide)

> [Rime 輸入方案創作](https://github.com/rime/home/wiki/RimeWithSchemata)
