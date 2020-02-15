+++
title = "git"
categories = ["Bash命令"]
tags = ["Bash命令", "Git", "Linux"]
+++



## git命令

```bash
#对比两个分支
git diff branch1..branch2

#避免git push每次都要输入用户名和密码 (有安全风险)
git config credential.helper store

#当改了很多代码，却又只想提交某部分修改，用以下命令，详见https://stackoverflow.com/questions/1085162/commit-only-part-of-a-file-in-git
git add --patch filename

#格式化git commit message
npx git-cz

#添加子模块（一个git仓库为另一个git仓库下的子目录，同时保持独立的git记录）
git submodule add https://github.com/chaconinc/DbConnector

#详见 https://git-scm.com/book/zh/v2/Git-%E5%B7%A5%E5%85%B7-%E5%AD%90%E6%A8%A1%E5%9D%97

#修改分支名
git branch -m src dst

#开分支
#1. 远程先开好分支然后拉到本地
git checkout -b feature-branch origin/feature-branch    //检出远程的feature-branch分支到本地
#2. 本地先开好分支然后推送到远程
git checkout -b feature-branch    //创建并切换到分支feature-branch  
git push origin feature-branch:feature-branch    //推送本地的feature-branch(冒号前面的)分支到远程origin的feature-branch(冒号后面的)分支(没有会自动创建)

#来自 <https://www.cnblogs.com/qyf404/p/git_push_local_branch_to_remote.html> 


#push/pull时，git协议不行就换http协议操作

#查询某个git仓库的hooks目录位置（一般来说是.git/hooks，但是submodule会有所不同）
git rev-parse --git-path hooks

#对比两个git分支，且忽略指定目录的不同
git diff alpha tmp --name-only | grep -v "crypto-config"
```
