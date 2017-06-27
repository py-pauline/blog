---
title: 深入理解JavaScript系列：闭包（closures）
date: 2017-06-27 10:42:00
tags: javascript
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
	  console.log('funArg');
	});

>funarg的实际参数其实是传递给exampleFunc的匿名函数。


	(function functionValued() {
	  return function () {
	    console.log('returned function is called');
	  };
	})()();

>函数不仅可以作为参数，还可以作为返回值。这类以函数为返回值的函数称为带函数值的函数（functions with functional value or function valued functions）。

* 第一类函数或第一类对象（作为正常数据存在：函数传递、接受函数式参数、以函数值返回）
* 自应用函数（接受自己作为参数的函数）


		(function selfApplicative(funArg) {
		//逻辑运算符优先级比关系运算符高
		  if (funArg && funArg === selfApplicative) {
		    console.log('self-applicative');
		    return;//条件满足，跳出条件所在的方法
		  }
		
		  selfApplicative(selfApplicative);
		
		})();


* 自复制函数（以自己为返回值的元素）

		 (function selfReplicative() {
		  return selfReplicative;
		})();

>自由变量是指在函数中使用的，但既不是函数参数也不是函数的局部变量（对于innnerFn函数来讲，localVar是自由变量）

	function testFn() {
	
	  var localVar = 10;
	
	  function innerFn(innerParam) {
	    console.log(innerParam + localVar);
	  }
	
	  return innerFn;
	}
	
	var someFn = testFn();
	someFn(20); // 30
# 动态作用域和静态作用域是什么、伪代码、call、

#### 闭包

>闭包是代码块和创建该代码块的上下文数据的结合