---
title: git 生成SSH密钥和公钥，如何关联配置github项目？
catalog: true
date: 2019-03-24 23:52:35
subtitle:
header-img: "http://po4ucl8b6.bkt.clouddn.com/headbg25.jpg"
tags:
- Hexo
catagories:
- Hexo
---
## git 生成SSH私钥和公钥，如何关联配置github项目？

> 生成ssh秘私钥和公钥，这里使用公钥添加到github上，hexo博客每次提交不用账户密码。

##### 1、根目录执行下列命令配置你的用户名
```
$ git config --global user.name "yaozhixing" 
```
#####  2、配置邮箱
```
$ git config --global user.email "yaozhixing797600@163.com" 
```
#####  3、生成密钥

```
$ ssh-keygen -t rsa -C “yaozhixing797600@163.com” 
```

#####  4、进入.ssh 隐藏文件夹

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

#####  5、github添加ssh。

- 登录github，[ 我的头像] > [ 设置 ] > [ SSH and GPG keys ] > [ 添加ssh ]添加帐号SSH Keys。
- 这里添加的是``id_rsa.pub``里面的公钥，复制粘贴在key里面，[确定]

![enter image description here](http://po4ucl8b6.bkt.clouddn.com/post01_ssh05.png)

- 输入下列命令进行验证是否成功
```
ssh -T git@github.com
```
![enter image description here](http://po4ucl8b6.bkt.clouddn.com/post01_ssh06.png)
如上图，Hi,XXX， You 're successfully authenticated .... 一大串。就说明你本地ssh 公钥和github配置成功！后面就可以一键提交！