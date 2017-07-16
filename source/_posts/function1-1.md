---
title:  牛客网做题知识点总结
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


##### setTimeout

		console.log(1);
		setTimeout(function(){
			console.log(2);
		},0);
		console.log(3);
		
		上述代码的执行结果：1，3，2；

>回调时，被回调的函数会被放在event loop里，等待线程里的任务执行完后才执行event loop里的代码。 因此，上述代码会先把线程里的执行完后，再执行event loop里的setTimeout函数.。

##### 载入数据

A.ajax() 方法通过 HTTP 请求加载远程数据。$.ajax(opts);opts为json格式，常见参数url、type、data等。

B.load() 方法从服务器加载数据，并把返回的数据放入被选元素中。$(selector).load(URL,data,callback);
必需的 URL 参数规定您希望加载的 URL。
可选的 data 参数规定与请求一同发送的查询字符串键/值对集合。
可选的 callback 参数是 load() 方法完成后所执行的函数名称。

C.$.get() 方法通过 HTTP GET 请求从服务器上请求数据。
$.get(URL,callback);
必需的 URL 参数规定您希望请求的 URL。
可选的 callback 参数是请求成功后所执行的函数名。

D.getScript() 方法通过 HTTP GET 请求载入并执行 JavaScript 文件。
jQuery.getScript(url,success(response,status));

##### javascript
javascript 语言特性中，有很多方面和我们接触的其他编程语言不太一样，比如说，javascript语言实现继承机制的核心就是<b>prototype</b>，而不是Java语言那样的类式继承。Javascript 解析引擎在读取一个Object的属性的值时，会沿着<b>原型链</b> 向上寻找，如果最终没有找到，则该属性值为 <b>undefined</b> ； 如果最终找到该属性的值，则返回结果。与这个过程不同的是，当javascript解析引擎执行“给一个Object的某个属性赋值”的时候，如果当前Object存在该属性，则改写该属性的值，如果当前的Object本身并不存在该属性，则赋值该属性的值 。