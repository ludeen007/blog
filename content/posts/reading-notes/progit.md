---
title: "《精通Git/Pro Git》 2e读书笔记"
date: 2019-12-11T18:42:55+08:00
draft: false
categories: ["读书笔记"]
tags: ["读书笔记", "Git", "Productive"]
---

## Git直接记录快照，而非差异比较

![alt image text](/progit/6.png)
Figure 6. 工作目录、暂存区域以及 Git 仓库

文件的3种状态：

1. 已修改modified
2. 已暂存staged
3. 已提交committed

## 基本的 Git 工作流程如下

1. 在工作目录中修改文件。
2. 暂存文件，将文件的快照放入暂存区域。
3. 提交更新，找到暂存区域的文件，将快照永久性存储到 Git 仓库目录

![alt image text](/progit/8.png)
Figure 8. 文件的状态变化周期

## 工作目录下的文件的2种状态：已跟踪tracked，未跟踪untracked

```bash
#查看提交2个历史及其文件修改
git log -p -2
#查看分支历史图
git log --graph
#某次提交忘了某个文件的修改：
git commit -m 'xx' #不完整
git add filename #补漏
git commit --amend #提交到上一个commit

#查看远程分支信息
git remote -v
git remote show origin
#修改/删除远程分支
git remote rename src dst
git remote rm xxx
```

## Git标签

```bash
#查看
git tag -l
#创建
git tag -a xx -m "yy"
git push origin tagname/--tags
```

## Git命令别名

```bash
git config --global alias.unstage 'reset HEAD --'
git config --global alias.last 'log -1 HEAD'
git config --global alias.visual '!gitk'
#用法 git unstage/last/visual
```

## Git分支

```bash
#合并
git checkout master
git merge dev
#查看
git branch --merged/--no-merged
git checkout -b newbranch origin/remotebranch
git checkout same-name-on-origin origin #自动创建与远程分支同名的分支
git branch -u origin/branchname #设置或改变分支的远程跟踪分支
git push origin --delete branchname #删除远程分支

#变基
git rebase --onto xxx
git rebase basebranch topicbranch
#对本地尚未推送的更改进行变基操作，从而简化提交历史，但决不能对任何已推送到服务器的修改进行变基操作!!!
```

## 第7章 Git工具

Revision Selection

```bash
git show sha-1
git log --abbrev-commit --pretty=oneline
#查看引用日志 git reflog
#查看HEAD在5次前的所指向的提交
git show HEAD@{5}
#查看HEAD在2个月前指向哪个提交
git show HEAD@{2.months.ago}
#查看上一个提交
git show HEAD^
#上上上个提交
git show HEAD~3

#提交区间
#双点
#在dev但不在master中的提交
git log dev..master
#在master但不在远程分支上的提交(git push会提交这些到远程分支)
git log origin/master..HEAD
#A或B包含，但C不包含的提交
git log refA refB ^refC或--not refC
#多点
#master或dev，但不同时包含的提交
git log --left-right master…dev
```

### 交互式暂存

```bash
git add -I
git add -p filename
```

### Git储藏

```bash
git stash
git stash list
git stash apply stash@{2}默认是0，即最近那个
#重新应用暂存的修改
git stash apply --index
git stash drop stash@{2}默认是0
#不储藏已git add的修改
git stash --keep-index
#储藏包括未跟踪文件
git stash -u
git stash --patch
git stash branch test-change
```

### 清理工作目录

```bash
git clean -f -d
git clean -d -n
git clean -n -d -x #(包含忽略文件)
git clean -x -i #(交互式)
```

### 搜索

```bash
git grep
#搜索在哪里有target串
git grep -p -n target *.js
#git 日志搜索
#搜索什么时候引入target
git log -Starget --oneline
#行日志搜索
#查看filename.c文件中function函数的每一次变更
git log -L :function:filename.c
```

### 重写历史

```bash
#1.修改最后一次提交
git commit --amend #(仅限未push到远程的！)
#2.修改多个提交信息
git rebase -I HEAD~3
#其他：压缩提交、拆分提交、核武器级选项filter-branch
#从每个提交中移除一个文件
git filter-branch --tree-filter 'rm -f password.txt' HEAD
#使一个子目录变成新的根目录
git filter-branch --subdirectory-filter trunk HEAD
#全局修改邮箱地址
git filter-branch #…
```

### 重置解密

1.三棵树
![alt image text](/progit/3tree.png)
2.工作流
![alt image text](/progit/workflow.png)
3.速查表 哪个命令影响哪些树
![alt image text](/progit/cmd-tree.png)

### 高级合并

1.合并冲突
1.1中断一次合并
Revere:记住解决一个块冲突的方法，下次遇到相同冲突时，自动地解决它。

### 使用Git调试

文件标注
1.git blame -C -L xx yy
2.二分查找 git bisect …

### 子模块

git submodule ...

### 凭证存储

```bash
git config --global credential.helper store
git config --global credential.helper cache
```

### Git最佳实践 待了解
