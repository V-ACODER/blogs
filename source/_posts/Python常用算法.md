---
title: Python常用算法
date: 2020-01-01 08:49:50
tags: Python
categories: 算法
---

#### 斐波那切数列
##### 1.递归实现
```
def fibFunc(n):
  if n == 1 or n == 2:
    return 1
  return fibFunc(n-1) + fibFunc(n-2)

def inputFib(n):
  arr = []
  for i in range(n):
    arr.append(fibFunc(i+1)) 
  return arr

nterms = int(input("please input a number: "))
if nterms <= 0:
  print("input error")
else:
  print(inputFib(nterms))
```

##### 2.最简实现

```

def fibFunc(n):
  a = 0
  b = 1
  arr = []
  for i in range(n):
    arr.append(b)
    a, b = b, a+b
  return arr

nterms = int(input("please input a number: "))
if nterms <= 0:
  print("input error")
else:
  print(fibFunc(nterms))
```

#### 汉诺塔递归
```
def move(n, a, b, c):
    if n == 1:
        print a, "-->", c
    else:
        move(n - 1, a, c, b)
        print a, '-->', c
        move(n - 1, b, a, c)
move(5, 'A', 'B', 'C')
```

<!-- more -->


#### 冒泡排序
```
def bubbleFunc(arr):
  n = len(arr)
  for i in range(n):
    for j in range(i + 1, n):
      if arr[i] > arr[j]:
        arr[i], arr[j] = arr[j], arr[i]
  print(arr)  

bubbleFunc([4, 79, 23, 5, 48, 12])
```

#### 计算程序运行时间

```
import time, functools

def performance(unit):
    def log_decorator(f):
        @functools.wraps(f)
        def wrapper(*args, **kw):
            x = time.time()
            r = f(*args, **kw)
            y = time.time()
            print 'call %s() in %f%s' %(f.__name__, (y-x), unit)
            return r
        return wrapper
    return log_decorator
    

@performance('ms')
def factorial(n):
    return reduce(lambda x,y: x*y, range(1, n+1))

print factorial(10)
```