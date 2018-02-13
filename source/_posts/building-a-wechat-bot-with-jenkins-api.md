---
title: "创建与jenkins通信的微信机器人"
date: 2017-05-11 21:01:26
tags:
    - jenkins
    - wechat
    - chatbot
categories:
    - 术业
---

基于当前自身对jenkins的使用经历, 加上最近发现了很多开源的微信api实现, 构思一个利用微信来执行任务并且查询任务状态的机器人.

<!-- more -->

### 微信api
基于网页版微信的通信机制, 很多人实现了各种语言的微信机器人api.
比如Python实现的[ItChat](https://github.com/littlecodersh/ItChat)和[wxpy](https://github.com/youfou/wxpy), 或者NodeJs实现的[wechaty](https://github.com/Chatie/wechaty).

### jenkinsapi
jenkins支持RESTful风格的接口调用, [jenkinsapi](https://github.com/pycontribs/jenkinsapi)提供了一套封装。

### 实现
先占坑，抽空再回来补上实现的部分。
