---
categories: [框架与技术]
tags: [框架与技术]
title: React-Router
date: '2022-09-11T03:10:45.010Z'
lastmod: '2024-05-08T11:15:15.866Z'
---

# React-Router

React Router 中有三种类型的组件： router components, route matching components，和 navigation components。

## React-router-dom

### router components

#### `<Router>`
Router 是所有路由组件共用的底层接口。通常，我们的应用程序将使用其中一个高级路由器代替：

- `<BrowserRouter>`
- `<HashRouter>`
- `<MemoryRouter>`
- `<NativeRouter>`
- `<StaticRouter>`

最常见的使用底层的 <Router> 的情形就是用来与 Redux 或者 Mobx 之类的状态管理库的定制的 history 保持同步。注意不是说使用状态管理库就必须使用 React Router ，它仅用作于深度集成。

#### `<BrowserRouter>`
#### `<HashRouter>`
#### `<MemoryRouter>`
#### `<NativeRouter>`
#### `<StaticRouter>`

### route matching components

#### `Route`

没有路径总会匹配挂载，如果不需要请用`Switch`

以下所有的三种渲染方法都会通过三个相同的Route属性
- match
- location
- history

