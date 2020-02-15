+++
title = "经常在linux 终端使用的命令"
categories = ["Bash命令"]
tags = ["Bash命令", "命令行", "Linux"]
+++

## tree

```bash
#tree命令排除目录
tree -I "node_modules" .

#只看目录，而且打印全路径
tree -afd ../workbench
```

## tar

```bash
#压缩
tar cvzf scb-blockchain-k8s.tar.gz ./scb-blockchain-k8s/
#压缩时排除某些目录（可能要先执行shopt -s globstar）
tar cvfz gulp-test.tar.gz --exclude=**/.git --exclude=**/node_modules gulp-test/
#解压缩
tar zxvf xxx.tar.gz
#查看文件
tar tvf xxx.tar
```

## diff

```bash
#对比两个目录
#This should do the job:
 diff -qr -x 'node_modules' ../../../scb-blockchain-nodejs-svc/ scb-blockchain-nodejs-svc/ | less
#Options explained (via diff(1) man page):
#• -r - Recursively compare any subdirectories found.
#• -q - Output only whether files differ.
#• -x 排除该目录

来自 <https://stackoverflow.com/questions/16787916/difference-between-two-directories-in-linux>
```

## ps

```bash
#列出所有进程
ps aux | less
```

## kill

```bash
给进程发送信号
kill -s 15 pid
```

## find

```bash
#查找以.ipynb结尾的普通文件
find -type f -name *.ipynb
#把.cpp文件重命名为同名的.h文件
find . -name '*.cpp' -exec sh -c 'mv "$0" "${0%.cpp}.h"' {} \;
```

## 拷贝目录，但排除某些目录

```bash
rsync -r --verbose --exclude 'exclude_pattern' ./* /to/where/
#来自 <https://stackoverflow.com/questions/4585929/how-to-use-cp-command-to-exclude-a-specific-directory>
```
