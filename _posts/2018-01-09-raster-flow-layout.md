---
layout: post
title: 栅格化流式布局
categories: 栅格化 
description: 前端栅格化流式布局介绍
key: wzyugh2018-03-16
keywords: 流式布局 栅格化
---

# 使用方法

```
javascript { .theme-peacock }
\<div class="c-row">
    \<div class="c-span3">3n</div>
    \<div class="c-span9">9n</div>
\</div>
\<div class="c-row">
    \<div class="c-span6">6n</div>
    \<div class="c-span6">6n</div>
\</div>"
```

全局样式组件，可直接使用。

12列栅格系统，由父元素"c-row"及子元素"c-span*"嵌套组成。一个c-row代表一行，若需多行布局，请包裹多个c-row。

c-row中子元素的盒模型模式为"box-sizing:border-box;"。单独使用"c-row"没有意义，必须结合"c-span"且"c-span"必须为"c-row"的直接子元素。"c-span*"之间的间距采用padding控制，在设置背景色、边框时需设置在子元素上。

### 特殊的1px间隔的栅格系统

```
javascript { .theme-peacock }
\<div class="c-row c-row-tight">
    <div class="c-span4">4n</div>
    <div class="c-span4">4n</div>
    <div class="c-span4">4n</div>
</div>
```
在需要使用1px间隔的栅格父容器"c-row"上并列添加"c-row-tight"类，即可实现子元素按照1px间隔排布。

注意：该布局目前仅允许在三联章、四联章图片显示中使用，请勿滥用。

## 栅格系统中边框使用技巧
由于"c-row"含有负边距，当栅格系统"c-row"外需要使用边线时，可在"c-row"外再嵌套一层，例如：

```
javascript { .theme-peacock }
\<div class="c-line-top">
    <div class="c-row">
        <div class="c-span3">3n</div>
        <div class="c-span9">9n</div>
    </div>
</div>
```

由于"c-span"盒模型为border-box，当栅格系统"c-span"内需要使用边线时，可在"c-span*"内再嵌套一层，例如：


```
javascript { .theme-peacock }

\<div class="c-row">
    <div class="c-span6">
        <p class="c-line-bottom">6n</p>
    </div>
    <div class="c-span6">
        <p class="c-line-bottom">6n</p>
    </div>
</div>
```
### 浮动盒模型父元素

```
javascript { .theme-peacock }
\<div class="c-flexbox" style="text-align:center;">
    <div style="width:40%; -webkit-box-flex:1; -webkit-flex:1 1 auto; background:#ccc;">左-可变宽度</div>
    <div style="-webkit-box-flex:0; -webkit-flex:none; background:red;">中-内容宽度</div>
    <div style="width:40%; -webkit-box-flex:1; -webkit-flex:1 1 auto; background:#ccc;">右-可变宽度</div>
</div>
```
栅格系统采用浮动盒模型实现，由于该模型在wise开发中经常使用，提供统一的浮动盒模型父元素c-flexbox方便自定义使用。

注意：子容器情况比较多变，不提供公共样式，自定义样式时需注意包含-webkit-box-flex; -webkit-flex; 分别对应新旧两版盒模型且保证前后顺序。

## 示例代码
### 流式栅格系统

```
javascript { .theme-peacock }
\<div class="c-container">
    <div class="c-row">
        <div class="c-span3">3n</div>
        <div class="c-span9">9n</div>
    </div>
    <div class="c-row">
        <div class="c-span3">3n</div>
        <div class="c-span3">3n</div>
        <div class="c-span3">3n</div>
    </div>
    <div class="c-row">
        <div class="c-span6">6n</div>
        <div class="c-span6">6n</div>
    </div>
</div>
```
### 在栅格系统中使用边线
```
javascript { .theme-peacock }
\<div class="c-container">
    <div class="c-line-top">
        <div class="c-row">
            <div class="c-span3">3n</div>
            <div class="c-span9">9n</div>
        </div>
        <div class="c-row">
            <div class="c-span12">12n-边线贯穿顶部并与栅格对齐</div>
        </div>
    </div>

    <div class="c-row">
        <div class="c-span6">
            <p class="c-line-bottom">6n-下有边线</p>
        </div>
        <div class="c-span6">
            <p class="c-line-bottom">6n-下有边线</p>
        </div>
    </div>
</div>
```
### 特殊的间隔缩紧的栅格样式

```
javascript { .theme-peacock }
\<div class="c-container">
    <div class="c-row c-row-tight">
        <div class="c-span4"><p style="background:#ccc">4n</p></div>
        <div class="c-span4"><p style="background:#ccc">4n</p></div>
        <div class="c-span4"><p style="background:#ccc">4n</p></div>
    </div>
    <div class="c-row c-row-tight">
        <div class="c-span3"><p style="background:#ccc">3n</p></div>
        <div class="c-span3"><p style="background:#ccc">3n</p></div>
        <div class="c-span3"><p style="background:#ccc">3n</p></div>
        <div class="c-span3"><p style="background:#ccc">3n</p></div>
    </div>
</div>
```
### 自定义浮动盒模型

```
javascript { .theme-peacock }
\<div class="c-container">
    <div class="c-flexbox" style="text-align:center;">
        <div style="width:40%; -webkit-box-flex:1; -webkit-flex:1 1 auto; background:#ccc;">左-可变宽度</div>
        <div style="-webkit-box-flex:0; -webkit-flex:none; background:red;">中-内容宽度</div>
        <div style="width:40%; -webkit-box-flex:1; -webkit-flex:1 1 auto; background:#ccc;">右-可变宽度</div>
    </div>
</div>
```










