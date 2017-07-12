---
title:  深入理解JavaScript系列(1)：
date: 2017-07-12 21:43:32
tags:
categories:
---
##### window全局对象

每个JavaScript环境有一个全局对象，当你在任意的函数外面使用this的时候可以访问到。你创建的每一个全部变量都成了这个全局对象的属性

>window是浏览对象，要在浏览器下访问
 
global = 'hello';
console.log(global); //hello
console.log(window.global);  //hello
console.log(this.global);  //hello
console.log(window['global']);  //hello
