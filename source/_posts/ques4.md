---
title: Object.prototype.toString.call()判断对象
date: 2018-03-22 13:10:57
tags: 工作问题
categories: programming
---

#### 判断数组还是对象 ####

	   function isobjarr(value){
	       if(Object.prototype.toString.call(value)=="[object Array]"){
	           console.log("数组");
	       }else if(Object.prototype.toString.call(value)=="[object Object]"){
	           console.log("对象");
	       }else{
	           console.log("都不是");
	       }
	   }


**ps：千万不能使用typeof来判断对象和数组，因为这两种类型都会返回"object"。**

<!-- more -->
 
#### 判断所有对象 ####

	console.log(Object.prototype.toString.call(123)) //[object Number]
	console.log(Object.prototype.toString.call('123')) //[object String]
	console.log(Object.prototype.toString.call(undefined)) //[object Undefined]
	console.log(Object.prototype.toString.call(true)) //[object Boolean]
	console.log(Object.prototype.toString.call({})) //[object Object]
	console.log(Object.prototype.toString.call([])) //[object Array]
	console.log(Object.prototype.toString.call(function(){})) //[object Function]

	
#### 判断是数组还是对象 ####