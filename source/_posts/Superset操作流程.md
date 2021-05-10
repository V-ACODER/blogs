---
title: Superset操作流程
date: 2021-05-10 13:34:30
tags: Superset
categories: 前端
---

### 前言
> Superset是Apache开源的现代化企业级BI应用程序，开发语言为Python/React，有多种搭建环境方式，跟随官方文档使用Docker镜像可轻松搭建部署。

### 优势
* 图表类型目前有40余中，折线图、柱状图、扇形图、地理图等基本满足使用要求。
* 支持csv/excel导入数据，支持数据、效果图下载。
* 自定义Dashboard拖拽排版交互体验很好。
* 数据库、数据集、图表、dashboard、用户各个模块管理清晰。
* 支持在线SQL查询。
* 支持多种数据库连接。

### 不足
* 文档不完善，制作图表参数配置上手难。
* 某些地方功能不完善，例如数据库数据更新后，图表没有联动更新。
* 没有文件夹管理。
* 对开发环境要求较高。

### 操作流程
1. 登录
![登录](/images/superset/login.png)

2. Home
![Home](/images/superset/home.png)

3. 连接数据库
![database](/images/superset/database.png)
![db2](/images/superset/db2.png)
![db3](/images/superset/db3.png)

<!-- more -->

4. 连接数据库中已存在表格或者上传数据
![ds1](/images/superset/ds1.png)
![ds2](/images/superset/ds2.png)

5. 创建图表（点击数据集进入，或者点击按钮 +CHART 新建）
##### 选择数据集
![chart1](/images/superset/chart1.png)

##### 选择图表类型
![chart2](/images/superset/chart2.png)

##### 配置图表，运行查看效果，保存时可指定Dashboard
![chart4](/images/superset/chart4.png)

6. 配置Dashboard
##### 新建Dashboard
![dashboard1](/images/superset/dashboard1.png)

##### 将新建的图表拖拽到指定区域
![dashboard2](/images/superset/dashboard2.png)

##### 保存预览，可导出或分享
![dashboard3](/images/superset/dashboard3.png)

### 自定义配置
使用superset_config.py可更改配置，例如：

* 连接数据库 SQLALCHEMY_DATABASE_URI
* 切换语言 BABEL_DEFAULT_LOCALE
* 更改public角色权限用于免登录 PUBLIC_ROLE_LIKE = 'Gamma'
* 跨域设置 HTTP_HEADERS = {}, WTF_CSRF_ENABLED = False