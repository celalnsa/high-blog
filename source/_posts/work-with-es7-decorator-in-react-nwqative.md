---
title: 在react-native中使用es7的decorator
date: 2017-04-15 08:27:03
tags:
    - es7
    - decorator
    - react-native
categories:
    - 写代码
---

本篇文章记录如何在react-native中使用es7的decorator提案
[了解decorator](https://github.com/wycats/javascript-decorators)
或者看[阮一峰的ECMAScript 6 入门](http://es6.ruanyifeng.com/#docs/decorator)

<!-- more -->

配置babel
==========

安装依赖
-----------

在react-native项目里安装 **babel-plugin-transform-decorators-legacy** 和 **babel-preset-react-native** 这两个库:
```bash
npm install --save-dev babel-plugin-transform-decorators-legacy
npm install --save-dev babel-preset-react-native
```

.babelrc
-----------

在项目根目录(*package.json所在的目录*)添加 *.babelrc* 文件:
```javascript
{
  "presets": [
    "react-native"
  ],
  "plugins": [
    "transform-decorators-legacy"
  ]
}
```

其中`"presets": ["react-native"]`是为了让babel首先兼容react-native的其他配置,参考[babel-preset-react-native](https://github.com/facebook/react-native/tree/master/babel-preset)

应用
==========

autobind
--------

举例使用 *autobind-decorator* 这个库, 其作用是在声明方法时自动bind(this):
安装
```bash
npm install --save autobind-decorator
```

为类方法添加装饰器

```jsx
import React from 'react';
import ReactNative from 'react-native';
const {
    TouchableNativeFeedback,
    View,
    Text,
} = ReactNative;

import autobind from 'autobind-decorator';

class A extends React.Component {
    constructor() {
        super();
        this.state = {
            count: 0,
        };
    }

    @autobind
    handlePress() {
        //此方法会被自动bind(this)
        this.setState({
            count: this.state.count + 1,
        });
    }

    render() {
        return (
            <View style={{flex: 1}}>
                <TouchableNativeFeedback onPress={this.handlePress}>
                    <View>
                        <Text>{this.state.count}</Text>
                    </View>
                </TouchableNativeFeedback>
            </View>
        );
    }
}
```

更多使用decorator的例子
----------
+ 为组件实现scu, 参考[pure-render-decorator](https://github.com/felixgirault/pure-render-decorator)
+ 打印生命周期方法的调用log
```javascript
@lifecycleLog
class B extends React.Component {
}
```

推广
=========
同理可得任意需要扩展babel plugin的配置方法
