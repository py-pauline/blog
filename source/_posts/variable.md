---
title: 深入理解JavaScript系列：变量对象（Variable Object）
date: 2017-07-03 10:31:18
tags: JavaScript
categories: programming
---

[点击查看原文](http://www.cnblogs.com/TomXu/archive/2012/01/16/2309728.html)

##### 枚举对象用hasOwnProperty过滤原型

方法一：

	var obj = {
		name:'tony',
		age:'12'
	}
	for(i in obj){
		if(obj.hasOwnProperty(i)){  //过滤原型链中继承的属性
			console.log(obj[i]) //tony,12
		}
	}

<!-- more -->
方法二：

	var obj = {
		name:'tony',
		age:'12'
	}
	var i,
		hasown = Object.prototype.hasOwnProperty;
	for(i in obj){
		if(hasown.call(obj,i)){  //过滤
			console.log(i) // name age
		}
	}

### 变量与执行上下文的关系

	var a = 1;
	(function(){
		var b=11;
	})();
	console.log(a) //1
	console.log(b) //b is not defined

>for循环并不能创建一个局部的上下文


	for (var i in {name:'彭迎',age:'11'}){
		// console.log(i) // name age
	}
	console.log(i) //age    循环已结束，但变量i依然在当前作用域

### 数据申明

>如果变量与执行上下文相关，那变量自己应该知道它的数据存储在哪里，并且知道如何访问。这种机制称为变量对象(variable object)。缩写VO。

##### 变量对象定义

变量对象（VO）是一个与执行上下文相关的特殊对象，它储存着在上下文中声明的以下内容：

* 变量（var,变量声明）
* 函数声明
* 函数的形参

##### 上下文类型一：全局上下文中的变量对象(有疑问)

>全局对象(Global object) 是在进入任何执行上下文之前就已经创建了的对象；
这个对象只存在一份，它的属性在程序中任何地方都可以访问，全局对象的生命周期终止于程序退出那一刻。
		

		var a = new String('test');
		 
		alert(a); // 直接访问，在VO(globalContext)里找到："test"
		 
		alert(window['a']); // 间接通过global访问：global === VO(globalContext): "test"
		alert(a === this.a); // true
		 
		var aKey = 'a';
		alert(window[aKey]); // 间接通过动态属性名称访问："test"

##### 上下文类型二：函数上下文中的变量对象

>在函数执行上下文中，VO是不能直接访问的，此时由活动对象(activation object,缩写为AO)扮演VO的角色。

###### VO(functionContext) === AO;

>活动对象是在进入函数上下文时刻被创建的，它通过函数的arguments属性初始化。arguments属性的值是Arguments对象
>Arguments对象是活动对象的一个属性，它包括如下属性：

* callee — 指向当前函数的引用
* length — 真正传递的参数个数
* properties-indexes (字符串类型的整数) 属性的值就是函数的参数值(按参数列表从左到右排列)。 properties-indexes内部元素的个数等于arguments.length. properties-indexes 的值和实际传递进来的参数之间是共享的。


##### 处理上下文代码的2个阶段

>执行上下文的代码被分成两个基本的阶段处理，变量对象的修改变化与这两个阶段紧密相关

* 进入执行上下文
* 执行代码


##### 关于变量

>任何时候，变量只能通过使用var关键字才能声明

