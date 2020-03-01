+++
title = "know-how"
categories = ["know-how"]
tags = ["know-how"]
+++

## 从 GitHub 下载单个文件

1. Go to the file you want to download.
2. Click it to view the contents within the GitHub UI.
3. In the top right, right click the Raw button.
4. Save as...

来自 <https://stackoverflow.com/questions/4604663/download-single-files-from-github>

## javascript

package.json 文件里加入以下命令，来使用淘宝 npm 镜像源安装依赖包

```json
{
  "preinstall": "npm config set registry http://registry.npm.taobao.org/"
}
```

用 gulp mocha chai 单元测试时，用 it.only()或者 decribe.only()可以只运行单次测试

## curl 命令行&符号要转义

## Vim

### delete to end of file

:.,\$d

来自 <https://alvinalexander.com/linux/vi-vim-delete-line-commands-to-end>

## Windows CMD 命令

### 定时关机

```cmd
$$ 一分钟后强制关机
shutdown /s /t 60 /f
```

### 刷新 DNS 缓存

```cmd
ipconfig /flushdns
```
