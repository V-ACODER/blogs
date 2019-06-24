---
title: 记一次Node内存泄露分析过程
date: 2019-05-16 16:24:02
tags: Node
categories: 服务端
---

## 第一次内存溢出
起因：2019年4月11日，爬虫爬公司官网404页面导致内存溢出，服务器不断重启
临时解决方案：扩大运行内存，把爬虫的网段加黑名单
![nuxt1](/images/nuxt1.png)

<!-- more -->

## 第二次内存溢出
2019年4月23日上午10点半左右，服务器每隔3小时内存溢出重启，解决内存泄露，刻不容缓
![nuxt2](/images/nuxt2.png)


## 工欲善其事，必先利其器
学习了相关知识后，发现大佬们普遍用的以下方法排查：
方案一：[heapdump](https://github.com/bnoordhuis/node-heapdump) + [memwatch-next](https://github.com/lloyd/node-memwatch#readme) + Chrome devTool
方案二：[Easy-Monitor](https://github.com/hyj1991/easy-monitor#readme)

参考教程：
* [如何记录堆快照](https://developers.google.com/web/tools/chrome-devtools/memory-problems/heap-snapshots?hl=zh-cn)
* [如何自己检查NodeJS的代码是否存在内存泄漏](https://www.w3ctech.com/topic/842)

##  一波三折
使用方案二顺利排查出泄漏点，修改提交，然而在搭起的测试服上并没见效：o(≧口≦)
![nuxt3](/images/nuxt3.png)

## 大胆猜测，小心验证
最后，只能靠猜测来排查了~~ 梳理一下后，我发现以下几个线索
线索1：空页面内存稳定，首页内存溢出 —> 首页的某个组件有问题
线索2：连接线下接口稳定，连接线上内存暴涨 —>线上数据触发
线索3：4月23日10点半左右开始—>  这个时间点改变的数据
线索4：与访问量无关的有规律溢出—>  是服务器端自己跑的任务
猜测：4月23日一个数据的变化触发了某个定时任务，首页在这个时间点的变动是配置了一个直播

验证：测试setTimeout、setInterval
结果：首页直播倒计时的setInterval没有释放

完结，撒花~