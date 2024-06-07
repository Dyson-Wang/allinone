---
categories: [编程语言]
tags: [编程语言]
title: JavaScript
date: '2022-09-05T12:52:19.715Z'
lastmod: '2024-05-08T11:14:42.016Z'
---

# JavaScript

## Basic

### `fetch`

`React`中的`fetch`是相对于`index.html`页面的路径，它返回一个可阅读流（Stream）`res`，调用`res.json()`方法，返回一个`Promise`对象，将流异步的转换为`json`字符串，这是为什么`fetch`有两个`.then()`函数的原因。
```
// 流->Promise->data
fetch('./data.json')
  .then(res => res.json())
  .then(data => { 
    dispatch({ 
      type: 'GET',
      num: Number(data[4])
    })
  })
```
