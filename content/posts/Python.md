---
categories: [编程语言]
tags: [编程语言]
title: Python
date: '2022-09-05T12:52:31.119Z'
lastmod: '2024-05-08T11:19:18.880Z'
---

# Python

## linux 安装

### 源码编译
```
curl -o [filename] [url]
tar -[z]xvf *.tar.xz
/usr/local/src/
yum -y install zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel gcc make

build-essential zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev libssl-dev libreadline-dev libffi-dev
```

### 依赖项

```
gcc zlib zlib1g-dev bz2
```

## API Server

### flask 框架， 安装flask-cors
```
pip install flask
pip install flask-cors
```

```
from flask import Flask, request
from flask_cors import CORS, cross_origin

app = Flask(__name__)
CORS(app, supports_credentials=True) // 全局跨域

@app.route('/api/dyson')
# @cross_origin(supports_credentials=True) // 部分路由跨域
def index():
    return {'name': 'dyson', 'msg': 'Hello Python!'}

if __name__ == '__main__':
    app.run()
```
