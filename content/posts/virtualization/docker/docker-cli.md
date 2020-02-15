+++
title = "docker命令"
categories = ["Docker"]
tags = ["Development", "Docker", "virtualization"]
+++

```bash
docker ps | awk '{print $NF}' | tail -7

#TODO 合并显示两栏，左边容器名，右边容器ip
docker ps | awk '{print $NF}' | tail -7 | xargs docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}'

docker ps | awk '{print $NF}' | tail -7 | xargs docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}'
docker rmi -f $(docker image ls | awk '{print $1}')

#进入容器执行命令
docker exec -it cli bash

#删除卷
docker volume rm $(docker volume ls | tail -n +2 | awk '{print $NF}')

#拷出容器里的文件
docker cp containerid:/some/path/file ./host/file
```
