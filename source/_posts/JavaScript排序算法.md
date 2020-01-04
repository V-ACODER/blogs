---
title: JavaScript排序算法
date: 2020-01-04 07:47:20
tags: JavaScript
categories: 算法
---

#### 1. 冒泡排序两两比较，最大放后边
```
function bubbleSort(arr) {
  let temp
  for (i = 0; i < arr.length - 1; i++) {
    for (j = 0; j< arr.length - 1 - i; j++) {
      if (arr[j] > arr[j + 1]) {
        temp = arr[j]
        arr[j] = arr[j + 1]
        arr[j + 1] = temp
      }
    }
  }
  return arr
}

bubbleSort([6, 5, 4, 3, 2, 1])
```

#### 2. 快速排序找基准，左右递归
```
function quickSort(arr) {
  let len = arr.length;
  if (len <=1 ) return arr;
  let pivotIndex = Math.floor(len / 2)
  let pivot = arr.splice(pivotIndex, 1)[0]
  let left = []
  let right = []
  arr.forEach(num => {
    if (num < pivot) {
      left.push(num)
    } else {
      right.push(num)
    }
  })
  return quickSort(left).concat([pivot],quickSort(right));
  
}
let newArr = quickSort([4, 2, 9, 7, 3])
console.log(newArr)
```

<!-- more -->

#### 3. 插入排序 未排序和前面已排序比较
```
function insertSort(arr) {
  let temp
  for(let i = 1; i< arr.length; i++) {
    for(let j = i; j > 0; j--) {
      if (arr[j] >= arr[j-1]) {
        break;
      } else {
        temp = arr[j]
        arr[j] = arr[j-1]
        arr[j-1] = temp
      }
    }
  }
  return arr
}
let insertArr = insertSort([4, 2, 9, 7, 3])
console.log(insertArr)
```

#### 4. 选择排序 保存最小数下标，再交换
```
function selSort(arr) {
  let index
  let temp
  for(let i = 0; i< arr.length - 1; i++) {
    index = i
    for(let j = i + 1; j<arr.length; j ++) {
      if (arr[index] > arr[j]) index = j
    }
    if (index !== i) {
      temp = arr[index]
      arr[index] = arr[i]
      arr[i] = temp
    }
  }
  return arr
}
let selArr = insertSort([4, 2, 9, 7, 3])
console.log(selArr)
```