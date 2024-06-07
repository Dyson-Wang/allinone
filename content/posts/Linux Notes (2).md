---
categories: [框架与技术]
tags: [框架与技术]
title: Linux Notes
date: '2022-09-05T10:52:59.297Z'
lastmod: '2024-05-08T11:15:15.724Z'
---

# Linux Notes

### 常用指令

`su` 切换用户

### 文件系统

`/etc/sysconfig/network-scripts/ifcfg-ens33` 网卡ens33配置

```
...
BOOTPROTO=(static|dhcp)
...
ONBOOT=yes
# 固定IP地址
IPADDR=192.168.131.138
NETMASK=255.255.255.0
GATEWAY=192.168.131.2
DNS=4.2.2.1
```

### 系统控制

抓取进程 `ps -aux | grep (filename|username)`

重启 `reboot`

立刻关机 `shutdown -h now`

查看系统发行版 `cat /etc/issue`

安装ifconfig `yum install net-tools`

### 防火墙
查看防火墙状态 systemctl status firewalld
开启防火墙 systemctl start firewalld  
关闭防火墙 systemctl stop firewalld
开启防火墙 service firewalld start 
若遇到无法开启
先用：systemctl unmask firewalld.service
然后：systemctl start firewalld.service

### 开放端口
查看想开的端口是否已开：firewall-cmd --query-port=6379/tcp
添加指定需要开放的端口：firewall-cmd --add-port=123/tcp --permanent
重载入添加的端口：firewall-cmd --reload
查询指定端口是否开启成功：firewall-cmd --query-port=123/tcp
移除指定端口：firewall-cmd --permanent --remove-port=123/tcp

### 修改环境变量

.bashrc 当前用户打开shell就会读取
/etc/profile env 等 系统级
thirdpartysoftware 保存在/usr/local/src/下
