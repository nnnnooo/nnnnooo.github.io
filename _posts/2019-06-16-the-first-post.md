---
layout: post
title:  "Markdown快速入门"
date:   2019-06-16
---

![My helpful screenshot]({{ "/images/pic01.jpg"}})

> Markdown是一种标记语言，它因为“代码简练、显示精美”而受到很多人的喜爱。在这篇文章你将初步入门Markdown。
>  MWeb 兼容 GFM 语法，还扩展支持两种语法：画图支持（mermaid, viz, echarts, plantuml, sequence, flow）和设置图片宽度（-c, -l, -r, -w）

[TOC]

## 标题

在Markdown中总共有6个标题，我们分别把它们称为：一级标题、二级标题、三级标题、四级标题、五级标题和六级标题。其中六级标题**最小**，一级标题**最大**。

```
    # 一级标题
    ## 二级标题
    ### 三级标题
    #### 四级标题
    ##### 五级标题
    ###### 六级标题
```
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题
    
## 换行

在Markdown之中我们会发现文字无法换行，始终集中在一行之中。在这里可以使用 HTML 换行标签 `</br>`。

## 分割线

分割线在我们写文章或笔记的时候是一个不可缺少的内容，它可以清楚的将文章分成不同的层次。在Markdown中分割线代码如下：

    看
    ***
    分割线

看
***
分割线

## 引用

在我们想要引用一句话的时候，我们在Markdown中使用如下代码：

    > 引用话语
    
> 引用的内容

## 文字样式

在Markdown中有：斜体、加粗、高亮、划线。这些文字样式供我们选择，代码如下：

    *斜体*</br>**加粗**</br>==高亮==</br>~~划线~~

<center>*斜体*</br>**加粗**</br>==高亮==</br>~~划线~~</center>

但如果我们想修改文字大小/颜色/字体，就要用font标签，代码如下：

    <font color=##78B756 size=10 face="宋体"><center>测试字体</center></font>
    
<font color=##78B756 size=10 face="STFangsong"><center>测试字体</center></font>

color代表字体颜色（要用16进制颜色值），size代表文字大小，face代表字体

最后我们来实现“文字居中”就要center标签，代码如下：

    <center>居中</center>

<center>居中</center>

**Ps：center和font都是html的标签，在markdown也能用**

## 代码高亮

**在Markdown中如果我们想要高亮一段代码，可以使用如下代码：**

    ```key
      代码
     ```

```sh
ls /
```

代码格式就是上面的，当然key要换成自己需要的编程语言，以下是编程语言对应的key

（来源：[互联网](https://sspai.com/post/45816)）

language | key
--- | ---
1C | 1c
ActionScript | actionscript
Apache | apache
AppleScript | applescript

## 列表

在Markdown中我们可以绘制列表，代码格式如下：

    - 列表1  
    - 列表1.1  
    - 列表1.2

- 列表1  
- 列表1.1  
- 列表1.2

```    
+ 列表1
+ 列表1.1
+ 列表1.2
```

+ 列表1
+ 列表1.1
+ 列表1.2


```
1. 列表1
2. 列表1.1
3. 列表1.2
```
1. 列表1
2. 列表1.1
3. 列表1.2

## 代办事项

在Markdown中你可以输入你最近的代办事项，代码格式如下：

    - [ ] 未完成事项
    - [x] 已完成事项

Ps：带x的代表已经完成的事项，空格的为还没有完成的事项

- [ ] 未完成事项
- [x] 已完成事项

</br>

## 链接以及图片

在Markdown中添加链接和图片有异曲同工之妙，所以我们放在一起来讲，代码如下：

    [少数派](https://sspai.com/)
    ![logo-w150](https://partner-cdn.lizhi.io/api/www//uploads/少数派.png)

[少数派](https://sspai.com/)
![-w150](https://partner-cdn.lizhi.io/api/www//uploads/少数派.png)

</br>

## 表格

在Markdown中我们同样可以绘制表格，代码格式如下：
  
```
大标题1|大标题2|大标题3
---|---|---
内容1|内容2|内容3
内容1|内容2|内容3
```

大标题1|大标题2|大标题3
---|---|---
内容1|内容2|内容3
内容1|内容2|内容3

## ## LaTeX （MathJax 渲染）

Markdown 语法：

```
块级公式：
$$  x = \dfrac{-b \pm \sqrt{b^2 - 4ac}}{2a} $$

\\[ \frac{1}{\Bigl(\sqrt{\phi \sqrt{5}}-\phi\Bigr) e^{\frac25 \pi}} =
1+\frac{e^{-2\pi}} {1+\frac{e^{-4\pi}} {1+\frac{e^{-6\pi}}
{1+\frac{e^{-8\pi}} {1+\ldots} } } } \\]

行内公式： $\Gamma(n) = (n-1)!\quad\forall n\in\mathbb N$

```

块级公式：
$$  x = \dfrac{-b \pm \sqrt{b^2 - 4ac}}{2a} $$

\\[ \frac{1}{\Bigl(\sqrt{\phi \sqrt{5}}-\phi\Bigr) e^{\frac25 \pi}} =
1+\frac{e^{-2\pi}} {1+\frac{e^{-4\pi}} {1+\frac{e^{-6\pi}}
{1+\frac{e^{-8\pi}} {1+\ldots} } } } \\]

行内公式： $\Gamma(n) = (n-1)!\quad\forall n\in\mathbb N$

## 脚注（Footnote）

```
这是一个脚注：[^sample_footnote]

[^sample_footnote]: 这里是脚注信息

```

这是一个脚注：[^sample_footnote]

## 注释和阅读更多

Actions->Insert Read More Comment *或者* `Command + .`
**注** 阅读更多的功能只用在生成网站或博客时，插入时注意要后空一行。

## TOC(Table of Contents)

```
[TOC]
```

* * *

[^sample_footnote]: 这里是脚注信息