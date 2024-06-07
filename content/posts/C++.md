---
categories: [编程语言]
tags: [编程语言]
title: C++
date: '2022-09-05T12:50:32.984Z'
lastmod: '2024-05-08T11:14:41.906Z'
---

# C++

## 封装 encapsulation 继承 多态性

### 
```
a.cpp 类definition
a.h   头文件declaration
a.ii  预处理后的代码文件 a.h + a.cpp
a.o   目标代码
a.out 可执行程序
a.s   汇编代码
```

### 条件编译

```
#ifndef _如果未定义_ 常用于重复引用 多次声明定义（类）
#define 
... 标准头文件结构
#endif
```

cpp 编译
g++ --save-temps 保留中间文件 -c 只编译 -D 定义变量
  -m32 以32位编译 -Wall
  

