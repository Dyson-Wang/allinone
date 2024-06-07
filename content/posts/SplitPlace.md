---
categories: [实验笔记]
attachments: [Clipboard_2024-05-09-16-51-46.png]
tags: [实验笔记]
title: SplitPlace
date: '2024-05-08T12:38:43.242Z'
lastmod: '2024-05-09T08:51:46.107Z'
---

# SplitPlace

## 实验路线

- 安装依赖
- 配置vagrant virtualbox docker
- proxy问题

## 环境配置

`python3 install.py`

### vagrant代理

```
# vagrantfile proxy

config.proxy.http     = "http://yourproxy:8080"
config.proxy.https    = "http://yourproxy:8080"
config.proxy.no_proxy = "localhost,127.0.0.1"
```

## 实验报错

![](/images/attachments/Clipboard_2024-05-09-16-51-46.png)
