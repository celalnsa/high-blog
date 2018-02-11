---
title: "[代码即利剑1]用Markdown写文档"
date: 2018-01-16 19:33:37
tags:
    - markdown
    - document
categories:
    - 工具
mathjax: true
---

本文可被看做用Markdown写文档的基础教程。

<!-- more -->

### 例
常常会有整理文档的需求，以前都是用Word，排版麻烦，发给别人的时候可能还有兼容问题。Markdown作为纯文本，源文件清晰明了，也可以轻松地转成pdf/ppt/html等其他格式。
入门的话推荐用网页版如[https://zybuluo.com/mdeditor](https://zybuluo.com/mdeditor)先体验下，下图是一个简单的例子。

![Markdown简单例子](/asserts/images/markdown_mj.png)

### 语法

#### 标题层次

```
# 一级标题
## 二级标题
### 三级标题
```

#### 有序列表

```
1. aaa
2. bbb
3. ccc
```

1. aaa
2. bbb
3. ccc

#### 无序列表

```
* aaa
* bbb
* ccc
```

* aaa
* bbb
* ccc

#### 引用

```
> Mr.High is getting higher.
```

> Mr.High is getting higher.


#### 链接

```
[绘制图表](https://github.com/adrai/flowchart.js)
```

[绘制图表](https://github.com/adrai/flowchart.js)

#### 图片

```
![Mou icon](http://www.easyicon.net/api/resizeApi.php?id=1174091&size=128)
```

![Mou icon](http://www.easyicon.net/api/resizeApi.php?id=1174091&size=128)

#### 字体

```
**粗体**
*斜体*
~~删除线~~
也可以用<font>标签包裹指定字体
<font face="STCAIYUN">我是华文彩云</font>
<font color=gray size=5>color=gray</font>
<font color=#0099ff size=5 face="黑体">color=#0099ff size=5 face="黑体"</font>
```

**粗体**
*斜体*
~~删除线~~
<font face="STCAIYUN">我是华文彩云</font>
<font color=gray size=5>color=gray</font>
<font color=#0099ff size=5 face="黑体">color=#0099ff size=5 face="黑体"</font>

#### 表格

```
| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |
```

| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |

#### 代码

```
行内代码用一对`包裹
like this `print 'hello world'`
```

like this `print 'hello world'`

代码块用一对\`\`\`包裹:
\`\`\`
def hello():
    print 'hello world'
\`\`\`

```
def hello():
    print 'hello world'
```


#### 公式
用$$包裹LaTeX公式：

```
$e^{\imath x} = \cos{x} + \imath\sin{x}$
```

$e^{\imath x} = \cos{x} + \imath\sin{x}$
