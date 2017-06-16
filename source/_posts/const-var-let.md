---
title: js中const，var，let申明变量的区别
date: 2017-06-16 15:32:58
tags:
categories:
---
文档参考：[http://www.cnblogs.com/ksl666/](http://www.cnblogs.com/ksl666/)

1.const定义的变量不可以修改，而且必须初始化。
	
	const b = 2;	//正确
	//const b;	//错误，必须初始化
	console.log('函数外const定义b'+b);//有输入出值
	b = 5;
	console.log('函数外修改cons定义的b'+b)//无法输出

2.var定义的变量可以修改，如果不初始化会数车undefined，不会报错。
 
	var a = 1;
	// var a;//不会报错
	console.log('函数外var定义a：' + a);//可以输出a=1
	function change(){
	a = 4;
	console.log('函数内var定义a：' + a);
	} 
	change();//可以输出a=4
	console.log('函数调用后var定义a为函数内部修改值：' + a);//可以输出a=4
	//若函数不调用，输出的结果为：a=1;
		
3.let是块级作用域，函数内部使用let定义后，对函数外部无影响。

	let c = 3;
	console.log('函数外let定义c：' + c);//输出c=3
	function change(){
	let c = 6;
	console.log('函数内let定义c：' + c);
	} 
	change();//输出c=6
	console.log('函数调用后let定义c不受函数内部定义影响：' + c);//输出c=3
	//若函数不调用，输出结果为：c=3;