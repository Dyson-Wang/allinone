---
categories: [框架与技术]
tags: [框架与技术]
title: Https Notes
date: '2023-09-20T06:39:33.891Z'
lastmod: '2024-05-08T11:15:15.676Z'
---

# Https Notes

```
openssl genrsa -des3 -out ca.pass.key 2048
openssl rsa -in ca.pass.key -out ca.key
openssl req -new -x509 -key ca.key -out ca.crt -days 365
openssl genrsa -des3 -out server.key 2048
openssl req -new -key server.key -out server.csr
openssl x509 -req -in server.csr -CA ca.crt -CAkey ca.key -set_serial 01 -out server.crt -days 365
```

## 虚构一个CA机构 RSA

```
# 生成CA认证机构的证书密钥key

# -genra    生成RSA私钥
# -des3 des3算法
# -out server.key 生成的私钥文件名
# -2048 私钥长度

openssl genrsa -des3 -out ca.pass.key 2048

# 去除密钥里的密码(可选)
# 这里需要再输入一次原来设的密码

openssl rsa -in ca.pass.key -out ca.key

# 用私钥ca.key生成CA认证机构的证书ca.crt
# 其实就是相当于用私钥生成公钥，再把公钥包装成证书

# -req 生成证书签名请求
# -new 新生成
# -key 私钥文件
# -out 生成的CSR文件
openssl req -new -x509 -key ca.key -out ca.crt -days 365
# 这个证书ca.crt有的又称为"根证书",因为可以用来认证其他证书
```

## 生成网站的证书

```
# 生成自己网站的密钥server.key
openssl genrsa -des3 -out server.key 2048

# 生成自己网站证书的请求文件
# 如果找外面的CA机构认证，也是发个请求文件给他们
# 这个私钥就包含在请求文件中了，认证机构要用它来生成网站的公钥，然后包装成一个证书

openssl req -new -key server.key -out server.csr 
-subj=C = CN, ST = beijing, L = beijing, O = xiao.work, OU = xiao, CN = gitlab.xiao.work, emailAddress = wangxinghao2001@163.com

# 使用虚拟的CA认证机构的证书ca.crt，来对自己网站的证书请求文件server.csr进行处理，生成签名后的证书server.crt
# 注意设置序列号和有效期（一般都设1年）

openssl x509 -req -in server.csr -CA ca.crt -CAkey ca.key -set_serial 01 -out server.crt -days 365

# set_serial指定生成的自签名根证书的序列号，默认情况下生成的自签名根证书序列号是0；该选项也只有在生成自签名根证书的时候有效。
```

## 配置nginx

```
把server.crt 和server.key 文件放在nginx/conf文件夹下。(和nginx.conf文件同一文件夹)
 
ssl_certificate server.crt;
ssl_certificate_key server.key;

/443 搜索 注释
```
## windows hosts配置

```
C:\Windows\System32\drivers\etc\hosts
```
