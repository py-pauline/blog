---
title: 关于JavaScript的疑难杂症
date: 2017-06-25 23:10:57
tags:
categories:
---
##### for……in声明

	var arr = new Array();
	arr[0] = 'tony';
	arr[1] = 'tom';
	arr[2] = 'lily';
	for(x in arr){
		console.log(x); // 0 1 2
		console.log(arr[x]); //tony tom lily
	}

##### sort()排序：改变原数组

>从字面上对数组排序

	var arr = new Array();
	arr[0] = 'tony';
	arr[1] = 'tom';
	arr[2] = 'aily';
	console.log(arr.sort()); //[ 'aily', 'tom', 'tony' ]

>从数值上进行排序

	function sortnum(a,b){
		var c = a-b;
		return c;
	}
	var arr = new Array();
	arr[0] = 20;
	arr[1] = 2;
	arr[2] = 88;
	console.log(arr.sort(sortnum)); //[ 2, 20, 88 ]

##### prototype 向模型函数添加属性

	function employee(name,job,born){
		this.name = name;
		this.job = job;
		this.born = born;
	}
	var bil = new employee('toby','dd','1994');
	employee.prototype.salary = null;
	bil.salary = 3333;
	console.log(bil.salary) //333


#### shift() 删除第一个元素，返回删除的元素
	
	var arr = new Array('lily','tony','daming','jack');
	var result = arr.shift();
	console.log(result); //lily

##### unshift（），向数组开头一个或更多元素，并返回新的长度，改变原数组

	var arr = new Array('lily','tony','daming','jack');
	
	var result = arr.unshift('lingling','emily');
	
	console.log(result); //6
	console.log(arr) //['lingling','emily','lily','tony','daming','jack']

##### pop（）删除末尾元素，返回删除的元素

	var arr = new Array('lily','tony','daming');
	var result = arr.pop();
	console.log(result); //daming

##### push（）向末尾增加元素，返回新数组长度
	
	var arr = new Array('lily','tony','daming');
	var result = arr.push('jone');
	console.log(result); //4

##### reverse() 颠倒数组中的元素顺序

	var arr = new Array('lily','tony','daming','jack');
	var result = arr.reverse();
	console.log(result); //[ 'jack', 'daming', 'tony', 'lily' ]

##### slice(start,end) 返回新数组，不会修改原数组

start:必须，第几个开始，若是-3，后面3个。

end：下标，第二个数必须大于第一个参数。

	var arr = new Array('lily','tony','daming','jack');
	var result = arr.slice(1,2);
	console.log(result); //['tony']

##### splice() 从数组中添加/删除项目，返回被删除的项目，改变数组

数组下标1开始，数1个，再添加tonyyy
	var arr = new Array('lily','tony','daming','jack');
	
	var result = arr.splice(1,1,'tonyyy');
	
	console.log(result); //['tony']
	console.log(arr) //['lily','tonyyy','daming','jack']

##### toString() 数组转化为字符串，并返回结果，不改变数组，与不加参数的join（）方法同义
##### pop（）删除末尾元素，返回删除的元素

	var arr = new Array('lily','tony','daming');
	var result = arr.pop();
	console.log(result); //daming

##### join（）指定的分隔符进行分割，默认用 ，分割

	var arr = new Array('lily','tony','daming');
	var result = arr.join();
	console.log(result); //lily,tony,daming

##### valueOf() 返回valueOf的原始值

<font color='#ff0000' size='5'>ES5中新增的Array方法</font>
[点击查看原文](http://www.zhangxinxu.com/wordpress/2013/04/es5%E6%96%B0%E5%A2%9E%E6%95%B0%E7%BB%84%E6%96%B9%E6%B3%95/#foreach)

##### forEach

>三个参数：（遍历数组的内容），（对应的数组索引），（数组本身）
		
		[].forEach(function(value, index, array) {
		    // ...
		});

>对比jQuery中$.each方法

		$.each([], function(index, value, array) {
		    // ...
		});

###### 第一个参数和第二个参数正好相反



	var arr = new Array('tony','lily','daming','jane');
	arr.forEach(console.log)

终端返回：
	
	tony 0 [ 'tony', 'lily', 'daming', 'jane' ]
	lily 1 [ 'tony', 'lily', 'daming', 'jane' ]
	daming 2 [ 'tony', 'lily', 'daming', 'jane' ]
	jane 3 [ 'tony', 'lily', 'daming', 'jane' ]





##### 
##### 
##### 
##### 
##### 

