---
title: "[代码即利剑4]用alda作曲"
date: 2018-01-19 20:03:46
tags:
    - alda
    - compose
categories:
    - 工具
---

本文介绍如何使用alda编写曲谱。

<!-- more -->

alda的官方描述：A music programming language for musicians.
很酷吧。
可以在官方的[web-demo](http://alda-lang.github.io/web-demo/)先体验一下

### 安装
参考[官方介绍](https://github.com/alda-lang/alda#installation)安装alda.
启动alda服务
```
alda up
```

### 语法
首先尝试演奏一小段：
```
alda play --code "piano: c6 d12 e6 g12~4"
```

`piano: c6 d12 e6 g12~4`就是alda写乐谱时的基本格式
首先指定乐器`piano：`然后是音`c`和表示时长的`6`

#### 乐器
alda支持的乐器[列表](https://github.com/alda-lang/alda/blob/master/doc/list-of-instruments.md)

#### 音高
十二平均律把音分成从低到高的`c c# d d# e f f# g g# a a# b`
在alda里，可以表示为`c c+ d d+ e f f+ g g+ a a+ b`，当然降c可以表示为`c-`
在乐谱的开头可以指定Octave为第几个八度：
```
piano: o3 c d e g
```

在乐谱中可以用`>`将后续音符提高一个八度，用`<`降低一个八度：
```
piano: o4 c d e g > c d e g < c d e g
```

#### 音长
alda音符后面的数字指示音的长短：
* c4表示一个1/4拍的c，c8表示一个1/8拍的c，注意没指定时默认用之前指定过的音长，如`c2 d e`中c后面的d和e都会变成1/2拍
* g12~4表示一个1/12拍加1/4拍的g
```
piano: c6 d12 e6 g12~4
```

#### 休止音符
休止音符用r表示，仍然可以跟数字表示音长：
```

#### 和弦
可以用/表示同时奏响，如：
```
piano: c/e/g c/e/g c/e/a c/e/a
```

#### 多乐器合奏
```
piano:
  c6 d12 e6 g12~4 r4 c6 d12 e6 a12~4

guitar:
  c/e/g6 r3 r2 c/e/g6
```

#### 一个例子
新建乐谱`test.alda`，内容：
```
(tempo! 90)
(quant! 95)

piano:
  o5 g- > g- g-/f > e- d-4. < b-8 d-2 | c-4 e- d- d- <b-1/>g-

flute:
  r2 g-4 a- b-2. > d-32~ e-16.~8 < b-2 a- g-1
```
播放乐谱
```
alda play --file test.alda
```

### Alda REPL
alda提供了交互式命令行的服务，通过`alda repl`进入交互式命令行状态，可以直接敲乐谱的代码播放。
