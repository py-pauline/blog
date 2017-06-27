---
title: 深入理解JavaScript系列：闭包（closures）
date: 2017-06-27 10:42:00
tags:
categories:
---
原文链接：http://www.cnblogs.com/TomXu/archive/2012/01/31/2330252.html

>补充：基本类型和引用类型

#### 基本数据类型

ES6 引入了一种新的原始数据类型 Symbol，表示独一无二的值。它是 JavaScript 语言的第七种数据类型，前六种是：Undefined、Null、布尔值（Boolean）、字符串（String）、数值（Number）、对象（Object）。
###### typeof：检测一个变量是不是最基本的数据类型

	a = 666;
	typeof a;    // number 

###### 约定：基本数据类型与原始数据类型等意。

#### 引用类型

除过上面的 6 种基本数据类型外，剩下的就是引用类型了，统称为 Object 类型。细分的话，有：Object 类型、Array 类型、Date 类型、RegExp 类型、Function 类型 等。


函数即是数据，函数可以赋值给变量，可以当参数传递给其他函数，可以从函数里返回。

	//高阶函数或函数式函数或者偏数理或操作符
	function exampleFunc(funArg) {
	  funArg();
	}
	
	exampleFunc(function () {
	  alert('funArg');
	});

>funarg的实际参数其实是传递给exampleFunc的匿名函数。


	(function functionValued() {
	  return function () {
	    alert('returned function is called');
	  };
	})()();

>函数不仅可以作为参数，还可以作为返回值。这类以函数为返回值的函数称为带函数值的函数（functions with functional value or function valued functions）。

######