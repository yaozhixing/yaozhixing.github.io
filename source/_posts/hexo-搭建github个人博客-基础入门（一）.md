---
title: '[hexo] 搭建github个人博客 基础入门（一）'
catalog: true
date: 2019-03-19 01:06:33
subtitle:
header-img: "http://po4ucl8b6.bkt.clouddn.com/headbg10.jpg"
tags:
- Hexo
catagories:
- Hexo
---
## [hexo] 搭建github个人博客 基础入门（一）
Hexo是一个快速、简洁且高效的博客框架。Hexo使用Markdown解析文章，在几秒内，即可利用靓丽的主题生成静态网页。本文介绍如何在Mac以及Windows上搭建Hexo，Linux用户也可以参考。综合官网教程以及自己在安装过程中的踩坑经历写下了教程，一步一步来就可以排忧解难了。
官网地址：[https://hexo.io/zh-cn/](https://hexo.io/zh-cn/)

使用Hexo搭建的个人博客网站：
本人博客地址：[https://yaozhixing.github.io/](https://yaozhixing.github.io/)
<!--more-->
## 安装Hexo
#### 1. 安装Nodejs。
[node.js](https://link.jianshu.com?t=https://nodejs.org/en/)下载地址 此步骤省略，请查看官网安装nodejs
##### 2. 更改npm源

```
$ npm config set registry https://registry.npm.taobao.org npm info underscore
```
原因是：国外的NPM源并不稳定，即使翻墙也不一定能将Hexo下载下来，所以这里直接更改为淘宝源镜像。
#### 3. 安装hexo
```
$ npm install -g hexo-cli
```
这里安装的是hexo最新版本，如果想安装以前的的版本请运行命令$ npm install -g hexo<br>

以上步骤不出问题的话就已经在本地机器上搭建起了Hexo环境。下面介绍Hexo的具体使用方法。

## Quick Start
#### 1、创建hexo工程

```
$ hexo init yaozhixing.github.io
$ cd aozhixing.github.io
$ npm install
```
创建一个文件夹[yaozhixing.github.io](https://yaozhixing.github.io/),必须是用 账户名+.github.io 组成。为什么取一个这个长的名字？本人装了2-3遍hexo d命令提交不成功，都是因为这个问题。<br>
因为后面，我们在github会创建一个项目就叫做: yaozhixing.github.io，对，没错，xxxx.github.io，这个xxxx就是你的github账户名（昵称，不是邮箱名），一旦这个项目生成，github就会Settings的GitHub Pages自动生成一个二级域名，地址就是：xxxx.github.io，特别注意！
新建完成后，指定文件夹的目录如下：

```
yaozhixing.github.io
├── _config.yml
├── package.json
├── scaffolds
├── source
|   └── _posts
└── themes
|   └── landscape
```
好了，一个hexo的项目yaozhixing.github.io已经建立好了，辣么我们该怎么跑起来了呢？下面来啦…

#### 2、生成静态文件
hexo generate  也可缩写成：**hexo g**

```
$ hexo g
```
他的作用是什么？为什么要生成静态文件。原因就是：简单点就是将Markdown文件解析成HTML文件，放在yaozhixing.github.io/public目录下。

#### 3、运行hexo服务器
命令行输入：hexo server   也可缩写成：**hexo s**

```
$ hexo s
```
来，让我们跑起来吧~~，它不会自动弹出浏览器打开，需要我们手动打开。所以浏览器输入：http://localhost:4000/ <br>

好了，简单的博客我们搭建好了，那我们怎么上传到git服务器上呢？继续！！

## 申请github免费静态内容空间
#### 1、请先在github官网注册账号然后才可以新建项目，创建一个叫“yaozhixing.github.io”的项目。如图：
![创建一个叫yaozhixing.github.io的项目](http://po4ucl8b6.bkt.clouddn.com/post01_01.png)

##### 2、复制项目的ssh链接，这里我们用ssh链接做。（因为https链接地址hexo后面可能会报错）如图：
![ssh链接](http://po4ucl8b6.bkt.clouddn.com/post01_02.png)

#### 3、安装deployer-git（勿忘）

```
$ npm install hexo-deployer-git --save
```
#### 4、在/yaozhixing.github.io/_config.yml中修改deploy属性(注意冒号:后面有个空格，),把刚才ssh地址放在repository后面

```
deploy:
  type: git
  repository: git@github.com:yaozhixing/yaozhixing.github.io.git
  branch: master
  message: init blog
```

#### 5、生成SSH密钥过程（每次提交不用输入账号密码）。
这里单独有一篇 [生成SSH密钥和公钥，如何关联配置github项目？](https://yaozhixing.github.io/article/git-生成SSH密钥和公钥，如何关联配置github项目？/)，可以另开窗口看，或者继续往下看也可以，步骤如下：

- 根目录执行下列命令配置你的用户名
```
$ git config --global user.name "yaozhixing" 
```

- 配置邮箱
```
$ git config --global user.email "yaozhixing797600@163.com" 
```

- 生成密钥

```
$ ssh-keygen -t rsa -C “yaozhixing797600@163.com” 
```

- 进入.ssh 隐藏文件夹

```
cd  ~/.ssh
```
![enter image description here](http://po4ucl8b6.bkt.clouddn.com/post01_ssh01.png)
- 连续三个回车，生成密钥，最后得到了两个文件：id_rsa和id_rsa.pub
```
ssh-keygen -t rsa -C "yaozhixing797600@163.com"
```
![enter image description here](http://po4ucl8b6.bkt.clouddn.com/post01_ssh02.png)
生成文件默认路径
![enter image description here](http://po4ucl8b6.bkt.clouddn.com/post01_ssh02_01.png)

- 输入eval "$(ssh-agent -s)"，添加密钥到ssh-agent
```
eval "$(ssh-agent -s)"
```
结果会像这样：
![enter image description here](http://po4ucl8b6.bkt.clouddn.com/post01_ssh03.png)

- 再次输入命令
```
ssh-add ~/.ssh/id_rsa
```
![enter image description here](http://po4ucl8b6.bkt.clouddn.com/post01_ssh04.png)

#### 6、github添加ssh。
- 登录github，[ 我的头像] > [ 设置 ] > [ SSH and GPG keys ] > [ 添加ssh ]添加帐号SSH Keys
![enter image description here](http://po4ucl8b6.bkt.clouddn.com/post01_ssh05.png)

- 输入下列命令进行验证是否成功
```
ssh -T git@github.com
```
![enter image description here](http://po4ucl8b6.bkt.clouddn.com/post01_ssh06.png)
如上图，Hi,XXX， You 've successfully authenticated .... 一大串。就说明你本地ssh 公钥和github配置成功！后面就可以一键提交！

#### 7、代码生成，服务器提交。

- 先清除 hexo clean
- 然后生成 hexo generate ， 也可缩写：hexo g
- 再在发布 hexo deploy ，也可缩写成： hexo d

```
$ hexo clean
$ hexo g
$ hexo d
```

nice，到这里初步的博客就完成了，步骤有点多，不过简单，稍微耐心一点，就可以完成的，不过还有遗留问题没有解决，不过是下几篇博文的内容，如何源代码和生产的静态代码同时提交？怎么更换主题？博文怎么评论？。


----------

> 其他文章列表，如下：

#### [hexo] hexo-theme-Danny 更换主题 基础入门（二）
#### hexo源代码和生产代码同时保存在同一个项目里且提交？
#### git如何生成秘钥？
#### hexo博文添加评论功能？