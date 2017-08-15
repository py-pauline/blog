---
title: node.js学习笔记四
date: 2017-06-20 10:36:11
tags: nodejs
categories: programming
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
	
	// 创建事件处理程序（函数赋给了connectHandler）
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

执行结果

 >$node main.js
 >
 >连接成功
 >
 >数据接收成功
 >
 >程序执行完毕

## EventEmitter
events模块只提供了一个对象：events.EventEmitter核心是事件触发与事件监听器功能封装

	var events = require('events'); 
	var emitter = new events.EventEmitter(); 
	emitter.on('someEvent', function(arg1, arg2) { 
		console.log('listener1', arg1,arg2); 
	}); 
	emitter.on('someEvent', function(arg1, arg2) { 
		console.log('listener2', arg1,arg2); 
	}); 
	emitter.emit('someEvent', 'arg1参数','arg2参数'); 
>node event.js
>
>listener1 arg1 参数 arg2 参数 
>
>listener2 arg1 参数 arg2 参数

### EventEmitter提供了多个属性
* on函数用于绑定事件函数


	>// 语法：on(event,listener)
	server.on('connection',function(stream){
		console.log('someone connection');
	})
	
* emit属性用于触发一个事件  [ >>更多属性](http://www.runoob.com/nodejs/nodejs-event.html)



	>按参数的顺序执行每个监听器，如果事件有注册监听返回 true，否则返回 false。
	//语法：emit(event, [arg1], [arg2], [...])
### 继承EventEmitter

大多数时候我们不会直接使用 EventEmitter，而是在对象中继承它。包括 fs、net、 http 在内的，只要是支持事件响应的核心模块都是 EventEmitter 的子类。
为什么要这样做呢？原因有两点：
首先，具有某个实体功能的对象实现事件符合语义， 事件的监听和发射应该是一个对象的方法。
其次 JavaScript 的对象机制是基于原型的，支持 部分多重继承，继承 EventEmitter 不会打乱对象原有的继承关系。

	var events = require('events');
	var emitter  = new events.EventEmitter();

## Buffer（缓冲区）
### 在nodejs中，专门定义了Buffer类，用来创建一个专门存放二进制的缓存区

>创建缓存var buf = var Buffer('256')-写入缓存区 buf.write('写入进来的')-从缓存区读取数据 buf.toString()

## Stream（流）

