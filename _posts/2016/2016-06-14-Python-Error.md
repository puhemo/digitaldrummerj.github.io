---
title: "Python Error"
date: 2016-06-14
modified: 2016-06-14
published: true
categories:
  - Python
tags:
  - Python
  - Error
excerpt: |
    A Collection of some python errors for search
---

A collection of some python errors for search

## SyntaxError

###  SyntaxError: non-ascii character ' xe6' in file
中文注释乱码问题  

```python
代码开始的第一行添加如下一条语句：
# This Python file uses the following encoding: utf-8

或添加语句为：
# encoding: utf-8
```
