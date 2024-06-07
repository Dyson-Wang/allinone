---
categories: [框架与技术]
tags: [框架与技术]
title: GitLab
date: '2024-01-02T07:06:51.216Z'
lastmod: '2024-05-08T11:15:49.901Z'
---

# GitLab

## yum安装

```
sudo firewall-cmd --permanent --add-service=http
sudo firewall-cmd --permanent --add-service=https
sudo systemctl reload firewalld

sudo yum install postfix
sudo systemctl enable postfix
sudo systemctl start postfix

curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.rpm.sh | sudo bash
yum install gitlab-ce

#/etc/gitlab/gitlab.rb
#external_url "http://10.0.0.1"

gitlab-ctl reconfigure

systemctl enable gitlab-runsvdir.service
```

## apt安装

## config

```
[root@localhost ssl]# vim /etc/gitlab/gitlab.rb
 
external_url 'https://gitlab.example.com'      ###改为https开头
 
nginx['enable'] = true
nginx['client_max_body_size'] = '2048m'
nginx['redirect_http_to_https'] = true           #取消#号 更改注释并为true
nginx['ssl_certificate'] = "/etc/gitlab/ssl/gitlab.example.com.crt"     #更改路径
nginx['ssl_certificate_key'] = "/etc/gitlab/ssl/gitlab.example.com.key"     #更改路径
 ###注意如果使用docker，这里的路径，需要是docker内证书的路径
[root@localhost ssl]# mkdir /etc/gitlab/ssl
```
