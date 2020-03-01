+++
title = "Fabric 命令行工具使用"
categories = ["Fabric"]
tags = ["Fabric"]
+++

## Fabric 命令行工具

### configtxlator

```bash
#创世块的内容转为json，里面有configtx.yaml文件的内容，尤其是policies的。
configtxlator proto_decode --input genesis.block --type common.Block >> genesis.block.json
```

![image alt text](/admin-base64.png)

上图箭头指向管理员的证书列表,进到 crypto-config/ordererOrganizations/example.com/users/Admin@example.com/msp/signcerts 目录，执行 base64 Admin@example.com-cert.pem >> admin.base64 即可得到图示的 base64 证书内容字符串。
