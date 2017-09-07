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

#### sessionStorage属性 ####

后台登录管理系统，必须从登录页面跳转实现，登录页面存储，后面页面取值。即实现登录功能。有存储重新打开无值。

	sessionStorage.setItem('openid','aaa');
	sessionStorage.getItem('openid');//aaa
