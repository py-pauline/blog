---
title: javascript学习笔记（二）
date: 2016-12-17 15:20:49
tags: javascript
categories:
---
### 对象
##### 创建对象

使用new构造函数
	
	var obj = new Object(); 
	obj.name = "MangGuo"; 
	obj.age = 25;

使用对象字面量表示法

	var obj = {
	    name : "MangGuo", //name是属性名，"MangGuo"是值
	    age : 25
	}

##### 访问属性

	var cat = {
	    "name": "tom",
	    "sex": "man",
	    "color": "yellow"
	}
	var name1 = cat.name; //通过点操作符来访问对象属性
	var name2 = cat["name"]; //通过中括号操作符来访问对象属性
##### 删除属性

	var cat = {
	    "name": "tom",
	    "sex": "man",
	    "color": "yellow"
	}
	delete cat.name;
	cat.sex = undefined;
	cat.color = null;
	alert("name属性是否存在：" + cat.hasOwnProperty("name"));  //false
	alert("sex属性是否存在：" + cat.hasOwnProperty("sex"));  //true
	alert("color属性是否存在：" + cat.hasOwnProperty("color"));  //true

PS: hasOwnProperty函数是判断某个属性是否存在于某个对象当中。
##### 原型
	var sum = {
	  name: "汇智网",
	  type: "加法"
	}
	Object.prototype.add = function(){
	  alert("原型对象的方法");
	}
	sum.add(); // =>原型对象的方法
##### 属性遍历

	var cat = {
	    "name": "小白",
	    "type": "汇智网",
	    "eat": function(){
	    alert("吃老鼠");
	    }
	}
	Object.prototype.color = "白色";
	var name;
	for(name in cat){
	    document.write(cat[name] + "\n");
	}

### 数组
	var arr = new Array();
	var arr = ["cat", "dog", "mouse"];

### 函数

函数声明

	alert(sum(3,11));  //弹出14
	function sum(x, y) {
	    return x + y;
	}
 函数表达式

	alert(sum(3,11);   // unexpected identifier 意外标识符错误
	var sum = function (x, y) {
	    return x + y;
	}
ps：因为在执行到函数所在的语句之前，变量sum 中不会保存有对函数的引用；而且由于第一行代码就会报错，也不会执行到下一行。

### 作为值的函数