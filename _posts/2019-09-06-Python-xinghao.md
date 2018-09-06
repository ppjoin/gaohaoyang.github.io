---
layout: post
title:  "Python笔记 - 参数中的星号*和双星号**"
categories: Python笔记
tags:  Python参数
author: PPJoin
---

* content
{:toc}

# A. 单星号（\*）：\*agrs
将所有参数以元组(tuple)的形式导入：
例如：

```python
def foo(param1, *param2):
        print param1
        print param2
```
输出内容如下: 
```python
>>> foo(1,2,3,4,5)
1
(2, 3, 4, 5)
```

# B. 双星号（\*\*）：\*\*kwargs
将参数以字典的形式导入

```python
def bar(param1, **param2):
        print param1
        print param2
```
输出内容如下: 
```python
>>> bar(1,a=2,b=3)
1
{'a': 2, 'b': 3}
```