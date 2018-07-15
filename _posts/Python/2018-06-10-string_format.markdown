---
layout: post
title: string format
date: 2018-06-10 20:33:00 +08:00
tags: string
---

# str.format() #

## Basic formatting ##

```
'{} {}'.format(1, 2)
```

output  `1 2`
---

```
'{1} {0}'.format(1, 2)
```
output `2 1`

## Value conversion ##

```
class Data(object):

    def __str__(self):
        return 'str'

    def __repr__(self):
        return 'repr'

'{0!s} {0!r}'.format(Data())
```

output `str repr`


## 对齐和占位 ##

`format`方法默认是**左对齐**

```
# 右对齐，且输出字符串占位为10个字符宽度
{:>10}.format('test)

# 左对齐，且输出字符串占位为10个字符宽度
{:10}.format('test')

# 设置占位宽度个数
'{:<{}s}'.format('test', 8)

# 占位符号
'{:_<10}'.format('test')

# 居中
'{:^10}'.format('test')
```

## 截断 ##

```
# 输出前5个字符
'{:.5}'.format('abcdefghijk')

# 指定截断字符数
'{:.{}}'.format('abcdefghijk', 7)


## 数 ##
```
# 整型
'{:d}'.format(42)

# 浮点型
'{:f}'.format(3.1415926)
```

## Named placeholders ##

```
data = {'first': 'Hodor', 'last': 'Hodor!'}

'{first} {last}'.format(**data)
'{first} {last}'.format(first='Hodor', last='Hodor!')
```
