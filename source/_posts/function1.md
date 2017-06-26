---
title: 深入理解JavaScript系列：函数（function）
date: 2017-06-26 16:56:16
tags:
categories:
---
[查看原文](http://www.cnblogs.com/TomXu/archive/2012/01/30/2326372.html)
#### JavaScript中三种函数类型
### 函数申明（缩写为FD）

* 有一个特定的名称
* 在源码中的位置：要么处于程序级（Program level），要么处于其它函数的主体（FunctionBody）中
* 在进入上下文阶段创建
* 影响变量对象
* 以下面的方式声明
		
		//1）直接在全局上下文中申明
		exampleFunc();
		function exampleFunc(){
			//2)或者在一个函数的函数体内
			function innerFd(){};
		}


### 函数表达式 （缩写为FE）

>补充：表达式的定义：表达式 是一组可以计算出一个数值的有效的代码的集合。

每一个合法的表达式都能计算成某个值，但从概念上讲，有两种类型的表达式：有副作用的（比如赋值）和单纯计算求值的。

* 在源码中须出现在表达式的位置
* 有可选的名称
* 不会影响变量对象
* 在代码执行阶段创建
	
		//1)赋值申明
		var foo = function(){
		
		};
		foo();//执行此匿名函数

		//2)拥有可选名称
		var foo = function foos(){
		
		}
		//在外部：foo访问，函数内部（递归调用）：_foo;
		//FE总是处在表达式的位置
		// 圆括号（分组操作符）内只能是表达式
		(function foo() {});
		 
		// 在数组初始化器内只能是表达式
		[function bar() {}];
		 
		// 逗号也只能操作表达式
		1, function baz() {};
>逗号操作符的说明
>
	// 注意是1,后面的声明
	1, function () {
	  alert('anonymous function is called');
	}();
	 
	// 或者这个
	!function () {
	  alert('ECMAScript');
	}();
 
>我有疑问,为什么是匿名函数

		function foo(callback) {
		  callback();
		}
		 
		foo(function bar() {
		  alert('foo.bar');
		});
		 
		foo(function baz() {
		  alert('foo.baz');
		});
等同于
		var foo = function () {
		  alert('foo');
		};
		 
		foo();

条件语句进行创建FE

	var foo = 10;
	var bar = (foo % 2 == 0
	  ? function () { console.log(0); }
	  : function () { console.log(1); }
	);
	bar(); //0

### 函数构造器创建的函数


