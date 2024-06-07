---
categories: [框架与技术]
tags: [框架与技术]
title: React Notes
date: '2022-09-05T09:44:29.416Z'
lastmod: '2024-05-08T11:15:15.843Z'
---

# React Notes

## Basic

### root 组件

`ReactDOM.render()` 已不推荐使用，使用以下新方法
```
const root = ReactDOM.createRoot(DOMElement);  
root.render(<Component />);
```

## React项目

### webpack

```
npm install webpack webpack-cli --save-dev
```

- `entry`

  ```
  module.exports = {
    entry: {
      a2: 'dependingfile.js',
      b2: {
        dependOn: 'a2', // 当前入口所依赖的入口。它们必须在该入口被加载前被加载。
        filename: 'output.js' // 指定要输出的文件名称。
        import: './src/app.js', // 启动时需加载的模块。
        library: {},
        runtime: false, // runtime 和 dependOn 不应在同一个入口上同时使用
        publicPath: '',
      },
    },
  };
  ```

- `output`
  ```
  module.exports = {
    entry: {
      app: './src/app.js',
      search: './src/search.js',
    },
    output: {
      filename: '[name].js', // 使用占位符分别输出
      path: __dirname + '/dist',
    },
  };

  // 写入到硬盘：./dist/app.js, ./dist/search.js
  ```
- `loader`

  loader 从右到左（或从下到上）地取值(evaluate)/执行(execute)。在下面的示例中，从 sass-loader 开始执行，然后继续执行 css-loader，最后以 style-loader 为结束。

  ```
  module.exports = {
    module: {
      rules: [
        {
          test: /\.css$/,
          use: [
            { loader: 'style-loader' }, // 支持query参数
            {
              loader: 'css-loader',
              options: { // loader options
                modules: true
              }
            },
            { loader: 'sass-loader' }
          ]
        }
      ]
    }
  };
  ```
- `plugin`

  webpack 插件是一个具有 apply 方法的 JavaScript 对象。

  由于插件可以携带参数/选项，你必须在 webpack 配置中，向 plugins 属性传入一个 new 实例。
  ```
  const HtmlWebpackPlugin = require('html-webpack-plugin');
  const webpack = require('webpack'); // 访问内置的插件
  const path = require('path');

  module.exports = {
    ...
    plugins: [
      new webpack.ProgressPlugin(), // 内置插件实例
      new HtmlWebpackPlugin({ template: './src/index.html' }),
    ],
  };
  ```
  ProgressPlugin 用于自定义编译过程中的进度报告，HtmlWebpackPlugin 将生成一个 HTML 文件，并在其中使用 script 引入一个名为 my-first-webpack.bundle.js 的 JS 文件。

### babel

```
npm install babel-loader @babel/core @babel/preset-env @babel/preset-react --save-dev
npm install @babel/polyfill --save-dev
npm install @babel/runtime @babel/plugin-transform-runtime @babel/plugin-syntax-dynamic-import --save-dev
```
以上插件中babel-loader主要用于高级语法转换成低级语法，它是webpack的一个loader，用来预处理文件；@babel/core是babel的核心模块，提供转换的API；@babel/preset-env可以根据配置的目标浏览器或者运行环境将ES5+代码自动转换为ES5代码，也是babel的一个模块；@babel/preset-react用来解析React中的JSX语法，同样也是babel的模块。以上的模块写法中，前面加有”@”符号的写法是babel 7.0+版本的写法，具体的可以查看babel官网。

### less/sass css预处理器

```
npm install stylus stylus-loader less less-loader sass-loader node-sass css-loader style-loader --save-dev
```

css-loader主要的作用是解析css文件, 像@import等动态语法；style-loader主要的作用是解析的css文件渲染到html的style标签内；stylus、less、sass是CSS的常见预处理器；stylus-loader、less-loader、sass-loader主要是将其对应的语法转换成css语法。

```
npm install postcss-loader autoprefixer --save-dev
```
但是如果我们使用CSS3的一些新特性时，需要为不同的浏览器在CSS代码中添加不同的前缀，在开发中手动添加太麻烦，所以我们可以通过postcss来自动添加各种浏览器前缀。

```
npm install file-loader url-loader --save-dev
```
解析字体、图片等静态资源

```
npm install mini-css-extract-plugin --save-dev
```
压缩css文件，不针对less

```
npm install webpack-dev-server --save-dev
npm install html-webpack-plugin --save-dev
```
代码热更新
