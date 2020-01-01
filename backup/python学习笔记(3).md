---
title: Python学习笔记(3)
date: 2016-08-05 10:32:45
tags: Python
categories: 服务端
---

### Python常用命令
1. 启动HTTP服务
```
[nohup] python -m SimpleHTTPServer [&]
```

2. 发送邮件
```
import smtplib 
mailhost='smtp.qq.com'
qqmail = smtplib.SMTP()
qqmail.connect(mailhost,25)

account = input('请输入你的邮箱：')
password = input('请输入你的密码：')
qqmail.login(account,password)

receiver=input('请输入收件人的邮箱：')

from email.mime.text import MIMEText
from email.header import Header
content=input('请输入邮件正文：')
message = MIMEText(content, 'plain', 'utf-8')
subject = input('请输入你的邮件主题：')
message['Subject'] = Header(subject, 'utf-8')

qqmail.sendmail(sender, receiver, message.as_string())
qqmail.quit()
```


---
参考链接：
[廖雪峰的官方网站](https://www.liaoxuefeng.com/wiki/897692888725344/923057144964288)


快速排序
插入排序
选择排序