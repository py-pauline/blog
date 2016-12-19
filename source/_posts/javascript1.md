---
title: javascript学习笔记（一）
date: 2016-12-13 20:51:53
tags: javascript
categories:
---
### 弹出框

##### 警告框（alert）

	alert("hello")

警告窗口有一个确定按钮，点击确定会继续执行后面的代码。	

##### 确认选择（confirm）

	if(confirm("请选择？")==true){
	    document.write("您选了确定");
	}else{
	    document.write("您选了取消");
	}
 在消息对话框中要显示的文本，返回的是布尔值。当点击“确定”按钮时，会返回true，点击“取消”按钮时，返回的是false。

##### 提示（prompt）
语法：prompt(str1, str2);
参数说明：
str1：要显示在消息对话框中的文本，不能修改
str2：文本框中的内容，可以修改

	var myName = prompt("输入您的名字");
	if(myName != null && myName != ''){
	    document.write("welcome to " + myName);
	}else{
	    document.write("welcome to my friend.");
	}

点击确定按钮，文本框中的内容将作为函数返回值，点击取消按钮将返回null。

##### 打开新页面

在html页面中，有时我们需要跳转到新的页面中。这是时候就用到了open()。

语法：window.open(URL, 窗口名称);
参数说明：

URL：可选,打开窗口的网址或路径。如果省略了这个参数，或者它的值是空字符串，那么新窗口就不会显示任何文档。

窗口名称：可选,该字符串是一个由逗号分隔的特征列表，声明了被打开窗口的名称。可以是"_top"、"_blank"、"_selft"、"_parent"等。

	function open_win() {
	     window.open("http://www.baidu.com","_blank");
	}
	open_win();

* _blank 在新窗口显示目标网页
* _selft 在当前窗口显示目标网页
* _parent 框架网页中当前整个窗口位置显示目标网页
* _top 框架网页中在上部窗口中显示目标网页

### break和continue语句

##### break语句用于跳出循环

	for (var i=0;i<10;i++) {
	  if (i==3) {
	    break;
	  }
	  document.write("i=" + i );//i=0i=1i=2
	}
	
##### continue语句
	for (var i=0;i<10;i++) {
	  if (i==3) {
	    continue; //跳过了值 3
	  }
	  document.write("i=" + i );//i=0i=1i=2i=4i=5i=6i=7i=8i=9
	}

### 该变HTML

	<html>
	<body>
	 
	<p id="p1">Hello World!</p>
	 
	    <script>
	        document.getElementById("p1").innerHTML="New text!";
	    </script>
	</body>
	</html>

### 数据类型
基础类型：Number、String、Boolean、Null、Undefined

对象类型：object（对象类型Object包括：Array、Function、Date...）

### 转义字符

![Aaron Swartz](blog/source/img/js_esc.PNG)