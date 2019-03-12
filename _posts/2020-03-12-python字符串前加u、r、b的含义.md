---
layout: post
title:  "python字符串前加u、b、r的含义"
date:   2019-03-12 23:18:54
categories: python
tags: python
excerpt: 简单说明一下python字符串的编码含义
mathjax: true
---
* content
{:toc}

# python字符串前加u、b、r的含义
参见：[Python 字符串前面加u,r,b的含义](https://www.cnblogs.com/liangmingshen/p/9274021.html)
## 0x1 字符前加u
例：u"我是含有中文字符组成的字符串。"
作用：
后面字符串以 Unicode 格式 进行编码，一般用在中文字符串前面，防止因为源码储存格式问题，导致再次使用时出现乱码。

## 0x2 字符前加r
例：r"\n\n\n\n”　　# 表示一个普通生字符串 \n\n\n\n，而不表示换行了。
作用：
去掉反斜杠的转移机制。
（特殊字符：即那些，反斜杠加上对应字母，表示对应的特殊含义的，比如最常见的”\n”表示换行，”\t”表示Tab等。 ）
应用：
常用于正则表达式，对应着re模块。

## 0x3 字符前加b
例: response = b'<h1>Hello World!</h1>'     # b' ' 表示这是一个 bytes 对象
作用：
b" "前缀表示：后面字符串是bytes 类型。
用处：
网络编程中，服务器和浏览器只认bytes 类型数据。

## 0x4 字符串和bytes类型转换
```
In [1]: b = b'example'

In [2]: type(b)
Out[2]: bytes

In [3]: s = bytes.decode(b)

In [4]: s
Out[4]: 'example'

In [5]: type(s)
Out[5]: str

In [6]: t = str.encode(s)

In [7]: t
Out[7]: b'example'

In [8]: type(t)
Out[8]: bytes
```
