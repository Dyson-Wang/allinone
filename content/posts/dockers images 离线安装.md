---
categories: [服务器搭建日志]
tags: [服务器搭建日志]
title: dockers images 离线安装
date: '2024-05-09T00:29:47.410Z'
lastmod: '2024-05-09T02:10:09.044Z'
---

# dockers images 离线安装

## 导出

```
docker save 'shreshthtuli/cifar100_semantic:latest' -o cifar100_semantic.tar
docker save 'shreshthtuli/cifar100_layer:latest' -o cifar100_layer.tar
docker save 'shreshthtuli/fashionmnist_semantic:latest' -o fashionmnist_semantic.tar
docker save 'shreshthtuli/fashionmnist_layer:latest' -o fashionmnist_layer.tar
docker save 'shreshthtuli/mnist_semantic:latest' -o mnist_semantic.tar
docker save 'shreshthtuli/mnist_layer:latest' -o mnist_layer.tar

docker save -o shreshthtuli.tar 'shreshthtuli/cifar100_semantic:latest' 'shreshthtuli/cifar100_layer:latest' 'shreshthtuli/fashionmnist_semantic:latest' 'shreshthtuli/fashionmnist_layer:latest' 'shreshthtuli/mnist_semantic:latest' 'shreshthtuli/mnist_layer:latest'
```

## 导入

```
# 本地复制到远程
# 拷贝文件
scp local_file remote_username@remote_ip:remote_folder 
scp local_file remote_username@remote_ip:remote_file 
scp local_file remote_ip:remote_folder 
scp local_file remote_ip:remote_file 
# 拷贝目录
scp -r local_folder remote_username@remote_ip:remote_folder 
scp -r local_folder remote_ip:remote_folder 
# 远程复制到本地
scp root@www.runoob.com:/home/root/others/music /home/space/music/1.mp3 
scp -r root@www.runoob.com:/home/root/others/ /home/space/music/
# 防火墙指定端口
-P 4588
```

```
docker load -i *.tar
docker tag imagesID <tag:ver>
```
