+++
title = "Fabric 工具使用"
categories = ["Fabric命令"]
tags = ["Fabric", "Hyperledger", "命令行"]
+++



## configtxlator

```bash
#创世块的内容转为json，里面有configtx.yaml文件的内容，尤其是policies的。
configtxlator proto_decode --input genesis.block --type common.Block >> genesis.block.json
```

![image alt text](/admin-base64.png)

上图箭头指向管理员的证书列表,进到crypto-config/ordererOrganizations/example.com/users/Admin@example.com/msp/signcerts目录，执行base64 Admin@example.com-cert.pem >> admin.base64即可得到图示的base64证书内容字符串。
