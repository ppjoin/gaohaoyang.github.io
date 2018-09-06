---
layout: post
title:  "Python笔记 - 参数中的星号*和双星号**"
categories: Python笔记
tags:  Python参数
author: PPJoin
---

* content
{:toc}

### 单星号 \*

将所有参数以元组 tuple 的形式导入。

例如：

```python
def foo(param1, *param2):
        print param1
        print param2
```

执行：
'
>>> foo(1,2,3,4,5)
'
输出：

'
1
(2, 3, 4, 5)
'

### 双星号 \*\*

将所有参数以字典的形式导入.

例如：

```python
def bar(param1, **param2):
        print param1
        print param2
```
执行：

'
>>> bar(1,a=2,b=3)
'

输出：

'
1
{'a': 2, 'b': 3}
'