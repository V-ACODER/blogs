---
title: JS中双等号隐式类型转换规则
date: 2020-01-08 06:51:30
tags: JavaScript
categories: 前端
---

> JS中的类型Number、String、Boolean、Object，这些类型在用双等号做比较时会发生隐式类型转换。规则如下：

1. 如果双等号左右有NaN，结果一律为false。其他数值直接对比。
2. 如果有布尔值，将false转为0，true转为1，再作比较。
3. 如果两边都是字符串，直接对比。如果一边字符串，先把字符串转为数字再对比。
4. 如果是复杂数据类型Object，先调用valueOf()，假如valueOf()不是数值，再调用toString进行转换。