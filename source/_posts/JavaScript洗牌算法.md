---
title: JavaScript排序算法
date: 2020-01-04 08:34:20
tags: JavaScript
categories: 算法
---
#### 洗牌算法

假设有54张扑克牌，按顺序叠放，洗牌之后变成乱序，每张牌的位置随机概率是相同的。
抽象成数组乱序排序，用Math.random生成随机数，使用Fisher–Yates Shuffle的算法，复杂度为O(n)。
这个算法的思想是，数组从后向前遍历，与之前任意元素交换。
使用JavaScript代码实现如下：

```
function shuffle(arr) {
  let len = arr.length
  let temp
  for(let i = len-1; i>=0; i--) {
    let index = Math.floor(Math.random() * len);
    temp = arr[i]
    arr[i] = arr[index]
    arr[index] = temp
  }
  return arr
}

let arr = []
for(i = 0; i< 54; i++) {
  arr.push(i + 1)
}
shuffle(arr)
```