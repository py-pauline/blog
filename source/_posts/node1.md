---
title: node.js学习笔记一（创建第一个应用）
date: 2017-06-15 20:46:22
tags:
categories:
---
### 什么是node.js
node.js是运行在服务器端的JavaScript。Node.js 是一个基于Chrome JavaScript 运行时建立的一个平台。
Node.js是一个事件驱动I/O服务端JavaScript环境，基于Google的V8引擎，V8引擎执行Javascript的速度非常快，性能非常好。

### node.js 应用的组成
 1. 引入require模块：可以使用require指令来载入node.js模块；
 2. 创建服务器：服务器可以监听客户端的请求；
 3. 接受请请求与响应请求：客户端可以使用浏览器或终端发送Http请求，服务器接受请求后返回响应数据。

<!-- more -->

#### 创建node.js应用
1.引入require模块

	var http = require('http'); //使用require指令来载入http模块，并将实例化的http赋值给变量http
2.创建服务器

* http.createServer()
* listen方法绑定8888接口
* 通过request和response来接受和响应数据

	var http = require('http');

	http.createServer(function (request, response) {

	// 发送 HTTP 头部 
	// HTTP 状态值: 200 : OK
	// 内容类型: text/plain

	response.writeHead(200, {'Content-Type': 'text/plain'});
	
	// 发送响应数据 "Hello World"
	response.end('Hello World\n');

	}).listen(8888);
	
	//终端打印信息如下
	console.log('server running at http://127.0.0.1:8888');

3.node命令执行以上的代码

	F:\practice\web>node server.js
	server running at http://127.0.0.1:8888

浏览器访问http://127.0.0.1:8888，你会看到写着“hello world”的网页。

**分析Node.js的HTTP服务器**

* <font color="#FF7F50">第一行请求（require）Node.js自带的http模块，并且把它赋值给http变量。</font>
* <font color="#FF7F50">接下来调用http模块提供的函数：creatServer。这个函数会返回一个对象，这个对象有一个叫做listen的方法，这个方法有一个数值参数，指定这个HTTP服务号监听的端口号。</font>
