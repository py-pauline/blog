---
title: node.js学习笔记四
date: 2017-06-20 10:36:11
tags:
categories:
---
# node.js回调函数、事件循环、EventEmitter、Buffer（缓冲区）、Stream（流）
## 回调函数
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

## 事件循环
事件驱动模型
![](http://oibijaovc.bkt.clouddn.com/%E4%BA%8B%E4%BB%B6%E9%A9%B1%E5%8A%A8%E7%A8%8B%E5%BA%8F.png)
通过实例化EventEmitter类来绑定和监听事件
>有疑问：绑定事件和触发事件的优先级

	// 引入 events 模块
	var events = require('events');
	// 创建 eventEmitter 对象
	var eventEmitter = new events.EventEmitter();
	
	// 创建事件处理程序
	var connectHandler = function connected() {
	   console.log('连接成功。');
	  
	// 触发 data_received 事件 
	   eventEmitter.emit('data_received');
	}
	
	// 绑定 connection 事件处理程序
	eventEmitter.on('connection', connectHandler);
	 
	// 使用匿名函数绑定 data_received 事件
	eventEmitter.on('data_received', function(){
	   console.log('数据接收成功。');
	});
	
	// 触发 connection 事件 
	eventEmitter.emit('connection');
	
	console.log("程序执行完毕。");

## EventEmitter
核心是事件触发与事件监听器功能封装

## Buffer（缓冲区）
## Stream（流）
