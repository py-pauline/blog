---
title: node.js学习笔记四
date: 2017-06-20 10:36:11
tags:
categories:
---
### 回调函数
补充说明：

	Math.sqrt(2);//求2的平方根

node.js异步编程的直接体现就是回调。阻塞是按顺序执行的，二非阻塞是不需要按顺序的，所以如果需要处理回调函数的参数，我们就需要写在回调函数内。
异步执行代码（非阻塞）

<!--more-->

	var fs = require("fs");
	fs.readFile('../../others/input.txt',function(err,data){
		if(err){
			return console.error(err);
		};
		console.log(data.toString());
	})
	console.log('程序执行结束');
终端执行结果

![](http://oibijaovc.bkt.clouddn.com/%E5%BC%82%E6%AD%A5.png)

### 事件循环

### EventEmitter
### Buffer（缓冲区）
### Stream（流）
