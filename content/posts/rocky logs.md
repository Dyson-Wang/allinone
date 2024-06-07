---
categories: [个人笔记, 框架与技术]
tags: [个人笔记, 框架与技术]
title: rocky logs
date: '2023-06-24T01:06:05.135Z'
lastmod: '2024-05-08T11:16:12.801Z'
---

# rocky logs

## 安装环境

- 切换yum源nju mirror
- 安装net-tools
- git 2.39.1
- tar 1.34
- 手动全局安装nodejs
- 配置npm mirror
```
npm get registry
npm config set registry https://registry.npmmirror.com
```
```
yarn config get registry
yarn config set registry https://registry.npmmirror.com
```


- yum-utils
```
sudo yum install -y yum-utils

sudo yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
```
- docker
```
sudo yum install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y

systemctl start docker

systemctl enable docker
```
```
// /etc/docker/daemon.json

{
    "registry-mirrors": [
        "https://24fgpaf5.mirror.aliyuncs.com",
        "https://83f60d800b31479a97ed45ce119dab75.mirror.swr.myhuaweicloud.com",
        "https://hub-mirror.c.163.com",
        "https://docker.mirrors.ustc.edu.cn",
        "https://mirror.baidubce.com",
        "https://reg-mirror.qiniu.com",
        "https://mirror.ccs.tencentyun.com",
        "https://registry.docker-cn.com"
    ]
}

systemctl daemon-reload
systemctl restart docker
docker info
```

# softwares

## gitlab

```
docker pull gitlab/gitlab-ce
docker images

docker run --detach \
  --publish 16443:443 --publish 16680:80 --publish 16622:22 \
  --name gitlab \
  --restart always \
  --volume $GITLAB_HOME/config:/etc/gitlab:Z \
  --volume $GITLAB_HOME/logs:/var/log/gitlab:Z \
  --volume $GITLAB_HOME/data:/var/opt/gitlab:Z \
  gitlab/gitlab-ce

docker run 
  -d
  -p 443:443 -p 9000:80 -p 22:22 //外：内
  --name gitlab
  --restart always
  -v $HOME/docker/gitlab/config:/etc/gitlab
  -v $HOME/docker/gitlab/logs:/var/log/gitlab
  -v $HOME/docker/gitlab/data:/var/opt/gitlab
  gitlab/gitlab-ce

# -d：后台运行
# -p：将容器内部端口向外映射
# --name：命名容器名称
# -v：将容器内数据文件夹或者日志、配置等文件夹挂载到宿主机指定目录

# 443:443：将http：443映射到外部端口443
# 9000:80：将web：80映射到外部端口9000
# 22:22：将ssh：22映射到外部端口22

port 8888 root 15630148029

```

## nginx /usr/local/nginx

