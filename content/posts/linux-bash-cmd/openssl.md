+++
title = "openssl"
categories = ["Bash命令"]
tags = ["Bash命令", "openssl", "命令行"]
+++



## openssl

```bash
# openssl查看证书内容
openssl x509 -text -noout -in ca.example.com-cert.pem

openssl crl -in /root/fabric-ca/clients/admin/msp/crls/crl.pem -text -noout

openssl crl -text -noout -in ca.pem

# 查看keyusage
openssl x509 -in ca-cert.pem -purpose -noout -text

#验证证书链
openssl verify -CAfile ca.pem user.pem


#How do I get common name (CN) from SSL certificate?
openssl x509 -noout -subject -in your-file.pem



#自签名是用以下命令查看Subject：和Issuer：的内容相同。
openssl x509 -text -noout -in 1.pem
#验证2.pem是1.pem颁发的命令(验证通过只返回OK)
openssl verify -verbose -CAfile 1.pem 2.pem

certificate signed by unknown authority:
openssl x509 -noout -text -in cacerts/cacert.pem | grep -A1 "Subject Key Identifier"
openssl x509 -noout -text -in admincerts/admincert.pem | grep -A1 "Authority Key Identifier"

```

## 公私钥匹配是用脚本

```bash
verify-cert-key.sh 1.pem 2.key
#返回PASS: key and cert match
```

脚本内容
![alt image text](/verify-cert-key.png)
