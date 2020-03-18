---
title: cmd远程连接服务器
catalog: true
date: 2020-03-18 09:27:14
subtitle:
header-img: 'http://cdn.dannyee.com/headbg07.jpg'
tags:
  - linux
  - cmd
catagories:
  - linux
---

## cmd 远程连接服务器

> 可直接 cmd 或 git bash 命令连接远程服务器，进行文件传输增删改查，步骤如下：

1. ssh 用户名@服务器地址

```
ssh root@192.168.0.110
```

2. 输入密码
3. 进入目录 /data/www/saas-fe/h5
4. 远程删除目录

```
   rm -rf /data/www/saas-fe/h5/business-card
```

4. 把本地打包后的文件夹 => 复制到 => 远程指定文件夹里。

```
   scp -r business-card/ root@192.168.0.110:/data/www/saas-fe/h5/
```
