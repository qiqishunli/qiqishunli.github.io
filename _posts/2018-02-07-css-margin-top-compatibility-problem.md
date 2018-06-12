---
layout: post
title: margin兼容之margin-top的传递问题
categories: css margin-top
description: css margin-top
key: wzyugh2018-03-16
keywords: css margin-top
---
两个盒子嵌套，如果给里面的盒子设置margin-top的话，这个margin-top会传递到外层盒子上，使得外层盒子具有margin-top 而里面盒子没有margin-top：

解决方案：

* 给外层盒子加 overflow:hidden; 属性
* 在某些情况下可以 设置内层盒子的 padding-top代替 margin-top
* 为外层盒子设置一个透明的上边框border-top:transparent 1px solid;
* 为外层盒子设置一个 padding-top: 1px;
* 为外层盒子设置 display: inline-block;
* 为外层盒子或者内层盒子设置position:absolute;