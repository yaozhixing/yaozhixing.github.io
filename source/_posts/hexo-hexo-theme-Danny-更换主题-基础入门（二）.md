---
title: '[hexo] hexo-theme-Danny 更换主题 基础入门（二）'
catalog: true
date: 2019-03-24 14:40:05
subtitle:
header-img: "http://po4ucl8b6.bkt.clouddn.com/headbg29.jpg"
tags:
---
## [hexo] hexo-theme-Danny 更换主题 基础入门（二）

>这个由Danny创作的Danny主题，是从原来的 [HuWeihuang](https://www.huweihuang.com/)和 [YenYuHsuan](http://beantech.org/) 改编而来的。

### Demo

Danny Blog : [https://yaozhixing.github.io/](https://yaozhixing.github.io/)

首页截图↓：
![enter image description here](http://po4ucl8b6.bkt.clouddn.com/post02_01.png)

归档↓：
![enter image description here](http://po4ucl8b6.bkt.clouddn.com/post02_02.png)

Tags标签↓：
![enter image description here](http://po4ucl8b6.bkt.clouddn.com/post02_03.png)

关于我↓：
![enter image description here](http://po4ucl8b6.bkt.clouddn.com/post02_04.png)

博文示例↓：
![enter image description here](http://po4ucl8b6.bkt.clouddn.com/post02_05.png)

----------


### Install Hexo
首先必须安装 Node.js 和Git 工具，这里就不在详细出教程了。

安装 hexo
```
npm install hexo-cli -g
```
### 使用方法
```
git clone https://github.com/yaozhixing/hexo-theme-Danny.git
cd hexo-Theme-Danny
npm install
```


----------


### 修改配置
修改  ``_config.yml`` 文件，配置自己需要的文件信息。
修改配置信息文件如下：

##### 1、站点配置信息
```
# Site
title: Danny Blog
subtitle: 每天多努力一点，进步就多一点
author: Danny
language:
timezone:

url: https://yaozhixing.github.io/       
root: /
#permalink: :year/:month/:day/:title/
permalink: :category/:title/
permalink_defaults:
  lang: en
```
这里还有其他文件配置信息，可根据自己需求设置：
header-img:  首页banner图片地址
article-img: 文章背景图片
404-img:  404 图片地址
signature: false #show signature
signature-img: img/signature/BeanTechSign-white.png
theme: 采用什么博客主题，文件夹名称

##### 2、Deployment选项
``很重要`` ``很重要`` ``很重要``, 请正确配置，如果不会，请看上一节 [ [hexo]搭建github个人博客 基础入门（一）](https://yaozhixing.github.io/article/hexo-%E6%90%AD%E5%BB%BAgithub%E4%B8%AA%E4%BA%BA%E5%8D%9A%E5%AE%A2-%E5%9F%BA%E7%A1%80%E5%85%A5%E9%97%A8%EF%BC%88%E4%B8%80%EF%BC%89/)
```
deploy:
  type: git
  repository: git@github.com:yaozhixing/yaozhixing.github.io.git
  branch: master
  message: hexo init
```
type：提交方式采用git
repository： 远程仓库的https地址和ssh的地址，我这里采用ssh地址，可根据上一节教程配置本地公钥，在github的添加公钥上去，就可以一件提交
branch： 远程地址提交的分支
message： 每次提交的提交说明

##### 3、侧边栏设置
sidebar: 是否显示侧边栏；
sidebar-about-description: 描述
sidebar-avatar: 头像
```
sidebar: true    
sidebar-about-description: "<your description>"
sidebar-avatar: img/<your avatar path>
```

##### 4、开启评论插件
本博客为例，采用来必力社区评论，请先去[来必力](https://www.livere.com/)申请账号，获取账号复制到这里
```
livere_uid:  xxxxx
```

#### 5、返回顶部图标设置
我的图片是钢铁侠，可以在css/image上更改为你自己的图片。


----------


### Post tag
设置博文是否显示post标签。
```
home_posts_tag: true
```


----------


### Hexo Basics
hexo 语法命令，如下：
- 新建博文： hexo new post  "xxx"
- 清空静态缓存文件： hexo clean 
- 生成静态文件： hexo generate （简写： hexo g）
- 启动本地服务器： hexo server （简写：hexo s）
- 提交服务： hexo deploy （简写：hexo d）


----------
### 赞一个

<!-- Place this tag in your head or just before your close body tag. -->
<script async defer src="https://buttons.github.io/buttons.js"></script>
<!-- Place this tag where you want the button to render. -->

如果您喜欢这篇hexo主题，就请赞一个 <a class="github-button" href="https://github.com/yaozhixing/yaozhixing.github.io" data-icon="octicon-star" aria-label="Star yaozhixing/yaozhixing.github.io on GitHub">Star</a> 小星星！  可以关注我的github账户，来吧，一起相互学习吧~<a class="github-button" href="https://github.com/yaozhixing" aria-label="Follow @yaozhixing on GitHub">Follow</a> 
