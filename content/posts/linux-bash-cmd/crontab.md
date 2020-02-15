+++
title = "bash终端"
categories = ["crontab"]
tags = ["crontab", "Linux"]
+++

## 技巧

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
