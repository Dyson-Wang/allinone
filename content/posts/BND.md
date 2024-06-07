---
categories: [个人笔记]
tags: [个人笔记]
title: BND
date: '2023-04-17T12:18:09.901Z'
lastmod: '2024-05-08T11:16:12.572Z'
---

# BND 

设每个用户下每个命名空间，可以单独配置一个数据库用于所建云函数的链接。

### 新建函数

API种类
1、数据库交互
2、静态资源上传与请求
3、函数内运算响应

沙箱逃逸

vm
```
const vm = require('vm');
vm.runInNewContext('this.constructor.constructor("return process")().exit()');
console.log('Never gets executed.');
```
vm2
```
const {VM} = require('vm2');
new VM().run('this.constructor.constructor("return process")().exit()');
// Throws ReferenceError: process is not defined
```

# API
## func部分

### 调用函数(GET方法)

**GET** */faas/:id*

**return**

```
{
  //标准返回对象
}
```

### 调用函数(POST方法)

**POST** */faas/:id*

```
{
  //示例对象
}
```

**return**

```
{
  //标准返回对象
}
```

## backend部分

### 添加函数

**POST** */addfunc*

```
{
  user-token,
  codeStr:String, //代码字符串
  method:String, //函数方法
  objScan:Object, //输入实例对象
  comment:String, //函数功能备注
  maxruntime
}
```

**return**

```
{
  status,
  message,
}
```

### 请求函数列表

#### 用户下全部函数

**GET** */funclist*

```
user-token
```

**return**

```
{
  funcarray:Array[{
      functionid,
      createTime,
      invokeTimes,
      namespaceid,
      master,
      ...
    }]
}
```

#### 命名空间下全部函数

**GET** */funclist/:namespaceid*

```
user-token
```

**return**

```
{
  funcarray:Array[{
      functionid,
      createTime,
      invokeTimes,
      namespaceid,
      master,
      ...
    }]
}
```
