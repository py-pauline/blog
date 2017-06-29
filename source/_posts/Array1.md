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
##### sort()排序
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

##### join（）指定的分隔符进行分割，默认用 ，分割

	var arr = new Array('lily','tony','daming');
	var result = arr.join();
	console.log(result); //lily,tony,daming

##### pop（）删除末尾元素，返回删除的元素

	var arr = new Array('lily','tony','daming');
	var result = arr.pop();
	console.log(result); //daming

#### shift() 删除第一个元素，返回删除的元素
	
	var arr = new Array('lily','tony','daming','jack');
	var result = arr.shift();
	console.log(result); //lily

##### push（）向末尾增加元素，返回新数组长度
	
	var arr = new Array('lily','tony','daming');
	var result = arr.push('jone');
	console.log(result); //4

##### reverse() 颠倒数组中的元素顺序

	var arr = new Array('lily','tony','daming','jack');
	var result = arr.reverse();
	console.log(result); //[ 'jack', 'daming', 'tony', 'lily' ]

##### slice() 返回新数组，不会修改原数组




