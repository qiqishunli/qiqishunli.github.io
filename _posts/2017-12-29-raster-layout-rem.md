---
layout: post
title: 栅格化布局rem布局
categories: rem 
description: 前端栅格化布局rem布局介绍
key: wzyugh2018-03-16
keywords: rem 栅格化
---

# REM简介
rem是相对于html元素font-size的一个单位。如果html上定义了font-size:100px;，则无论在任何地方都是1rem = 100px。这个大小不会受到父元素的影响。

我们统一针对不同宽度的设备修改基准font-size值。当遇到需要适应页面大小的元素，都可以使用rem为单位来定义。

# 基准规则
|屏幕宽度 | font-size | 典型设备 |
|---| | |
| 大于360px | 100px | ip6/6s/6p |
| 不大于360px | ip4/5/5s | Nexus 5|
定义页面基准font-size为100px，当屏幕宽度小于等于360px时，基准值变为90px，即所有使用rem单位的元素按0.9倍缩小。

注意：由于rem单位依赖html基础font-size值，因此严禁以任何形式重写html font样式行为！！

关于为何使用100px
设置100px主要为了方便计算，理论上任意值均可。

PC chrome有12px最小字号限制，若使用10px会造成pc调试困难从而带来不必要的麻烦。

# 如何使用
```
 { .c-rem-box {
    width: 2.5rem;          /* = 250px */
    font-size: 0.14rem;     /* = 14px */
    line-height: 0.3rem;    /* = 30px */
    text-indent: 2em;
    padding: 0.1rem;        /* = 10px */
    background: #ccc;
    box-shadow: 0 0 0.1rem #000;
}}
```
所有需要使用距离单位的地方均可使用rem单位。根据UE图标记的px宽度，按照1rem = 100px换算使用即可。
