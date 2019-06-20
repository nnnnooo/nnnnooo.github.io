---
layout: post
title:  "「!」使用"
date:   2019-06-17
---

## 从历史记录中使用命令号来运行命令

首先输入 `history` 命令得到命令的序号，使用 `!加序号` 就能执行该命令

## 执行指定的之前执行过的命令

`!负数` 执行你记录序列中的倒数第 X 条命令

## 向一条新命令传递旧命令的参数避免重复输入

`!$` 符号可以将上一条命令的参数传递给下一条命令参数

## 如何用(!)处理两个以上的参数

例如我在桌面上创建了一个 1.txt 文件

```sh
touch ~/Destop/1.txt
```

然后使用CP命令把它复制到 ‘~/Downloads’ 目录

```sh
cp ~/Destop/1.txt ~/Downloads
```

这样我们就向CP命令传递了两个参数。第一个是 ‘~/Destop/1.txt’ ，第二个是 ’~/Downloads’，为了区分它们，我们使用 echo 来打印每个参数。

```sh
echo "1st Argument is:!^"
echo "2nd Argument is:!cp:2"
```

- `!^` 表示第一个参数
- `!命令名：参数序号` ，比如 `!cp:2`表示第二个参数
- `!*` 表示所有参数

## 通过关键词来执行之前的命令

我们可以通过执行关键词来执行之前的命令。可以按照下面的命令来理解：

```sh
ls /home > /dev/null                    [Command 1]
ls -l ~/Desktop > /dev/null             [Command 2]
ls -la ~/Downloads > /dev/null          [Command 3]
ls -lA /usr/bin > /dev/null             [Command 4]
```

上面是相同的ls命令对应了不同参数和文件夹。此外我们将每一个标准输出都传递到了 ‘/dev/null’ 因为我们并不希望处理程序的标准输出。现在我们可以调用命令的关键词来实现它们。

```sh
!ls         [Command 1]
!ls -l      [Command 2]
!ls -la     [Command 3]
!ls -lA     [Command 4]
```

当你使用 “ls” 关键词来执行之前命令的时候，你一定会被标准输出给惊讶到。

## 使用(!!)来运行或者改变之前的命令

昨天我运行了一个获取IP的Shell命令：

```sh
ip addr show | grep inet | grep -v 'inet6' | grep -v '127.0.0.1' | awk '{print $2}' | cut -f 1 -d/
```

突然我意识到需要将结果重定向到 ip.txt 中，这时你应该想到用 “UP” 键恢复上一个命令再加上 ‘>ip.txt‘ 命令来重定向进去：

```sh
ip addr show | grep inet | grep -v 'inet6' | grep -v '127.0.0.1' | awk '{print $2}' | cut -f1 -d/ > ip.txt
```

感谢这次救命的”UP” 键。那么再考虑下这个场景，如果我需要运行下面的这个脚本：

```sh
ifconfig | grep 'inet addr:' | awk '{print $2}' | grep -v '127.0.0.1' | cut -f2 -d:
```

当我运行它的时候突然报出了 ”bash:ifconfig:command not found” 错误，我意识到可能是我设定了这个命令需要 root 权限来运行它。那么现在怎么办？需要重新登录 root 账号来执行它么？这种情况下使用 ”up” 键也并不管用。所以这里我们使用 `!!` 命令来选择调用这条命令。

```sh
su -c "!!" root
```

显而易见的是 su 是用来选择执行用户的， -c 是用来表示执行具体命令的，最重要的部分 `!!` 代替了你最后一次运行的命令。然后输入你的root密码即可运行它了。

## 使用 !(文件名) 的方式来避免命令对某个文件的影响

这里的 “!” 符号相当于逻辑否定来使用，用来避免对加了 “!” 前缀的文件产生影响。

A.从目录中删除除 2.txt 外的所有文件:

```sh
rm !(2.txt)
```

B.从目录中删除 pdf 为后缀以外的文件（请忽略下图中多出来的一个$）:

```sh
rm !(*.pdf)
```

## 检查某个目录是否存在，如果存在就将其打印

这里使用 `! -d`  命令来判断目录是否为空，同时使用 “&&” 和 “||” 命令来打印判断目录是否存在：

```sh
[ ! -d ~/Tecmint ] && printf '\nno such ~/Tecmint directory exist\n' || printf '\n~/Tecmint directory exist\n'
```

## 检测目录是否是否为空，如果为空则退出

和上面的命令类似。这里是检测目录是否为空，如果为空则退出命令

```sh
[ ! -d ~/Tecmint ] && exit
```


## 检测目录是否为空，如果为空则在 home 目录中重新创建目录

```sh
[ ! -d ~/Tecmint ] && mkdir ~/Tecmint
```

