---
title: ajax增删改查
date: 2017-06-15 11:45:07
tags:
categories:
---

##### $.get()方法

$.get()方法通过http get请求从服务器上请求数据。

语法：$.get(url,[,data][,success][,dataType]);除url之外，所有属性可选。

* 网址：string; 请求的url地址

* 数据：PlainObject或String；发送到请求的服务器的普通对象或字符串

* 成功：function；回调函数；如果提供了dataType则必需，但可以使用null或jquery.noop作为占位符

* 数据类型：string；从服务器语气的数据类型。默认值：智能识别（xml，json，script，text，html）

		$.get({
			url:url，
			data:{usernumber:1}，
			success:function(data){
				console.log(data)
			}，
			dataType:json
		})

等价于

		$.ajax({
			type：'get',
			url:url，
			data:{usernumber:1}，
			success:function(data){
				console.log(data)
			}，
			dataType:json
		})

##### $.post()方法

$.post()方法通过 HTTP POST 请求从服务器上请求数据。

语法：$.post(url[,data][,success][,dataType]);

* 网址：string; 请求的url地址

* 数据：PlainObject或String；发送到请求的服务器的普通对象或字符串

* 成功：function；回调函数；如果提供了dataType则必需，但可以使用null或jquery.noop作为占位符

* 数据类型：string；从服务器语气的数据类型。默认值：智能识别（xml，json，script，text，html

		$.post({
			url:url,
			data:{usernumber:1}
			success:function(data){
				console.log(data)
			},
			dataType:json
		})

等价于

		$.ajax({
			type:'post',
			url:url,
			data:{usernumber:1}
			success:function(data){
				console.log(data)
			},
			dataType:json
		})


补充：
Ajax技术核心就是XMLHttpRequest对象。

Ajax技术的工作原理：可以分成3步

1.创建Ajax对象：var xhr = new XMLHttpRequest();

2.xhr 发送请求：xhr.open('get','test.html','true');

                          
	xhr.send();

3.xhr获取响应：

    xhr.onreadystatechange = function(){
    	if(xhr.readystate == 4){//请求的状态码
                               /*
                               0:请求还没有建立（open执行前）
                               1：请求建立了还没发送（执行了open）
                               2：请求正式发送（执行了send）
                               3：请求已受理，有部分数据可以用，但还没有处理完成
                               4：请求完全处理完成
          						alert(xhr.responseText);//返回的数据
                               }
                             }