---
categories: [框架与技术]
tags: [框架与技术]
title: rancher & k8s notes
date: '2022-09-05T09:38:21.715Z'
lastmod: '2024-05-08T11:15:15.819Z'
---

# rancher & k8s notes

```
yum install wget expect vim net-tools ntp bash-completion ipvsadm ipset jq iptables conntrack sysstat libseccomp conntrack ipvsadm ipset jq iptables curl sysstat libseccomp wgeta vim net-toolsgit yum-utils device-mapper-persistent-data lvm2 -y

```

```
yum-config-manager --add-repo https://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo

yum install -y docker-ce-19.03.9-3.el7

```

```
mkdir -p /etc/docker
tee /etc/docker/daemon.json <<-'EOF'
{
"registry-mirrors": ["https://4bsnywin.mirror.aliyuncs.com"],
"exec-opts":["native.cgroupdriver=systemd"]
}
EOF
```

```
systemctl daemon-reload; systemctl restart docker; systemctl enable --now docker.service

```

```
yum -y install chrony
```

```
cat > /etc/chrony.conf <<-'EOF'
pool 192.168.131.136 iburst
driftfile /var/lib/chrony/drift
makestep 1.0 3
rtcsync
allow 192.168.131.0/24
local stratum 10
keyfile /etc/chrony.keys
leapsectz right/UTC
logdir /var/log/chrony
EOF
```

```
systemctl restart chronyd.service --now

chronyc -a makestep

chronyc sourcestats -v

```

```
mkdir /var/log/journal
mkdir /etc/systemd/journald.conf.d
cat > /etc/systemd/journald.conf.d/99-prophet.conf <<-'EOF'
[Journal]
#持久化保存到磁盘
Storage=persistent
#压缩历史日志
Compress=yes
SyncIntervalSec=5m
RateLimitInterval=30s
RateLimitBurst=1000
#最大占用空间10G
SystemMaxUse=10G
#单日志文件最大200M
SystemMaxFileSize=200M
#日志保存时间2周
MaxRetentionSec=2week
#不将日志转发到syslog
ForwardToSyslog=no
EOF
```
```
systemctl restart systemd-journald

```
```
cat > /etc/hosts <<-'EOF'
127.0.0.1 localhost localhost.localdomain localhost4 localhost4.localdomain4
::1 localhost localhost.localdomain localhost6 1ocalhost6.localdomain6
192.168.131.129 rancher
192.168.131.134 k8s-master-01
192.168.131.135 k8s-node-02
192.168.131.133 k8s-node-03
EOF
```
```
nmtui-hostname

sed -ri 's/.*swap.*/#&/' /etc/fstab

reboot

```




### 注释：rancher主机的配置

```
docker pull rancher/rancher:v2.6.3-linux-amd64

mkdir -p /mnt/d/rancher_data

docker run -d --privileged -p 80:80 -p 443:443 -v /mnt/d/rancher_data:/var/lib/rancher/ --restart=always --name rancher-v2.6.3 rancher/rancher:v2.6.3-linux-amd64
```


#### 最小安装 centos 配置 ifconfig 命令
```
yum install net-tools
```

