---
categories: [个人笔记]
tags: [个人笔记]
title: Github
date: '2022-09-11T02:34:29.927Z'
lastmod: '2024-05-08T11:16:12.625Z'
---

# Github

1. 获取GitHub官方CDN地址

首先,打开

The Best IP Address, Email and Networking Tools
​www.ipaddress.com/
查询以下三个链接的DNS解析地址

github.com
assets-cdn.github.com
github.global.ssl.fastly.net

140.82.113.4
185.199.108.153
151.101.1.194

2. 修改系统Hosts文件

接着,打开系统hosts文件(需管理员权限)。
路径：C:\Windows\System32\drivers\etc

mac或者其他linux系统的话,是/etc下的hosts文件,需要切入到root用户修改

```
# Copyright (c) 1993-2009 Microsoft Corp. 
# 
# This is a sample HOSTS file used by Microsoft TCP/IP for Windows. 
# 
# This file contains the mappings of IP addresses to host names. Each 
# entry should be kept on an individual line. The IP address should 
# be placed in the first column followed by the corresponding host name. 
# The IP address and the host name should be separated by at least one 
# space. 
# 
# Additionally, comments (such as these) may be inserted on individual 
# lines or following the machine name denoted by a '#' symbol. 
# 
# For example: 
# 
#      102.54.94.97     rhino.acme.com          # source server 
#       38.25.63.10     x.acme.com              # x client host 




# localhost name resolution is handled within DNS itself. 
#   127.0.0.1       localhost 
#   ::1             localhost 


140.82.113.3    github.com
185.199.108.153 assets-cdn.github.com
199.232.69.194  github.global.ssl.fastly.net
```
并在末尾添加三行记录并保存。(需管理员权限，注意IP地址与域名间需留有空格)
感谢评论区 
@trans-bug
 的分享， 对于ubuntu系统，修改完hosts文件执行如下命令: sudo /etc/init.d/network-manager restart
3. 刷新系统DNS缓存

最后,Windows+X 打开系统命令行（管理员身份）或powershell

运行 `ipconfig /flushdns` 手动刷新系统DNS缓存。

- mac系统修改完hosts文件,保存并退出就可以了.不要要多一步刷新操作.
- centos系统执行/etc/init.d/network restart命令 使得hosts生效

