---
title: localStorage和sessionStorage的用法
date: 2017-09-04 15:28:12
tags: javascript
categories: programming
---


* localStorage:没有时间限制
* sessionStorage：针对一个session的数据存储，关闭浏览器即被清除。


#### localStorage属性 ####

不涉及到登录业务时采用此存储方式，有存储定有值。

	localStorage.setItem('openid','aaa');
	localStorage.getItem('openid');//aaa

API

	localStorage.getItem(‘key’,’val’) - 取得 
	localStorage.setItem(‘key’) - 设置 
	localStorage.removeItem(‘key’) - 移除 
	localStorage.key(0) - 取key值 
	localStorage.clear() - 清空

#### sessionStorage属性 ####

后台登录管理系统，必须从登录页面跳转实现，登录页面存储，后面页面取值。即实现登录功能。有存储重新打开无值。

##### 单个储存 #####

		sessionStorage.setItem('openid','aaa');
		sessionStorage.getItem('openid');//aaa

##### 多个变量对象储存 #####

[**ps：** 对象储存需要用JSON.stringify()方法转为json字符串，取出的时候需要用JSON.parse()
转为json对象(sessionStorage,localStorage)](https://77ya.github.io/2017/10/18/json/)


	 	var data = {
	       "url":"1233",
	       "age":2,
	       "sex":"女"
	     }
	     sessionStorage.setItem("mydata",JSON.stringify(data)); //json对象转为字符串对象
	    var mydata =  sessionStorage.getItem("mydata");
	     var result = JSON.parse(mydata)
	     console.log(result);

