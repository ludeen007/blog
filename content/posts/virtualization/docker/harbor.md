+++
title = "搭建harbor.io私有容器仓库"
categories = ["Docker"]
tags = ["Development", "harbor.io", "Docker", "virtualization"]
+++

```bash
#hosts 配置：
#172.x.y.z harbor.io
#登陆
docker login -u admin -p admin harbor.io
#创建、改标签、推送镜像
docker build -t mynode:v1.0 .

docker tag mynode:v1.0 harbor.io/nodejs/mynode:v1.0

docker push harbor.io/nodejs/mynode:v1.0
```
