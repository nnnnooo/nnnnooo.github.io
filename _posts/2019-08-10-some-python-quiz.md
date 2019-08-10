---
layout: post
title:  "PT 助手"
date:   2019-07-14
---

- 1.编写代码，打印 1-1 亿之内的偶数

```py
def even_maker(x):
    # generator
    # 遇到 yield 语句返回，再次执行时从上次返回的 yield 语句处继续执行。
    g = (i for i in range(1, int(x/2 + 1)))
    for i in g:
        yield i * 2

for i in even_maker(10**9):
    print(i, ',')
```

- 2.写一个函数，用正则表达式清除字符串中 [] 和其中的内容。s = "[lol] 你好，帮我把这些 markup 清掉，[smile]。谢谢！"

```py
s = "[lol]你好，帮我把这些markup清掉，[smile]。谢谢！"
print re.sub('\[.*?\]', '', s)
```

- 3.请使用 Python, 对下面的函数进行处理

```py
def hello(name):
print "hello, %s" % name
在函数被调用时打印耗时详情
```

```sh
<function name: hello>
<function call begin>
hello, tom
<function call end>
[timecosts: 3.81469726562e-06s]
```

```py
def name_and_time_func(func):
    def name_time(*param):
        start_time = datetime.datetime.now()
        print '<function name: %s>', func.__name__
        print '<function call begin>'
        func(*param)
        print '<function call end>'
        time.sleep(1)  # 可以不加，但是不加的话看不出来时间间隔
        print '[time costs: %s]', datetime.datetime.now() - start_time
    return name_time

@name_and_time_func
def hello(name):
    print "hello, %s" % name

hello('apple')
``` 

- 4.写一个函数，将驼峰命名法字符串转成下划线命名字符串，如 GetItem -> get_item，getItem -> get_item

```py
def camel_name(name):
    _name = re.sub('[A-Z]', lambda x: '_' + x.group(0).lower(), name)
    return _name if _name[0] != '_' else _name[1:]  # 替换完之后有可能第一个字母是下划线，需要去掉

names = ['GetItem', 'getItem', 'getitem']
    for i in names:
        print camel_name(i)
``` 

- 5.打印列表：[1, 2, 3, 4...n]，n=20；请编写代码打印如下规律的输出：

```
        1 [1*, 2, 3, 4, 5]
        2 [1, 2*, 3, 4, 5]
        3 [1, 2, 3*, 4, 5]
        4 [2, 3, 4*, 5, 6]
        5 [3, 4, 5*, 6, 7]
        6 [4, 5, 6*, 7, 8]
        ...
        20 [16, 17, 18, 19, 20*]
```

```py
def page_print(page, total=20, width=5):
    # page是当前页码，就是标*的页码
    # total是总页码
    # width是显示的页数（*页码会出现在中间）

    # 设置打印页码，避免超出范围
    if page < 1:
        page = 1
    if page > total:
        page = total

    # 设置起始页码
    if page < width / 2 + 1:
        start = 1
    elif page > total - width / 2:
        start = total - width
    else:
        start = page - width / 2

    ret = str(page) + '['
    for i in xrange(start, start + width + 1):
        if i == page:
            ret += '*'
        ret += str(i)
        if i != start + width:
            ret += ', '
        else:
            ret += ']\n'

return ret

t = 18
for i in xrange(1, t + 1):
    print page_print(page=i, total=t, width=8)
``` 

- 6.写一个程序模拟银行排队，只有一个队伍，一个用户进入时允许插队 (进入队伍任意位置), 但要保证每次导致队伍变更，队伍中受影响的人都收到通知

```sh
Customer A line up at position 11
Customer B: order changed to 12
Customer C: order changed to 13
Customer D: order changed to 14
``` 

- 7.用户系统，存在相互关注的动作，当进入某个人的个人主页，需要展示其粉丝数，关注数，粉丝列表以及关注列表。请简要描述解决方案，包括 db 建模 / 数据层 / 业务层，以及应对高并发 / 关注取关等情况的处理逻辑。

- 8.给定一些 NxN 的矩阵，对于任意的路线，定义其【和】为其线路上所有节点的数字的和，计算从左上角到右下角的路线和最小值。每条路线只能从某一点到其周围（上下左右）的点，不可斜行。 例如，

```sh
4,6
2,8 的路线和最小值为 4-2-8 14
```

```sh
1,2,3
4,5,6
7,8,9 的路线和最小值为 1-2-3-6-9 21
```

---

> [几个 python 练习题](https://www.cnblogs.com/anpengapple/p/5071215.html)