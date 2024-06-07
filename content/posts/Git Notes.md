---
categories: [框架与技术]
attachments: [Clipboard_2022-09-10-17-37-34.png, Clipboard_2022-09-10-17-38-20.png, Clipboard_2022-09-10-17-40-13.png]
tags: [框架与技术]
title: Git Notes
date: '2022-09-10T09:32:17.716Z'
lastmod: '2024-05-08T11:15:15.655Z'
---

# Git Notes

## git 源码安装

```
//依赖库 gcc gcc-c++

```

### `git proxy`

```
//http || https
git config --global http.proxy 127.0.0.1:7890
git config --global https.proxy 127.0.0.1:7890

//sock5代理
git config --global http.proxy socks5 127.0.0.1:7891
git config --global https.proxy socks5 127.0.0.1:7891

git config --global --get http.proxy
git config --global --get https.proxy

git config --global --unset http.proxy
git config --global --unset https.proxy

```

### `git log `

- `-p` 显示diff补丁 -2 限定数量
- `--stat` 显示简略统计信息
- `--pretty` =oneline一行输出 =short,full,fuller
  ```
  $ git log --pretty=format:"%h - %an, %ar : %s"
    ca82a6d - Scott Chacon, 6 years ago : changed the version number
    085bb3b - Scott Chacon, 6 years ago : removed unnecessary test
    a11bef0 - Scott Chacon, 6 years ago : first commit
    ```
    ![](/images/attachments/Clipboard_2022-09-10-17-37-34.png)
- ![](/images/attachments/Clipboard_2022-09-10-17-38-20.png)

