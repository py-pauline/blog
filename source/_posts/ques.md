---
title: 前端疑难杂症集锦
date: 2017-07-06 22:52:12
tags:
categories: 
---

记录各种奇奇怪怪的问题

<!-- more -->

### 循环label语句
[地址：](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Loops_and_iteration)

一个 [label](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/label) 提供了一个可以让你引用到您程序别的位置的标识符。

### 原型的使用方式

一般写法

	var a = 8;
	b=9;
	function add(x,y){
		return x+y;
	}
	function subtract(x,y){
		return x-y;
	}
	console.log(add(a,b))
	
	var fn1=function(arg1,arg2){
		this.arg1 = arg1;
		this.arg2 = arg2;
	};

原型方式一

	var fn1=function(arg1,arg2){
		this.arg1 = arg1;
		this.arg2 = arg2;
	};
	fn1.prototype = {
		add:function(x,y){
			return x+y;
		},
		subtract:function(x,y){
			return x-y;
		}
	}
	var newfn = new fn1();
	console.log(newfn.add(2,3))

原型方式二

	var fn1=function(arg1,arg2){
		this.arg1 = arg1;
		this.arg2 = arg2;
	};
	fn1.prototype = function(){
		add:function(x,y){
			return x+y;
		},
		subtract:function(x,y){
			return x-y;
		}
	}();
	var newfn = new fn1();
	console.log(newfn.add(2,3))

hasOwnProperty：判断一个对象是否包含自定义属性而不是原型链上的属性，

	Object.prototype.bar = 1; //表示object的原型对象，所有对象都继承他的属性和方法
	var foo= {moo:2};
	for(var i in foo){
		if(foo.hasOwnProperty(i)){
			console.log(i)
		}
	}