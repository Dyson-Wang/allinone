---
categories: [服务器搭建日志]
tags: [服务器搭建日志]
title: vm服务器日志-rocky
date: '2024-02-03T14:03:11.175Z'
lastmod: '2024-05-08T11:20:52.691Z'
---

# vm服务器日志-rocky

## VM install

```
rocky-9.3-x86_64-minimal
```

-- blogs
-- env

## 日志

- **配置nju源**

```
sudo sed -e 's|^mirrorlist=|#mirrorlist=|g' \
         -e 's|^#baseurl=http://dl.rockylinux.org/$contentdir|baseurl=https://mirror.nju.edu.cn/rocky|g' \
         -i.bak \
         /etc/yum.repos.d/rocky-extras.repo \
         /etc/yum.repos.d/rocky.repo
dnf makecache
```

- **yum**

```
yum install -y git nodejs net-tools tar 
```

- **git 代理设置**

```
git config --global user.name "Dyson Wang"
git config --global user.email "Dyson.Wang@outlook.com"
git config --global http.proxy 'http://192.168.237.1:7890'
git config --global https.proxy 'http://192.168.237.1:7890'
```
