---
title: ES6
date: 2017-08-28 21:27:02
tags: ES6
categories: programming
---
#### ES6申明变量的6种方法 ####

ES5只有两种申明变量的方法：var命令、function命令
ES6添加了4种方法：let、const、import、class

<!-- more -->

#### let和const ####

let所声明的变量，只在let命令所在的代码块内有效。

	{
	  let a = 10;
	  var b = 1;
	}
	
	a // ReferenceError: a is not defined.
	b // 1


const声明一个只读的常量。一旦声明，常量的值就不能改变。

	//报错
    const a =11;
	a=33;
	

for循环特点：设置循环变量的那部分是一个父作用域，而循环体内部是一个单独自作用域。

    for(let i = 0;i<3;i++){
		let i =2;
		console.log(i) // 2 2 2
	}

输出3次2，说明函数内部的变量i和循环变量i不在同一个作用域，有单独作用域。

#### 数组的解构赋值 ####
 ES6允许按照一定模式，从数组和对象中提取值，对变量进行赋值，这被称为结构。

    let a = 1;
	let b = 3;
	let c = 4;
	//ES6写法
	let[a,b,c] = [1,3,4]

一些例子
	
	let [foo, [[bar], baz]] = [1, [[2], 3]];
	foo // 1
	bar // 2
	baz // 3
	
	let [ , , third] = ["foo", "bar", "baz"];
	third // "baz"
	
	let [x, , y] = [1, 2, 3];
	x // 1
	y // 3
	
	let [head, ...tail] = [1, 2, 3, 4];
	head // 1
	tail // [2, 3, 4]
	
	let [x, y, ...z] = ['a'];
	x // "a"
	y // undefined
	z // []

#### 对象的解构赋值 ####
	
	对象的解构与数组有一个重要的不同。数组的元素是按次序排列的，变量的取值由他的位置决定；而对象的属性没有次序，变量必须与属性同名，才能取到正确的值。	

	let { foo, bar } = { foo: "aaa", bar: "bbb" };
	foo // "aaa"
	bar // "bbb"

这实际说明，对象的解构赋值是下面的简写形式

	let { foo: foo, bar: bar } = { foo: "aaa", bar: "bbb" };

对象名与属性名不一致的情况下

    let {foo:result} = {foo:'aaa',bar:'bbbb'}
	console.log(result) //aa
	console.log(foo); //not define

#### repeat() ####

返回一个新字符串，表示将原字符串重复n次。