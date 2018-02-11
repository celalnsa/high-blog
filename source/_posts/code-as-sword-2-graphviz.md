---
title: "[代码即利剑2]用graphviz画流程图"
date: 2018-01-17 20:22:28
tags:
    - graphviz
    - flow-chart
categories:
    - 工具
---

本文介绍如何用graphviz画流程图。

<!-- more -->

### 工具安装
从[graphviz](http://www.graphviz.org/download/)下载安装

### 简单例子
可通过运行一个简单例子，验证是否安装成功。
新建`test.dot`文件，内容如下：
```
digraph abc{
  a;
  b;
  c;
  d;

  a -> b;
  b -> d;
  c -> d;
}
```

生成svg：
```
dot -Tsvg test.dot -o test.svg
```

生成的test.svg如下：
![test_graphviz](/asserts/images/test_graphviz.svg)

### 简单教程
详细教程参考官方文档[dotguide](https://graphviz.gitlab.io/_pages/pdf/dotguide.pdf)

#### 创建图
```
digraph abc {
}
```

#### 添加节点
可通过`[]`设置属性，常用`label`增加注解，`shape`指定形状，`color`指定颜色
```
a [label="节点a", shape="triangle"];
b [label="节点b", shape="circle", color="green"];
c [label="节点c", shape="point"];
d [label="节点d"];
```

#### 添加边
可通过`[]`设置属性，常用`label`增加注解，`style`指定形状，`color`指定颜色
```
a -> b [label="边ab", style="dashed"];
b -> d [label="边bd", style="dotted", color="green"];
c -> d [label="边ab"];
```

#### 子图
可通过`subgraph`创建子图，通过边在子图之间建立关联
```
subgraph sub {
    x;
    y;
    z;
    d -> x -> y -> z;
}
```

#### 完整示例
```
digraph abc {
  a [label="节点a", shape="triangle"];
  b [label="节点b", shape="circle", color="green"];
  c [label="节点c", shape="point"];
  d [label="节点d"];

  a -> b [label="边ab", style="dashed"];
  b -> d [label="边bd", style="dotted", color="green"];
  c -> d [label="边ab"];

  subgraph sub {
    x;
    y;
    z;
    d -> x -> y -> z;
  }
}
```
生成结果如下
![demo_graphviz](/asserts/images/demo_graphviz.svg)
