---
title: Nginx配置 config文件中root和alias的区别
catalog: true
date: 2020-03-18 09:09:27
subtitle:
header-img: 'http://cdn.dannyee.com/headbg05.jpg'
tags:
  - nginx
  - linux
catagories:
  - nginx
  - linux
---

#### Nginx 配置 config 文件中 root 和 alias 的区别

> 最近前端的组长叫我配置 linux 下 nginx 项目的时候，在有说到 nginx 的虚拟目录的时候，配到了 root 和 alias 配置的区别问题，做个总结。

##### 如果域名是：http://blog.dannyee.com

#### 1、root 配置

```
location /index/ {
       root /home/www/;
}
```

#### 2、alias 配置

```
location /project/ {
      alias /home/www/;
}
```

#### 3、区别

- root 属性指定的值是要加入到最终路径的，所以访问的位置变成了 **http://blog.dannyee.com/project/1.html** 实际指向的是 **/home/www/project** 下的
- alias 属性其会抛弃 URI，直接访问 alias 指定的位置, 所以最终路径变成 **http://blog.dannyee.com/index/1.html** 实际指向的是 **/home/www/**

#### 4、总结

- root 属性，指定的值是要加入到最终路径的 /home/www/index/ ,他会带上 location 斜杠后面的 index，组成的新的最终路径。
- alias 属性，其会抛弃 URI，直接访问 alias 指定的位置, 所以最终路径变成 /home/www/
