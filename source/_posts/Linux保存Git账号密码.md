---
title: Linux保存Git账号密码
catalog: true
date: 2020-03-25 12:49:39
subtitle:
header-img: 'http://cdn.dannyee.com/headbg09.jpg'
tags:
  - linux
  - git
catagories:
  - linux
  - nginx
---

#### 1. 首先需要 ftp 连接到你的 Linux 服务器，在根目录（~/）下，使用 touch 命令创建文件 .git-credentials ：

```
touch .git-credentials
```

#### 2. 然后用 vim 命令编辑此文件：

```
vim .git-credentials
```

按 i 键进入编辑模式，输入：
http(s)://{你的用户名}:{你的密码}@你的服务器地址
注意：① 我的服务器是 http 的，所有这里不加 s 。② 去掉 {}

#### 3. 在终端下执行如下命令：

```
git config --global credential.helper store
```

#### 4. 可以看到 ~/.gitconfig 文件会多一项：

cat .gitconfig

```
[credential]
     helper = store
```

说明已经配置好了，再次 push 或 pull 试试看吧，不需要输入密码了。
