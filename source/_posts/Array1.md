---
title: 关于JavaScript的疑难杂症
date: 2017-06-25 23:10:57
tags:
categories:
---
### for……in声明
	var arr = new Array();
	arr[0] = 'tony';
	arr[1] = 'tom';
	arr[2] = 'lily';
	for(x in arr){
		console.log(x); // 0 1 2
		console.log(arr[x]); //tony tom lily
	}
### sort()排序
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




