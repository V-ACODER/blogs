---
title: Hexo+Next搭建博客过程中遇到的问题
date: 2019-8-30 14:48:44
tags: 开发工具
categories: 开发工具
---

#### 1. Next7.6版本无法显示背景动画
查看控制台，显示canvas-nest文件加载失败，需要手动下载此文件到next/source/lib里
```
cd themes/next
git clone https://github.com/theme-next/theme-next-canvas-nest source/lib/canvas-nest
```

#### 2. 修改Next后无法提交主题到自己的github上
删除next和canvas-nest隐藏的git文件再提交
> 如果是mac电脑，可用“shift+command+>”显示或不显示隐藏文件

#### 3. Next主题配置问题
* 显示中文，要将外部_config.yml中的language设置为zh-CN
* scheme配置主题
* avatar配置头像
* motion和canvas_nest配置背景动画
* post_meta修改“发表于”、“更新于”