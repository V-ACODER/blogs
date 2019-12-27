---
title: HTTP协议各版本的对比变化
date: 2018-01-10 10:20:40
tags: HTTP
categories: 通信
---


> HTTP是基于TCP/IP协议的应用层协议。它不涉及数据包（packet）传输，主要规定了客户端和服务器之间的通信格式，默认使用80端口。

版本 | 出版时间 | 方法 | 响应内容 | 新增功能
-|-|-|-|-
HTTP/0.9 | 1991    | GET | 字符串 | 服务器只能回应HTML格式的字符串，发送完毕，就关闭TCP连接
HTTP/1.0 | 1996.05 | + POST、HEAD | + 图像、视频、二进制文件 | 状态码（status code）、多字符集支持、多部分发送（multi-part type）、权限（authorization）、缓存（cache）、内容编码（content encoding）
HTTP/1.1 | 1997.01 | + PUT、PATCH、HEAD、 OPTIONS、DELETE | + 头部Host | + 持久连接（persistent connection、管道机制（pipelining）
HTTP/2   | 2015    | + | 头信息和数据体都是二进制 | 双向的、实时的多工（Multiplexing）通信、头信息压缩、服务器推送（server push） 

注释：
- +号表示包含上个版本的内容
- 1.0版本非标准声明Connection: keep-alive支持持久连接，1.1版本不用声明，关闭连接时发送Connection: close
- 对于同一个域名，大多数浏览器允许同时建立6个持久连接
- 管道机制，即在同一个TCP连接里面，客户端可以同时发送多个请求
- HTTP/2只有在 HTTPS 环境才会生效
- HTTPS在HTTP的基础下加入SSL层

<!-- more -->

---
参考链接：
[HTTP 协议入门](http://www.ruanyifeng.com/blog/2016/08/http.html)