---
title: 在react-native中利用appium进行自动化集成测试
date: 2017-04-28 19:31:17
tags:
    - react-native
    - automated-test
    - appium
    - android
    - python
categories:
    - 术业
---

本篇文章简单介绍如何在react-native中使用appium进行e2e自动化测试。

<!-- more -->

### Appium与WebDriver
[Appium](http://appium.io/)是一个用来对移动设备App进行集成测试的工具。
[WebDriver](https://www.w3.org/TR/webdriver/)是用任意语言模拟浏览器行为的标准，主要用在[Selenium](http://www.seleniumhq.org/)系列的工具，用来对web项目进行集成测试。

### ReactNative中的实现
Appium可以用 **uiautomator** 进行页面元素的查找和操作，用react-native写的Android页面，为了方便查找可以设置`accessibilityLabel`.
如下的一个Component实现：
```jsx
<TouchableNativeFeedback
    background={TouchableNativeFeedback.Ripple("red", true)}
    accessibilityLabel="clickZone"
    onPress={counter}
>
    <View style={DynamicStyle.AccessibilityLabel.clickZone}>
        <Text>Some Text</Text>
    </View>
</TouchableNativeFeedback>
```
其中给一个可点击的`TouchableNativeFeedback`设置了`accessibilityLabel="clickZone"`.

+ Appium脚本的实现
在Appium脚本中可以进行View的查找和点击：
```python
desired_caps = {
    'platformName': 'Android',
    'deviceName': 'Meizu MX5',
    'appPackage': 'com.androidcode',
    'appActivity': '.MainActivity',
}
driver = webdriver.Remote('http://localhost:4723/wd/hub', desired_caps)

sleep(5)
try:
    ## 用accessibilityLabel定位元素
    el = driver.find_element_by_accessibility_id('clickZone')
    assert el
    ## 模拟点击3下
    map(lambda x: el.click(), range(0, 3))

    ## 用Text属性定位元素
    els = driver.find_elements_by_android_uiautomator('new UiSelector().textContains("Some")')
    assert els
    logging.warning(els[0].text)
except Exception, e:
    logging.error(e, exc_info=True)

driver.quit()
```
