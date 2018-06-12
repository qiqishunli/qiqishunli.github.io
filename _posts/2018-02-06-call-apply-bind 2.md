---
layout: post
title: call apply bind的区别
categories: call apply bind
description: call apply bind
key: wzyugh2018-03-16
keywords: call apply bind
---

在js中，所有函数在执行的时候都会默认传入两个参数，一个是this，一个是arguments。在默认情况下this都是指向当前调用函数的对象的。但是有时候我们需要改变this的指向，也就是说使函数可以被其他指定的对象来调用。这时候我们就需要用到call，apply和bind了。

### call，apply和bind方法的来历

在js中所有的函数都是Function的实例，而且对于Function来说，它的原型即Function.prototype中含有很多东西，其中call,apply和bind方法就是Function原型中的方法，所以根据原型的规则，所有的函数都可以使用原型中属性和方法，所以来说，对于所有的函数都可以使用call，apply和bind方法。简单一句话：call，apply和bind都是Function原型中的方法，而所有的函数都是Function的实例。

call，apply和bind的核心功能就是改变this的指向

### call,apply和bind的区别

它们在功能上是没有区别的，都是改变this的指向，它们的区别主要是在于方法的实现形式和参数传递上的不同：

* ①：函数.call(对象,arg1,arg2....)
* ②：函数.apply(对象，[arg1,arg2,...])
* ③：var ss=函数.bind(对象,arg1,arg2,....)

结合代码来理解：

```
function fn(a,b,c,d){
　　console.log(a,b,c,d);
}
//call
fn.call(null,1,2,3);
//apply
fn.apply(null,[1,2,3]);
//bind
var f = fn.bind(null,1,2,3);
f(4);

结果如下：
1 2 3 undefined
1 2 3 undefined
1 2 3 4
```