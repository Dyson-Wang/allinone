---
categories: [编程语言]
tags: [编程语言]
title: Java
date: '2022-09-05T12:53:22.789Z'
lastmod: '2024-05-08T11:18:59.105Z'
---

# Java

## 环境env

### 环境配置

`JAVA_HOME`
`C:\Program Files\Java\jdk1.8.0_131`

`Path`
`%JAVA_HOME%\bin;`

`CLASSPATH`
`.;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar;`

## grammar

### 关键字

- 访问控制
  - private 私有的
  - protected 受保护的
  - public 公共的
  - default 默认
- 类、方法和变量修饰符
  - abstract	声明抽象
  - class	类
  - extends	扩充、继承
  - final	最终值、不可改变的
  - implements	实现（接口）
  - interface	接口
  - native	本地、原生方法（非 Java 实现）
  - new	创建
  - static	静态
  - strictfp	严格浮点、精准浮点
  - synchronized	线程、同步
  - transient	短暂
  - volatile	易失

## 正则表达式

  - \s+ 匹配多个空格
  - . 匹配任意字符
  - \. 匹配.
  - \\ 匹配反斜杠
  - \d+ 多个数字
  - ()? 括号里的可选
  - /[0-9]+/ 匹配一次任意长度的数字
  - ^ 开头
  - $ 结尾
  - ?* 匹配一次或无数次
  - {n, m} 匹配至少n次，最多m次
  