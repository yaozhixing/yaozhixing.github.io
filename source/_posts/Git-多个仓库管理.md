---
title: Git 多个仓库管理
catalog: true
date: 2020-03-25 12:54:01
subtitle:
header-img: 'http://cdn.dannyee.com/headbg11.jpg'
tags:
  - git
catagories:
  - git
---

## Git 多个仓库管理

> 现在代码托管的网站很多（比如 github，gitee 等），又不想一个一个分别为代码托管手动都建立一个项目。这时候这个就迎刃而解了，一个项目多个仓库，保存，提交，推送等等，一键搞定！

#### 1. 查看现有的远程仓库有多少个

```
git remote -v
```

#### 2. 添加新仓库地址

```
git remote add github https://github.com/yaozhixing/vdouban.git
```

这里成功添加了一个新仓库到工程中，注意这里的 **github** 是远程仓库的 ID，大家可以随便取，只要不重复就可以了。

#### 3. 拉取

```
git pull github master
git add .
git commit -m "init program"
```

#### 4. 提交远仓

```
git push github master
```

PS: 如果提交不上去。 请用强制推送命令： **git push -u gitHub master -f**
