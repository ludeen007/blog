+++
title = "Couchdb"
categories = ["Fabric"]
tags = ["Fabric", "Couchdb"]
+++

## Couchdb 校验数据入库，比如在 wallet 验证身份(可扩展到查询其他数据)

### 1. 去可视化页面里进行人工查验

couchdb 服务起来后，访问 http://IP:PORT/_utils/index.html 来查看数据库

1. 查看应用日志，找到标志身份的关键字段，BEGIN PUBLIC KEY-----\n 后的字符串，例如 MFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAErHWrHfmNlyRuSQCONq6i6MNktNws
2. 在对应的 CouchDB 可视化页面的 wallet 数据库执行以下正则查询

```json
{
  "selector": {
    "member": {
      "$regex": "MFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAErHWrHfmNlyRuSQCONq6i6MNktNws"
    }
  }
}
```

3. 如果查询结果不为空，表示 wallet 存在身份

### 2. 用 bash 脚本查询 Couchdb 数据

#### 2.1 按主键查询

```bash
#!/bin/bash

set -x

USER=admin:adminpw

URL=$1
#URL=http://$USER@IP:PORT

DADABASE_NAME=your-database-name
KEY_WORD=$2
#KEY_WORD="02238fa044fea40ef1167cadd091025a118b50b2ccd5079557e8b780cfff03fa"


curl $URL

curl -X GET $URL/$DADABASE_NAME

curl -X GET $URL/$DADABASE_NAME/_all_docs

RET=$(curl -s -X POST $URL/$DADABASE_NAME/_find \
        -H "content-type: application/json" \
        -d "{\"selector\":{\"docType\":\"identity\",\"key\":\"$KEY_WORD\"}}")

echo "RET:"
echo $RET

set +x
```

#### 2.2 按正则查询

```bash
#!/bin/bash

set -x

URL=$1

DADABASE_NAME=wallet
KEY_WORD="$2"
#KEY_WORD="MIGHAgEAMBMGByqGSM49AgEGCCqGSM49AwEHBG0wawIBAQQgBWmCNqiRTSoGtGJc"


curl $URL

curl -X GET $URL/$DADABASE_NAME

#curl -X GET $URL/$DADABASE_NAME/_all_docs

RET=$(curl -s -X POST $URL/$DADABASE_NAME/_find \
        -H "content-type: application/json" \
        -d "{\"selector\":{\"member\":{\"\$regex\":\"$KEY_WORD\"}}}")

echo "RET:"
echo $RET

set +x
```
