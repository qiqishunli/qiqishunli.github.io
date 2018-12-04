---
layout: post
title: javascript 中有关于回调函数的详细深入解读
categories: callback function
description: callback function
key: wzyugh2018-03-16
keywords: callback function
---
## 什么是回调函数
> 把一个函数当做实参值传递给函数的形参变量（或者传递给函数，通过arguments获取），在另外一个函数中把传递的函数执行，这种机制叫做回调函数机制
> 反思在某一个函数的某一个阶段需要完成某一件事情（而这件事情是不确定的）都可以利用回调函数机制，把需要处理的事情当做值传递进来

```
	function fn(num, callBack) {
		//=>callBack:传递进来的回调函数
		typeof callBack === 'function' ? callBack():null;
		//callBack && callBack(); //=>这种方式默认就是，要不然不传参数，传递的话参数值肯定是函数
	}
	fn(10);
	fn(20, function(){
		//=>此处的匿名函数就是给callBack传递的值
	})
	
```
> 既然我们把函数作为值窜地给fn了，此时在fn中我们可以尽情的操作传递的函数
> 1、我们可以在fn中把回调函数执行0-N次
> 2、我们还可以给回调函数传递参数
> 3、我们还可以把回调函数中的this进行修改
> 4、我们还可以接收回调函数执行的时候返回的值

## 例子
执行fn可以实现任意数求和，把求出的和传递给回调函数

```
function fn(callBack) {
	var argNum = Array.prototype.slice.call(arguments, 1);
	total = eval(argNum.join('+'));
	callBack && callBack(total);
}
fn(function (result){
	console.log(result);
},10,20,30);
```
## 都有哪些方法都是依托回调函数来完成的

```
var ary = [12，23，34];
ary.sort(function(a,b){
	//->a:当前项
	//->b:后一项
	return a-b;//返回一个大于零的值，a和b的位置进行交换	
});

ary.forEach(function(iem,index,input){
	//->item:当前遍历的这一项
	//->index：当前遍历这一项的索引
	//->input：原始遍历的数组
	/-> forEach 每当循环遍历的数组中的某一项，都户把传递的回调函数执行一次（不见执行还把遍历的这一项的值传递给回调函数）
});
```
map遍历数组中的每一项，原有数组不变，返回的结果是修改后的新数组（map相对于forEach来说，增加了对原有项的修改）
```
var newAry = ary.map(function(item,index,input) {
	return item*10;//=>回调函数中返回的是啥，相当于把当前遍历这一项修改为啥（回调函数汇总不写return，默认返回的是undefined）
});
```