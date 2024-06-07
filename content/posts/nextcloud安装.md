---
categories: [服务器搭建日志]
tags: [服务器搭建日志]
title: nextcloud安装
date: '2024-05-03T07:49:10.528Z'
lastmod: '2024-05-08T11:21:57.843Z'
---

# nextcloud安装

## seafile?安装

```
sudo docker run \
--init \
--sig-proxy=false \
--name nextcloud-aio-mastercontainer \
--restart always \
--publish 10180:80 \
--publish 10181:8080 \
--publish 10183:8443 \
--volume nextcloud_aio_mastercontainer:/mnt/docker-aio-config \
--volume /var/run/docker.sock:/var/run/docker.sock:ro \
nextcloud/all-in-one:latest
```
