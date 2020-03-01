+++
title = "Kubernetes"
categories = ["Kubernetes"]
tags = ["Kubernetes"]
+++

## kubectl 命令

```bash
#列出pods
kubectl get pods --all-namespaces
#在应用容器里执行命令
kubectl exec -it  postgredb-explorer-deployment-xxxxxxxxx -n explorer bash
#查看应用日志
kubectl logs -f postgredb-explorer-deployment-8d78b7d6f-fbx97 -n explorer
#一次创建多个configmap
#指定到yaml文件的所在目录
kubectl create -f x/y/z/configmap/
```
