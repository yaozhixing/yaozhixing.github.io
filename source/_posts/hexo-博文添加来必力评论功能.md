---
title: '[hexo] 博文添加来必力评论功能'
catalog: true
date: 2019-03-25 00:51:57
subtitle:
header-img:
tags:
- Hexo
catagories:
- Hexo
---

## [hexo] 博文添加来必力评论功能

> hexo，博文写好了，但是没有互动评论功能，这岂不是很不快乐的一件事。所以为每篇博文是很有必要的。

- HyperComments：https://www.hypercomments.com （来自俄罗斯的评论系统，使用谷歌账号注册。可以访问，不会用，好气，，）

- 来必力：https://livere.com （来自韩国，使用邮箱注册。）

- 畅言： http://changyan.kuaizhan.com （安装需要备案号。不太好用。）

- Gitment： https://github.com/imsun/gitment （有点小bug，比如说每次需要手动初始化，登录时会跳到主页。。）

- Valine: https://github.com/xCss/Valine (基于Leancloud的极简风评论系统，用了下，没效果，是我Next主题的原因还是？）

综上，最终采用了来必力。

### 注册账号
[来必力](https://livere.com)：  
注册（有可能注册上面要花费点功夫）。

### 安装
- 选择免费的city版本。
- 复制其中的uid字段。

### 安装在hexo上
根目录 ``_config.yml`` 添加代码如下，把uid放进去：
```
livere_uid:  xxxxx
```
### 重启运行
hexo s ，重新运行看下效果，有一个小人跑来跑去加载完成后就会出来。至此，大功告成。