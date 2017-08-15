---
title: 深入理解JavaScript系列:作用域链（scope chain）
date: 2017-07-04 21:37:54
tags: javascript
categories: javascript
---

[
点击查看原文](http://www.cnblogs.com/TomXu/archive/2012/01/18/2312463.html)

## 作用域链
>如果要简要的描述并展示其重点，那么作用域链大多数与内部函数相关。

ECMAScript 允许创建内部函数，我们甚至能从父函数中返回这些函数。
	
	var x = 10;
 
	function foo() { 
	  var y = 20; 
	  function bar() {
	    alert(x + y);
	  } 
	  return bar; 
	}
	 
	foo()(); // 30

这样，很明显每个上下文拥有自己的变量对象：对于全局上下文，它是全局对象自身；对于函数，它是活动对象。
>作用域链正是内部上下文所有变量对象（包括父变量对象）的列表。此链用来变量查询。即在上面的例子中，“bar”上下文的作用域链包括AO(bar)、AO(foo)和VO(global)。

###### 在进入上下文时函数声明放到变量/活动（VO/AO）对象中
	
	var x = 10;
	 
	function foo() {
	  var y = 20;
	  alert(x + y);
	}
	 
	foo(); // 30

>[[scope]]是所有父变量对象的层级链，处于当前函数上下文之上，在函数创建时存于其中。

注意这重要的一点－－[[scope]]在函数创建时被存储－－静态（不变的），永远永远，直至函数销毁。即：函数可以永不调用，但[[scope]]属性已经写入，并存储在函数对象中。

	var x = 10;
	 
	function foo() {
	  alert(x);
	}
	 
	(function () {
	  var x = 20;
	  foo(); // 10, but not 20
	})();