---
title: HTTP缓存
date: 2018-01-13 14:20:30
tags: HTTP
categories: 通信
---

> 常见的http缓存只能缓存get请求响应的资源，根据是否需要重新向服务器发起请求来分类，可分为强缓存和协商缓存。

![总图](/images/http/z.jpg)

#### 1. 强缓存
如果Cache-Control的max-age没有过期或者Expires的缓存时间没有过期，就直接使用浏览器的缓存数据
![强缓存](/images/http/q.jpg)

#### 2. 协商缓存
如果不用强缓存，浏览器第二次请求时就会与服务器进行协商，如果服务器端的资源没有修改，那么就会返回304状态码
![协商缓存](/images/http/x.jpg)

---
参考链接：
[一文读懂http缓存（超详细）](https://www.jianshu.com/p/227cee9c8d15)