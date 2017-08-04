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

##### defer属性：延迟脚本执行，只支持IE浏览器


##### js基本数据类型（6种原始类型+Object）:String Boolean Number Null Undefined Symbol和Object

##### js获取select下拉框的值：

	<form action="">
		<select name="" id="">
			<option value="1">1</option>
			<option value="1" selected="selected">2</option>
			<option value="1">3</option>
			<option value="1">4</option>
			<option value="1">5</option>
		</select>
	</form>
	<script>
		//javascript
		var obj = document.getElementsByTagName('select')[0]; //select
		console.log(obj);
		var index = obj.selectedIndex;//属性可设置或返回下拉列表中被选选项的索引号。
		console.log(index)
		var text = obj.options[index].text; // 选中文本
		var value = obj.options[index].value; // 选中值

		//jquery	
		var obj = $('select');
		var text = obj.find('option:selected').text();
		var value = obj.find('option:selected').val();
	</script>

##### 解释语言的特性：非独立、效率低

解释性语言和编译性语言的定义：
计算机不能直接理解高级语言，只能直接理解机器语言，所以必须要把高级语言翻译成机器语言，计算机才能执行高级语言编写的程序。
翻译的方式有两种，一个是编译，一个是解释。两种方式只是翻译的时间不同。

解释性语言的定义：
解释性语言的程序不需要编译，在运行程序的时候才翻译，每个语句都是执行的时候才翻译。这样解释性语言每执行一次就需要逐行翻译一次，效率比较低。
现代解释性语言通常把源程序编译成中间代码，然后用解释器把中间代码一条条翻译成目标机器代码，一条条执行。

编译性语言的定义：
编译性语言写的程序在被执行之前，需要一个专门的编译过程，把程序编译成为机器语言的文件，比如exe文件，以后要运行的话就不用重新翻译了，直接使用编译的结果就行了（exe文件），因为翻译只做了一次，运行时不需要翻译，所以编译型语言的程序执行效率高。

非独立：JavaScript语言依赖执行环境，对于客户端来说是浏览器，对于服务端来说是node。
效率低：执行前不需要编译，执行时才编译，因此效率低。

###### angularjs1中的服务实质上是：单例对象

###### var obj=/ /;声明obj为正则对象

###### 跨域：通过iframe设置document.domain可以实现跨域

###### javascript 标准事件模型：事件捕获-事件处理-事件冒泡

###### call和apply

call与apply都属于Function.prototype的一个方法，所以每个function实例都有call、apply属性

apply传入的是一个参数数组，也就是将多个参数组合成为一个数组传入

call传入的则是直接的参数列表。call 方法可将一个函数的对象上下文从初始的上下文改变为由 thisObj 指定的新对象。

##### 浏览器内核

mozilla内核 (firefox,flock等)     -moz
                                                      webkit内核(safari,chrome等)   -webkit
                                                      opera内核(opera浏览器)         -o
                                                      trident内核(ie浏览器)               -ms
