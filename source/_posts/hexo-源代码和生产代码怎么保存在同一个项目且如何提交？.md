---
title: '[hexo] hexo-源代码和生产代码怎么保存在同一个项目且如何提交？'
catalog: true
date: 2019-03-24 22:00:23
subtitle:
header-img: "http://po4ucl8b6.bkt.clouddn.com/headbg41.jpg"
tags:
- Hexo
catagories:
- Hexo
---

## [hexo] hexo-源代码和生产代码怎么保存在同一个项目且如何提交？


>源代码只能保存在本地电脑上，如果本地电脑上源代码一旦丢失，或者你想要在公司（别的电脑）电脑上写点博文，那么我们的博客就不能多台电脑同步而且会面临随时嗝屁的风险，删掉了再也找不到源代码了，这是多么可怕的一件事啊？作为程序员这是绝对不可容忍的。

### 原因
博客源代码 hexo d 提交后，目录中会自动创建一个文件夹.deploy_git。
里面是我们的生产代码。``那是因为源代码和生产代码在同一个分支，生产代码会把源代码覆盖导致的。``，问题出在这里。

```
deploy:
  type: git
  repository: git@github.com:yaozhixing/yaozhixing.github.io.git
  branch: master
  message: hexo init
```
我们把源代码默认保存在master上，然后deploy保存也放在master分支上，当然已提交会覆盖源代码，所以会出现这个问题！

### 解决方法
- ``推荐方法``  我用的是这个方法
**把源代码放在开发分支下，如创建一个分支名: develop，把源代码全部放在develop上，hexo g 提交代码自动发布在master上**，自然解决了这个问题！

- 把deploy里的branch放在另一个分支，比如 githubPage上，然后在github的 项目[设置]里，设置默认分支为 githubPage， ok！

### 总结
这两种方法都可以，推荐使用第一种方法。都是使用github的分支功能分别保存两个代码，方便简洁高效！