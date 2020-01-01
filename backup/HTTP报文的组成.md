---
title: HTTP报文的组成
date: 2018-01-12 07:10:30
tags: HTTP
categories: 通信
---

> HTTP协议的主要特点：简单快速、灵活、无连接、无状态

#### 一、请求由请求行、请求头、空行和请求体组成
1. 请求行

GET | path | HTTP/1.1 
-|-|-
方法 | 路径 | 协议版本
2. 请求头
Host
Connection
Accept
Accept-encoding
Cookie
Content-Length 1.1版本才有，除分块传输编码（chunked transfer encoding）外
3. 请求体
发送的参数


#### 二、响应由响应行、响应头、空行和响应体组成
1. 响应行

HTTP/1.1 | 200 | OK
-|-|-
协议版本 | 状态码 | 状态描述
2. 响应头
Server
Date
Content-Type
Transfer-Encoding
Connection
Expires
Cache-Control
Set-Cookie
Access-Control-Allow-Origin
Access-Control-Allow-Credentials

3. 响应体
服务器返回的内容

#### 三、具体方法
- GET（SELECT）：从服务器取出资源（一项或多项）。
- POST（CREATE）：在服务器新建一个资源。
- PUT（UPDATE）：在服务器更新资源（客户端提供改变后的完整资源）。
- PATCH（UPDATE）：在服务器更新资源（客户端提供改变的属性）。
- DELETE（DELETE）：从服务器删除资源。
- HEAD：获取资源的元数据。
- OPTIONS：获取信息，关于资源的哪些属性是客户端可以改变的。

---
参考链接：
- [RESTful API 设计指南](http://www.ruanyifeng.com/blog/2014/05/restful_api.html)

