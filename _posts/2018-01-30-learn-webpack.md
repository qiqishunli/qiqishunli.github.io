---
layout: post
title: webpack 学习笔记
categories: webpack
description: webpack的用法
key: wzyugh2018-03-16
keywords: webpack
---


## 开始
安装webpack

先全局安装
 
```
npm install webpack -g  
```      
然后本地安装，安装到node_modules并安装到了依赖列表里

```
npm install webpack --save-dev（开发依赖）
```


创建
index.html
entry.js


webpack ./entry.js bundle.js

- 模块依赖 webpack会分析入口文件，解析包依赖关系的各个文件
- 这些文件（模块）都打包到bundle.js文件中
- webpack会给每个模块分配一个唯一的id并通过这个id索引和访问模块
- 页面启动时先执行entry.js 代码，其他的模块会在require时依赖加载


## 加载css文件
安装loader：

```
npm install css-loader style-loader
```
- 首先style.css 也看成是一个模块
- css-loader来读取它
- style-loader 把它插入到页面中