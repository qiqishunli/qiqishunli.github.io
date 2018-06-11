---
layout: post
title: css 小技巧总结一
categories: css
description: css小技巧总结
keywords: css
---

## 一、CSS实现长宽等比例的div

```
	.img-box{
		position: relative;
		width: 20%;
		height: 0;
		padding-bottom: 15%;
		overflow: hidden;
	}
	.img-box img{
		position: absolute;
		top: 0;
		right: 0;
		bottom: 0;
		left: 0;
	}
```
## 二、绘制三角形

```
.demo {
      width: 0;
      height: 0;
      border-left: 50px solid transparent;
      border-right: 50px solid transparent;
      border-bottom: 50px solid red;
      border-top: 50px transparent solid;
    }
```



