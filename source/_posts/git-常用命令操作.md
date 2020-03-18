---
title: git 常用命令操作
catalog: true
date: 2020-03-17 19:21:02
subtitle:
header-img: 'http://cdn.dannyee.com/headbg01.jpg'
tags:
  - Git
catagories:
  - Git
---

#### 常用命令

```
git add .                       添加
git commit -m '备注信息'        提交信息
git stash                       暂存
git stash pop                   取出暂存
git pull --rebase               拉取远程
git push                        提交


git branch                      查看所有的分支
git checkout <BranchName>       切换分支


git rebase --continue           处理冲突后继续操作
git rebase –abort               放弃一次合并
```

#### 1、删除本地分支：

```
git branch -d <BranchName>
```

#### 2、拉取远程分支并穿件本地分支

```
1. git fetch
2. git branch -r
3. git checkout -b <BranchName> origin/<BranchName>
```

#### 3、查看提交记录

```
git log
git reflog
```

#### 4、查看某某提交记录

```
git log --author=username
```

#### 5、“挑拣”提交：cherry-pick

```
1. git reflog 查找到要检索的id，复制下来id；
2. git cherry-pick <commit id>；
3. 顺利完成会提示：Finished one cherry-pick.  冲突要手动解决冲突；
4. git push (重要，重要，重要)；
```

参考：
[https://blog.csdn.net/fightfightfight/article/details/81039050](https://blog.csdn.net/fightfightfight/article/details/81039050)

#### 6、冲突解决：

```
1. 手动解决冲突后
2. git add .
3. git rebase --continue      处理冲突后继续操作
4. git push
```

#### 7、合并分支

```
1. git checkout agent
2. git rebase dev               可以将dev分支合并到当前分支
3. 看是否有冲突文件，有就解决冲突，没有就 git push
4. 有冲突解决后，git add .      标记冲突已解决
5. git rebase --continue        继续，还有冲突继续解决
6. git push
```

#### 8、回退的 3 中处理方式

##### 1. 未 add，未提交；

```
git checkout -- a.txt    丢弃某个文件，或者
git checkout -- .        丢弃全部
```

##### 2、已 add，未提交

```
git reset HEAD .  或者
git reset HEAD a.txt
```

##### 3、已 add， 已提交，未 push

```
1. git log # 得到你需要回退一次提交的commit id

2. git reset --hard <commit_id>  # 回到其中你想要的某个版
或者
git reset --hard HEAD^  # 回到最新的一次提交
或者
git reset HEAD^  # 此时代码保留，回到 git add 之前

3. git reset HEAD~ --soft 远程拉回本地记录，远程记录删除，本地保留远程记录
```

## windows 删除文件，超快的。

```
cnpm install rimraf -g
rimraf node_modules
```

### 清除 npm 缓存文件

```
npm cache clean --force

npm i

npm config set registry " https://registry.npm.taobao.org "

npm config set disturl https://npm.taobao.org/dist
```
