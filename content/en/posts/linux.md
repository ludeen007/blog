+++
title = "bash"
categories = ["Bash命令"]
tags = ["Bash命令"]
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

## crontab

```bash
#定期任务，修改/etc/crontab文件后，记得重启crontab服务(sudo systemctl restart crond.service)使修改生效
#任务例子
# For details see man 4 crontabs

# Example of job definition:
# .---------------- minute (0 - 59)
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ...
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7) OR sun,mon,tue,wed,thu,fri,sat
# |  |  |  |  |
# *  *  *  *  * user-name  command to be executed
# every minute
* * * * * root date >> ~/workbench/crontab-output/every-minute.txt
# every 5 minutes
*/5 * * * * root date >> ~/workbench/crontab-output/every-5-minute.txt
# every 5 hours
* */5 * * * root date >> ~/workbench/crontab-output/every-5-hours.txt
# every 15th day of month
0 0 15 * * root date >> ~/workbench/crontab-output/every-15th-day.txt
# every 4th weekday
0 0 * * 4 root date >> ~/workbench/crontab-output/every-4th-weekday.txt
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
