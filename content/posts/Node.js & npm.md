---
categories: [框架与技术]
tags: [框架与技术]
title: Node.js & npm
date: '2022-09-06T07:48:17.757Z'
lastmod: '2024-05-08T11:15:15.794Z'
---

# Node.js & npm

源码安装nodejs

```
./configure --prefix=/usr/local/node/0.10.24
```

## npm

### `package.json`

#### `proxy` 选项

作用过程为APP向自身路由请求API，如果404，则由代理转发请求`proxy`指向的服务器上的API。

https://localhost:3000/clusters/projects/projects/pods/hhh666-dd88895c4-55v6n
https://localhost:3000/clusters/projects/projects/pods/pushprox-kube-etcd-client-2ncmj
