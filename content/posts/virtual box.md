---
categories: [服务器搭建日志]
tags: [服务器搭建日志]
title: virtual box
date: '2024-05-06T03:12:42.654Z'
lastmod: '2024-05-08T11:22:23.447Z'
---

# virtual box

# 删除虚拟机

```
VBoxManage controlvm vm1 poweroff
VBoxManage controlvm vm2 poweroff
VBoxManage unregistervm --delete vm1
VBoxManage unregistervm --delete vm2
```
## echo

```
export proxy="http://172.21.15.197:2080"
export http_proxy=$proxy
export https_proxy=$proxy
export ftp_proxy=$proxy
export no_proxy="localhost, 127.0.0.1, ::1, 192.168.0.0/16, 172.16.0.0/12, 10.0.0.0/8"
echo 'Acquire::http::Proxy "http://172.21.15.197:2080/";\nAcquire::https::Proxy "http://172.21.15.197:2080/";' | sudo tee -a /etc/apt/apt.conf.d/proxy.conf
```
