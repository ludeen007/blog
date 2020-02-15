+++
title = "Couchdb校验入库"
categories = ["Couchdb"]
tags = ["Fabric", "Hyperledger", "Couchdb", "数据库"]
+++

## wallet验证身份(可扩展到查询其他数据)
couchdb服务起来后，访问
http://IP:PORT/_utils/index.html
来查看身份信息数据库

来自 <http://docs.couchdb.org/en/stable/install/unix.html#user-registration-and-security>

1. 查看日志
2. 找到关键字段，BEGIN PUBLIC KEY-----\n后的字符串 MFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAErHWrHfmNlyRuSQCONq6i6MNktNws
3. 在对应的CouchDB可视化页面的wallet数据库执行查询

```json
{
   "selector": {
      "member": {
         "$regex": "MFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAErHWrHfmNlyRuSQCONq6i6MNktNws"
      }
   }
}
```

4. 如果查询结果不为空，表示wallet存在身份

## 查询Couchdb数据的bash脚本
按主键查询

```bash
#!/bin/bash

set -x

USER=admin:adminpw

URL=$1
#URL=http://$USER@IP:PORT

DADABASE_NAME=ic
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

按正则查询

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
