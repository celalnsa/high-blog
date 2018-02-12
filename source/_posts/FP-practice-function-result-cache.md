---
title: "函数式编程实践-缓存函数执行结果"
date: 2017-04-27 20:00:06
tags:
    - functional-programing
    - python
categories:
    - 术业
---

受函数式编程思想启发, 实现Python函数缓存装饰器。

<!-- more -->

### 纯函数
学习函数式编程可以看[JS函数式编程指南中文版](https://github.com/llh911001/mostly-adequate-guide-chinese)
纯函数可测，可重演，最重要的是，因为同样的输入一定会产生同样的输出，使得函数的执行结果是可以被缓存的。

### 实现
利用Python的闭包来实现一个缓存函数执行结果的装饰器：
```python
def cache_result(f_key=lambda x: x, expired=0):
    """
    @param f_key: cache_key生成函数
    @param expired: cache有效时间
    @return: 带cache功能的原函数
    """
    def dec(func):
        cache_v = {}
        cache_t = {}

        def new_func(*args, **kwargs):
            key = f_key(*args, **kwargs)
            if key not in cache_t or expired and time.time() - cache_t[key] >= expired:
                cache_v[key] = func(*args, **kwargs)
                cache_t[key] = time.time()
            return cache_v[key]
        return new_func
    return dec
```
`f_key`是函数入参生成的key，相当于唯一标识一组入参，默认值是id函数(像`x => x`这样的)。
`expired`是函数缓存的有效时间。
可以看到在`new_func`的逻辑当中，只有当缓存里没有这个key，或者缓存的时间已经过期时，才会重新执行原来的函数`func`并更新缓存。

### 使用
如下是一个需要读取redis数据的函数，注意这个函数不是一个纯函数，因为返回结果收到外部环境(redis缓存)影响。但这里数据的实时变化频次很低，近似地认为在一段时间(5秒)内，函数的执行结果是不变的。
```python
@cache_result(lambda self, user_id, locale: RedisDataHelper.get_data_key(user_id, locale), 5)
def get_data(self, user_id, locale):
    ret = self.redis_db.get(RedisDataHelper.get_data_key(user_id, locale))
    return ret
```
加上缓存的装饰器后，5秒内如果调用的入参经过RedisDataHelper.get_data_key产生了已经缓存过的key，则在有效期5秒内会优先返回缓存的结果。

### 延伸
Python3.2开始，`functools`模块内置了`lru_cache`装饰器，参考[文档](https://docs.python.org/3.6/library/functools.html#functools.lru_cache)。
这个装饰器会自动把函数的入参当做缓存的key来使用，并且按照最近访问的原则控制缓存的大小。
下面是官方的一个例子，用一个无限大的缓存空间来实现fibonacci数的动态规划算法：
```
@lru_cache(maxsize=None)
def fib(n):
    if n < 2:
        return n
    return fib(n-1) + fib(n-2)
```
有兴趣的话可以看看[源代码](https://github.com/python/cpython/blob/3.6/Lib/functools.py)里`lru_cache`装饰器的实现，大致的思路差不多，增加了lru策略以及锁相关的实现。
