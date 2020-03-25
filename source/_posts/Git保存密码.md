---
title: Git保存密码
catalog: true
date: 2020-03-25 12:52:25
subtitle:
header-img: 'http://cdn.dannyee.com/headbg10.jpg'
tags:
  - git
catagories:
  - git
---

## Git 保存密码

> 一键保存，以后再也不用担心多次弹窗输入账户密码。

找到 **.git** 文件夹，**config** 文件，末尾添加这段即可：

```
[credential]
    helper = store
```
