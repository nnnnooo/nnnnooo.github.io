---
layout: post
title:  "XPath Position()"
date:   2019-06-24
---

> [博客园 - 清风软件测试](https://www.cnblogs.com/111testing/p/10848385.html)
> [博客园 - 无风](https://www.cnblogs.com/zhaozhan/category/209171.html)

## XPath 轴

基本的之前都有了解，今天新学到了两个定位轴，用于选取同级节点。（关于学习，感觉都是用到了才去学，学校课程系统性的学习总是感觉不能用上，老是记不住，学完了就忘光了。）
* preceding-sibling: 选取当前节点之前的所有同级节点
* following-sibling: 选取当前节点之后的所有同级节点

## 定位函数 `position()`

用法：

```
//div[@class="pt28"]/div[@class="rowCore"][position() > 1 and position() < last()-1]//text()

//B[position() mod 2 = 0 ]

//E[ position() = floor(last() div 2 + 0.5) or position() = ceiling(last() div 2 + 0.5) ]
```

可以将需要节点的位置定位到一个范围或者确切的值。