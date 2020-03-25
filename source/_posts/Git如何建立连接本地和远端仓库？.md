---
title: Git如何建立连接本地和远端仓库？
catalog: true
date: 2020-03-25 12:57:29
subtitle:
header-img: 'http://cdn.dannyee.com/headbg12.jpg'
tags:
  - git
catagories:
  - git
---

## 本地有工程，远端没有创建，如何建立连接，如何提交？

> 往往有时候是这样的，项目先行，或者脚手架工具自动创建的 web 工程名，功能都完成一个版本了，git 仓库并没有建立项目，因此我们要如何关联起来，一键提交到 git 上去。

#### 1. 在 github 上点击 【新建项目】

#### 2. 在本地创建一个【工程名】

```
mkdir <工程名>
```

#### 3. 进到文件名下

```
cd 工程名
```

#### 4. 初始化 git 仓库

```
git init
```

#### 5. 建立连接

```
git remote add origin 仓库地址（github上的）
```

#### 5. 把分支上的文件拉下来

```
git pull origin master
```

#### 6. 开发项目，写代码

#### 7. 添加

```
git add .
```

#### 8. 提交本地

```
git commit -m "init program"
```

#### 9. 推送

```
git push origin master
```

PS：如果推送失败，建议使用 强制推送：

```
git push -u origin master -f
```

## 远端有仓库，本地没有工程（最常见）

1.克隆

```
git clone 仓库地址
```
