---
categories: [框架与技术]
tags: [框架与技术]
title: Nginx Notes
date: '2022-09-06T07:52:42.435Z'
lastmod: '2024-05-08T11:15:15.770Z'
---

# [Nginx](https://nginx.org/en/) Notes

## curl
```
curl -o [filename] [link]
```

## Basic

### 依赖

```
yum install -y gcc gcc-c++ pcre pcre-devel zlib zlib-devel openssl openssl-devel
```

### Linux-nginx

```
cd ./nginx/nginx-1.16.1/
./configure --prefix=/usr/local/nginx --user=nginx --group=nginx 
--with-http_gzip_static_module //静态压缩
--with-http_stub_status_module //监视连接数等信息 ip/mystatus
--with-http_ssl_module //需要安装ssl证书时候用

make
make install
```

**nginx安装地址：** `/usr/local/nginx/`

**nginx托管页面目录：** `/usr/local/nginx/html/`

**nginx配置文件目录：** `/usr/local/nginx/conf/nginx.conf`

```
#user  nobody;
worker_processes  1;

#error_log  logs/error.log;
#error_log  logs/error.log  notice;
#error_log  logs/error.log  info;

#pid        logs/nginx.pid;


events {
    worker_connections  1024;
}


http {
    include       mime.types;
    default_type  application/octet-stream;

    sendfile        on;
    keepalive_timeout  65;

    server {
        listen       80;
        server_name  localhost;

        location / {
            root   html;
            index  index.html index.htm;
            # proxy_pass https://192.168.131.138/;
        }
        location /v3 {
            root   html;
            index  index.html index.htm;
            proxy_pass https://192.168.131.138/v3;
        }
        location /v1 {
            root   html;
            index  index.html index.htm;
            proxy_pass https://192.168.131.138/v1;
        }
        location /k8s {
            root   html;
            index  index.html index.htm;
            proxy_pass https://192.168.131.138/k8s;
        }

        error_page   500 502 503 504  /50x.html;
        location = /50x.html {
            root   html;
        }

    }

}
```
**nginx启动文件：** `/usr/local/nginx/sbin/nginx`
```
./nginx
nginx -s reopen #重启Nginx
nginx -s reload #重新加载Nginx配置文件，然后以优雅的方式重启Nginx
nginx -s stop #强制停止Nginx服务
killall nginx #杀死所有nginx进程  
nginx -s quit #优雅地停止Nginx服务（即处理完所有请求后再停止服务）
nginx -t #检测配置文件是否有语法错误，然后退出
nginx -v #显示版本信息并退出
nginx -V #显示版本和配置选项信息，然后退出
nginx -t #检测配置文件是否有语法错误，然后退出
nginx -T #检测配置文件是否有语法错误，转储并退出
nginx -q #在检测配置文件期间屏蔽非错误信息
nginx -?,-h #打开帮助信息  
nginx -p prefix #设置前缀路径(默认是:/usr/share/nginx/)
nginx -c filename #设置配置文件(默认是:/etc/nginx/nginx.conf)
nginx -g directives #设置配置文件外的全局指令
```

## error
```
getpwnam("nginx") failed //没有找到nginx用户
```
nginx编译安装之后，启动出现了：nginx: [emerg] getpwnam("nginx") failed
这个是因为我编译安装nginx的时候指定了--user=nginx和--group=nginx，去除就没事了
但是出于安全性考虑，还是用独立权限的账户运行（root权限太大，web渗透的时候可利用的机会太多了）

```
useradd -s /sbin/nologin -M nginx
mkdir -p  /var/cache/nginx/client_temp
```
