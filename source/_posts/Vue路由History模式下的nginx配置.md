---
title: Vue路由History模式下的nginx配置
catalog: true
date: 2020-03-18 09:13:06
subtitle:
header-img: 'http://cdn.dannyee.com/headbg06.jpg'
tags:
  - vue
  - nginx
  - 路由
catagories:
  - vue
  - nginx
---

#### Vue 路由 History 模式下的 nginx 配置

> 使用 history 模式，使项目地址 URL 更加友好。

##### 1、 URL 示例 1：http://www.mydomain.com/Home

要进行配置的 `Vue-router` 关联项为：

```
const router = new VueRouter({
    base: './',
    mode: 'history',
    routes: routes
  });
```

`nginx` 相关配置：

```
server {
    listen 80;
    location ~ .*\.(htm|html)$ {
        add_header Cache-Control no-store;
    }
    index index.html;
    root /opt/www/vue-project;
    try_files $uri $uri/ /index.html;
  }
```

##### 2、URL 示例 http://www.mydomain.com/project/Home

若发布的项目是基于域名指定路径下，则在== Vue-router== 须配置 base 为指定路径

```
const router = new VueRouter({
    base: '/project/',
    mode: 'history',
    routes: routes
  });
```

`vue.config.js` (仅针对使用 vue-cli 3.0 以上版本需要配置)

> baseUrl 已废弃，改用 publicPath

```
module.exports = {
  // 基本路径
  publicPath: '/project/',
  ...
}
```

`nginx` 配置：

```
server {
    listen 80;
    location /project {
      location ~ .*\.(htm|html)$ {
        add_header Cache-Control no-store;
      }
      index index.html;
      alias /opt/www/project;
      try_files $uri $uri/ /project/index.html;
    }
  }
```

或者：

```
server {
    listen 80;
    location /project {
      location ~ .*\.(htm|html)$ {
        add_header Cache-Control no-store;
      }
      index index.html;
      root /opt/www/;
      try_files $uri $uri/ /project/index.html;
    }
  }
```
