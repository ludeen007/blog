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

## 查看 cpu 和内存信息

```bash
cat /proc/meminfo
```

## rabbimqadmin

```bash
rabbitmqadmin.py -H 172.16.87.31 -P 32577 -u guest -p guest list queues | grep  amq | awk {'print $2'} | xargs -I {} rabbitmqadmin.py -H 172.16.87.31 -P 32577 -u guest -p guest delete queue name={}


#!/bin/bash
#删除固定名字的队列
queues=(
    queue1
    queue2
)

HOST=localhost
PORT=5672
PREFIX=test.
VHOST=/

for value in "${queues[@]}"; do
    rabbitmqadmin.py -H $HOST -P $PORT -V $VHOST -u guest -p guest delete queue name=$PREFIX$value
done
```
