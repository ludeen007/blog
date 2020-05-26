+++
title = "git"
categories = ["Bash命令"]
tags = ["Bash命令", "Git", "Linux"]
+++

git 实用工具、使用技巧等

## bash-git-prompt

在 bash 命令提示符后面，显示有用的 git 信息，比如有几个文件改动等
<https://github.com/magicmonty/bash-git-prompt>

## git 命令别名，减少打字

<https://github.com/GitAlias/gitalias>

## git cheat sheet

<https://github.com/arslanbilal/git-cheat-sheet>

## git tips

<https://github.com/git-tips/tips>

## 备忘的 git 命令

### 对比两个分支

git diff branch1..branch2

### 避免 git push 每次都要输入用户名和密码

注：有安全风险
git config credential.helper store

### 当改了很多代码，却又只想提交某部分修改

git add --patch filename

### 查看 diff，只看新增和修改，不看删除等

git diff --diff-filter=AM

### 格式化 git commit message

npx git-cz

### 添加子模块

一个 git 仓库为另一个 git 仓库下的子目录，同时保持独立的 git 记录
git submodule add https://github.com/user/repo
详见 https://git-scm.com/book/zh/v2/Git-%E5%B7%A5%E5%85%B7-%E5%AD%90%E6%A8%A1%E5%9D%97

### 修改分支名

git branch -m src dst

### 开分支

1. 远程先开好分支然后拉到本地
   git checkout -b feature-branch origin/feature-branch //检出远程的 feature-branch 分支到本地
2. 本地先开好分支然后推送到远程
   git checkout -b feature-branch //创建并切换到分支 feature-branch
   git push origin feature-branch:feature-branch //推送本地的 feature-branch(冒号前面的)分支到远程 origin 的 feature-branch(冒号后面的)分支(没有会自动创建)
   来自 <https://www.cnblogs.com/qyf404/p/git_push_local_branch_to_remote.html>

### push/pull 时，git 协议不行就换 http 协议操作

### 查询某个 git 仓库的 hooks 目录位置

一般来说是.git/hooks，但是 submodule 会有所不同
git rev-parse --git-path hooks

### 对比两个 git 分支，且忽略指定目录

git diff alpha tmp --name-only | grep -v "dir-name"

### 对比两个 git 分支，且忽略指定目录和文件

git diff accfa7d7 HEAD ":(exclude)node_modules/" ":(exclude)\*.yaml"

如果经常需要忽略某个目录，比如 node_modules/，可以在/etc/profile 加入环境变量
EXCL=":(exclude)node_modules/"
然后执行命令时引用它
git diff --cached --name-only \$EXCL

### conditional config on Windows

在 Windows 系统的某些目录下用新的配置文件
.gitconfig 添加 includeIf 定制某些目录下 git 用别的配置文件
示例：目录 c:/directory-name/subdir/下，用 email user2@two.com 而不是全局的 email user1@one.com
.gitconfig 内容示例
[user]
name = user1
email = user1@one.com
[includeIf "gitdir/i:c:/directory-name/subdir/"]
path = .gitconfig-another
.gitconfig-another 设置别的配置项，比如 email
.gitconfig-another 内容示例
[user]
email = user2@two.com

### stash only specific files

git stash push -p -m some-message dir1/file1 dir2/file2

### stage the modified and deleted files, exclude untracked files

git add -u

### find the latest 10 commits

If you want commits for all branches you need the --all argument, limit git log to ten with -10 and use --date-order to tell git log to sort the commits with respect to date.
git log -10 --all --date-order
