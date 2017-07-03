---
title: 初识对象
date: 2016-12-17 15:20:49
tags: javascript
categories:
---
## 简单认识对象
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

<!-- more -->

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

##### in操作符，针对Object（对象操作），不是数组




# 对象、数组、函数简单了解

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
	//函数+参数
	function funcName(someFunc,someParam){
		return someFunc(someParam);
	}
	//函数sum()
	function sum(num){
		return num+3;
	}
	var result = funcName(sum,5);
	alert(result);//8

### 函数调用
JavaScript函数在定义时并不会去执行，只有我们在调用定义的函数时，它才会去执行。
四种方式调用函数，如下：

* 方法调用模式；
* 函数调用模式；
* 构造器调用模式；
* apply调用模式；

##### 方法调用模式
当函数被保存为对象的一个属性时，我们称它为一个方法。

	var myObj = {//对象字面量 （有疑问）
	    param1: 1,
	    param2: 2,
	    sum: function (){
	    //this关键字指代当前的对象
	    return this.result = this.param1 + this.param2; 
	    }
	}
	console.log(myObj.sum()); 
##### 函数调用模式
属于全局是调用，即通常通常的函数调用。
	//函数一
	var add = function(a,b){
	  return a + b;
	}
	add(1,2);
	//函数二
	function add(a,b){
	  return a + b;
	}
	add(1,2);
##### 构造器调用函数
将函数作为构造器的来使用的语法就是在函数调用前面加上new关键字。

	var add = function() {
	    this.name = "hello";
	    this.sum = function (a, b){
	        return a + b;
	    }
	}
	// 构造器调用模式
	var obj = new add(); //obj是一个对象
	document.write(obj.sum(1,2)) //==>3
##### apply调用模式
js中函数也是对象。call()和apply()用来间接的调用函数。称之为apply调用模式。

apply()方法让我们构建一个<font color=#ff0000 size=3>参数数组</font>传递给调用函数。它也允许我们选择this的值。apply()方法接收两个参数，第一个是要绑定给<font color=#ff0000 size=3>this的值</font>，第二个就是一个<font color=#ff0000 size=3>参数数组</font>。

语法：<font color=#ff0000 size=3>函数名.apply(对象，参数数组)；</font>

	//apply()方法
	var add = function (a, b) {
	    return a + b;
	}
	 
	add.apply(null,[1,2]);  //=>3

<font color=#0000ff size=3>有疑问：null改变无变化</font>

##### call()方法
call()方法和apply()方法类似，<font color=#ff0000 size=3>区别在第二参数不是一个数组是需要列举出来的</font>。上述代码用call方法实现。
	var add = function(a,b){
		return a + b;	
	}
	add.call(null,1,2)//=>3


