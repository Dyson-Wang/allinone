---
categories: [框架与技术]
tags: [框架与技术]
title: docker in rocky
date: '2023-05-09T11:19:11.421Z'
lastmod: '2024-05-08T11:15:15.618Z'
---

# docker in rocky


```
sudo yum install -y yum-utils
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo

yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
yum install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

```
// daemon.json

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

```
sudo dnf check-update
sudo dnf config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
sudo dnf install docker-ce docker-ce-cli containerd.io -y
sudo systemctl start docker
sudo systemctl status docker
sudo systemctl enable docker
```

```
docker pull mysql:latest
docker images
docker ps -a

docker run -itd --name mysql-test -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 mysql

```

-i 以交互模式运行容器，通常与 -t 同时使用
-t 为容器重新分配一个伪输入终端，通常与 -i 同时使用
-d 后台运行容器，并返回容器ID
--name="nginx-lb": 为容器指定一个名称
-e username="ritchie": 设置环境变量
-p: 指定端口映射，格式为：主机(宿主)端口:容器端口

## drone 

```
docker run
  --volume=/srv/drone:/data
  --env=DRONE_GITLAB_SERVER=HTTP://192.168.1.104:8888
  --env=DRONE_GITLAB_CLIENT_ID=b19a3167484bf0d283e16a57b4f4e31e63617b48ebf4fc1714a2078eecaef00c
  --env=DRONE_GITLAB_CLIENT_SECRET=56bba1c6fa31998b6e0923c54300f60ba513b9ffcdc41696c258975ff1537f54
  --env=DRONE_RPC_SECRET=323c3689a93a2853c38b28e78736a482
  --env=DRONE_SERVER_HOST=192.168.1.104
  --env=DRONE_SERVER_PROTO=http
  --publish=32222:80
  --publish=32221:443
  --restart=always
  --detach=true
  --name=drone
  drone/drone:latest

```

```
version: '3.9'
# 创建自定义网络
networks:
  drone:
    name: drone
    driver: bridge
services:
  # 数据库服务
  db:
    image: postgres:latest
    container_name: drone_db
    restart: always
    networks:
      - drone # 加入到drone网络
    ports:
      - '32000:5432'
    environment:
      - POSTGRES_USER=drone # PGSQL默认用户
      - POSTGRES_PASSWORD=drone # PGSQL默认密码
      - POSTGRES_DB=drone # PGSQL默认数据库
    volumes:
      - /srv/drone/db:/var/lib/postgresql/data
  # Drone Server 服务
  server:
    image: drone/drone:latest # 目前drone最新版本为 2.8.0
    container_name: drone_server
    restart: always
    networks:
      - drone # 加入到drone网络
    ports:
      - '32222:80'
    environment:
      - DRONE_SERVER_PROTO=http # 访问协议，创建webHooks和重定向
      - DRONE_SERVER_HOST=192.168.1.104:32222 # 主机名称，创建webHooks和重定向
      - DRONE_RPC_SECRET=323c3689a93a2853c38b28e78736a482 # 与 drone runner 通讯的密钥
      - DRONE_USER_CREATE=username:root,admin:true # 管理员账户
      - DRONE_DATABASE_DRIVER=postgres # 数据库类型
      - DRONE_DATABASE_DATASOURCE=postgres://drone:drone@db/drone?sslmode=disable # 数据库连接
      - DRONE_GIT_ALWAYS_AUTH=true # 使用 oauth 身份验证信息拉取代码
      - DRONE_GITLAB_SERVER=HTTP://192.168.1.104:8888
      - DRONE_GITLAB_CLIENT_ID=b19a3167484bf0d283e16a57b4f4e31e63617b48ebf4fc1714a2078eecaef00c
      - DRONE_GITLAB_CLIENT_SECRET=56bba1c6fa31998b6e0923c54300f60ba513b9ffcdc41696c258975ff1537f54
    volumes:
      - /srv/drone/server:/data
      - /var/run/docker.sock:/var/run/docker.sock
    depends_on:
      - db
  # Drone Docker Runner
  runner:
    image: drone/drone-runner-docker:latest # 目前drone-runner-docker最新版本为 1.8.0
    container_name: drone_runner
    restart: always
    networks:
      - drone # 加入到drone网络
    ports:
      - '32220:3000'
    environment:
      - DRONE_RUNNER_NAME=docker-runner
      - DRONE_RUNNER_CAPACITY=10 # 限制runner可执行的并发管道数量
      - DRONE_RPC_PROTO=http # 访问drone server 协议
      - DRONE_RPC_HOST=192.168.1.104:32222 # 访问drone server 服务器地址
      - DRONE_RPC_SECRET=e1ad8a7f3dbc68ca9c21bcc949335009 # 与 drone server 通讯的密钥
      - DRONE_UI_USERNAME=root # Drone Runner 的 UI 用户账号
      - DRONE_UI_PASSWORD=8888 # Drone Runner 的 UI 用户密码
    volumes:
      - '/var/run/docker.sock:/var/run/docker.sock'
    depends_on:
      - server
```
