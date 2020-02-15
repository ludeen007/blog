+++
title = "javascript"
categories = ["编程语言"]
tags = ["编程语言", "Javascript"]
+++

## javascript

package.json文件里加入以下命令，来使用淘宝npm镜像源安装依赖包

```json
{
    "preinstall": "npm config set registry http://registry.npm.taobao.org/"
}
```

用gulp mocha chai 单元测试时，用it.only()或者decribe.only()可以只运行单次测试
