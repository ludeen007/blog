+++
title = "bash终端"
categories = ["Bash命令"]
tags = ["Bash命令", "Linux"]
+++

## 技巧

```bash
#重新执行上一个命令
!!
#获取上一个命令的输出
$(!!)
#复制fabric-ca-client 到当前目录下的bin目录，可以这样：
which fabric-ca-client
cp $(!!) ./bin
```

## 同步时间

```bash
ntpdate 0.asia.pool.ntp.org
```

## 找出最大的文件或目录

```bash
du -hs * | sort -rh | head -5

du -Sh | sort -rh | head -5

find -type f -exec du -Sh {} + | sort -rh | head -n 5
```

## 查看端口号占用

```bash
#找出占用25672端口号的pid(在最后一栏)
netstat -pan | grep 25672

#查看pid对应的进程信息
ps aux | grep 5334
```

## 查看cpu和内存信息

```bash
cat /proc/meminfo
```
