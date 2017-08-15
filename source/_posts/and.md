---
title: js中逻辑运算符：与、且
date: 2017-07-18 21:27:02
tags: javascript
categories: programming
---

逻辑运算符通常用于布尔型（逻辑）值；这种情况，它们返回一个布尔型值。然而，&&和||运算符实际上返回一个指定操作数的值，因此这些运算符也用于非布尔型，它们返回一个非布尔型值。

<!-- more -->

##### 短路计算

true || (anything)  短路计算的结果为 true

false && (anything)  短路计算的结果为false

##### 或（代表符号：||）

其中一个条件满足即可。

例1：

	var a=4399<0 || typeof('aaa')  //语句一返回false，故执行语句二
	console.log(a)  //string  

例2：
	
	var a=4399>0 || typeof('aaa')  语句一返回true，满足其一
	console.log(a)  //true
	
>概括为：true停 false向后

		o1=true || true       // t || t 结果为 true
		o2=false || true      // f || t 结果为 true
		o3=true || false      // t || f 结果为 true
		o4=false || (3 == 4)  // f || f 结果为 false
		o5="Cat" || "Dog"     // t || t 结果为 Cat
		o6=false || "Cat"     // f || t 结果为 Cat
		o7="Cat" || false     // t || f 结果为 Cat

##### 且（代表符号：&&）

>概括为：false停 true向后
		
		a1=true && true       // t && t 结果为 true
		a2=true && false      // t && f 结果为 false
		a3=false && true      // f && t 结果为 false
		a4=false && (3 == 4)  // f && f 结果为 false
		a5="Cat" && "Dog"     // t && t 结果为 Dog
		a6=false && "Cat"     // f && t 结果为 false
		a7="Cat" && false     // t && f 结果为 false


##### 布尔值中以下类型返回false
	
	Boolean(undefined) // false
	
	Boolean(null) // false 
	
	Boolean(0) // false 
	
	Boolean(NaN) // false 
	
	Boolean('') // false

	Boolean(false) // false

##### Number中默认转换为0

	Number()
	Number(0)
	Number('')
	Number('0')
	Number(false)
	Number(null)
	Number([])
	Number([0])