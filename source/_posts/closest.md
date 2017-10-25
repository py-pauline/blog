---
title: 模拟菜单选中效果
date: 2017-10-23 14:17:40
tags: css选择器 html
categories: programming
---
当被最接近的李彪元素或其子后代元素被点击时，会切换背景颜色，之前写这种效果用的removeClaa和addClass，今天发现了一个更简洁的方法。直接上代码吧！

	<style>
	    .pink{background-color: pink;}
	    li{margin-top:10px;}
	</style>
	<body>
	    <ul id="box">
	        <li>第一行</li>
	        <li>第二行</li>
	        <li>第三行</li>
	    </ul>
	    <script src="https://cdn.bootcss.com/jquery/3.2.1/jquery.min.js"></script>
	    <script>
	        //菜单点击标识 clisest从当前元素开始向上遍历
	        $(document).bind("click",function(e){
	            $(e.target).closest("li").toggleClass("pink");
	        })
	    </script>
	</body>

<!-- more -->

#### 效果预览 ####
![](http://oibijaovc.bkt.clouddn.com/QQ%E6%88%AA%E5%9B%BE20171024180956.png)

#### closest() ####

语法：.closest(selector，context)

selector:选择器
context:指定选择器匹配范围

用法：获得匹配选择器的第一个祖先元素，从当前元素开始沿DOM树向上

效果图

![](http://oibijaovc.bkt.clouddn.com/QQ%E6%88%AA%E5%9B%BE20171025110734.png)

#### toggleClass() ####

语法一：.toggleClass(class,switch);

class:必须，移除或添加的class类名，多个用空格分隔
switch：可选，布尔值

语法二：$(selector).toggleClass(function(index,class),switch)

示例：

html

	<style type="text/css">
	.listitem_1, .listitem_3{color:red;}
	.listitem_0, .listitem_2{color:blue;}
	</style>
	</head>
	
	<body>
	<h1 id="h1">This is a heading</h1>
	<ul>
	<li>Apple</li>
	<li>IBM</li>
	<li>Microsoft</li>
	<li>Google</li>
	</ul>
	<button class="btn1">添加或移除列表项的类</button>
	</body>
	</html>

js
	
	<script type="text/javascript">
	$(document).ready(function(){
	  $("button").click(function(){
	    $('ul li').toggleClass(function(){
	      return 'listitem_' + $(this).index();
	    });
	  });
	});
	</script>

![](http://oibijaovc.bkt.clouddn.com/QQ%E6%88%AA%E5%9B%BE20171024172804.png)