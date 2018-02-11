---
title: "[代码即利剑3]用reveal做ppt"
date: 2018-01-18 20:53:21
tags:
    - ppt
    - reveal
categories:
    - 工具
---

本文推荐使用reveal.js做ppt。

<!-- more -->

[reveal.js](https://github.com/hakimel/reveal.js)是一款专门用来做ppt的前端框架，支持markdown语法，可以方便地排版以及处理样式和动画，作为一个web服务，在浏览器中打开，同时也支持转成pdf。

### 安装
参考[官方文档](https://github.com/hakimel/reveal.js#installation)安装，如果不需要提供外部访问的服务，可以按照 **Basic setup** 指示，下载工程压缩包，解压后直接在浏览器中打开index.html文件即可。

### 使用
修改`index.html`文件，在`<div class="slides"></div>`标签里添加`<section></section>`即可增加一页ppt。
官方提供的`demo.html`本身是一个很好的文档，可以修改然后打开试试看，点击看[原效果](https://revealjs.com)
