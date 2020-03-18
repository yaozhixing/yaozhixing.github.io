---
title: nginx window 命令
catalog: true
date: 2020-03-17 19:38:20
subtitle:
header-img: 'http://cdn.dannyee.com/headbg02.jpg'
tags:
  - nginx
catagories:
  - nginx
---

Windows 下 Nginx 的启动、停止等命令

在 Windows 下使用 Nginx，我们需要掌握一些基本的操作命令，比如：启动、停止 Nginx 服务，重新载入 Nginx 等，下面我就进行一些简单的介绍。

#### 1、启动：

```
start nginx
或
nginx
```

注：建议使用第一种，第二种会使你的 cmd 窗口一直处于执行中，不能进行其他命令操作

#### 2、停止：

```
nginx -s stop
或
nginx -s quit
```

注：stop 是快速停止 nginx，可能并不保存相关信息；quit 是完整有序的停止 nginx，并保存相关信息

#### 3、重新载入 Nginx：

```
nginx -s reload
```

当配置信息修改，需要重新载入这些配置时使用此命令。

#### 4、重新打开日志文件：

```
nginx -s reopen
```

#### 5、查看 Nginx 版本：

```
nginx -v
```
