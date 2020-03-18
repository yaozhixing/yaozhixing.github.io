---
title: Nginx linux 入门配置
catalog: true
date: 2020-03-18 09:05:39
subtitle:
header-img: 'http://cdn.dannyee.com/headbg03.jpg'
tags:
  - nginx
  - linux
catagories:
  - nginx
  - linux
---

### Nginx 入门配置

> 最近项目老大，有叫我配置 linux 的 nginx，然后根据项目需求总结一下 nginx 知识；

#### 一、介绍

Nginx 是一个 web 服务器也可以用来做负载均衡及反向代理使用，目前使用最多的就是负载均衡，具体简介我就不介绍了百度一下有很多，下面直接进入安装步骤

#### 二、 官网

nginx： [http://www.nginx.org/](https://note.youdao.com/)

#### 三、Nginx 安装

##### 1、下载 Nginx 及相关组件

进入 usr/local/src/ 目录

```
[root@localhost /] cd usr/local/src/
```

```
[root@localhost src]# wget http://nginx.org/download/nginx-1.10.2.tar.gz
```

```
[root@localhost src]# wget http://www.openssl.org/source/openssl-fips-2.0.10.tar.gz
```

```
[root@localhost src]# wget http://zlib.net/zlib-1.2.11.tar.gz
```

```
[root@localhost src]# wget ftp://ftp.csx.cam.ac.uk/pub/software/programming/pcre/pcre-8.40.tar.gz
```

##### 2、安装 Nginx 及相关组件

openssl 安装

```
[root@localhost src]# tar zxvf openssl-fips-2.0.10.tar.gz
省略安装内容...

[root@localhost src]# cd openssl-fips-2.0.10
[root@localhost openssl-fips-2.0.10]# ./config && make && make install
省略安装内容...
```

pcre 安装

```
[root@localhost src]# tar zxvf pcre-8.40.tar.gz
省略安装内容...
[root@localhost src]# cd pcre-8.40
[root@localhost pcre-8.40]# ./configure && make && make install
省略安装内容...
```

zlib 安装

```
[root@localhost src]# tar zxvf zlib-1.2.11.tar.gz
省略安装内容...
[root@localhost src]# cd zlib-1.2.11
[root@localhost zlib-1.2.11]# ./configure && make && make install
省略安装内容...
```

nginx 安装

```
[root@localhost src]# tar zxvf nginx-1.10.2.tar.gz
省略安装内容...
[root@localhost src]# cd nginx-1.10.2
[root@localhost nginx-1.10.2]# ./configure && make && make install
省略安装内容...
```

##### 3、启动 nginx

进入 nginx 安装目录

```
[root@localhost /] cd usr/local/nginx/
[root@localhost nginx]
```

启动 nginx 命令[记住][记住][记住]

```
[root@localhost nginx] /usr/local/nginx/sbin/nginx
```

ok，完成
进入 Linux 系统的图形界面，打开浏览器输入 localhost，说明 nginx 启动成功

---

#### 四、nginx 的基本操作

##### 1、基础命令

```
启动
[root@localhost ~]# /usr/local/nginx/sbin/nginx

停止/重启
[root@localhost ~]# /usr/local/nginx/sbin/nginx -s stop(quit、reload)

命令帮助
[root@localhost ~]# /usr/local/nginx/sbin/nginx -h

验证配置文件
[root@localhost ~]# /usr/local/nginx/sbin/nginx -t

配置文件
[root@localhost ~]# vim /usr/local/nginx/conf/nginx.conf
```

##### 2、如何知道 nginx 安装位置？

```
[root@localhost ~]# ps -nux | grep nginx
```

##### 3、vim 简单语法

```
默认vim打开后是不能录入的，需要按键才能操作，具体如下：
开启编辑：按“i”或者“Insert”键
退出编辑：“Esc”键
退出vim：“:q”
保存vim：“:w”
保存退出vim：“:wq”
不保存退出vim：“:q!”
```
