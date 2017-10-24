---
title: 模拟菜单选中效果
date: 2017-10-23 14:17:40
tags: css选择器 html
categories: programming
---

之前写这种效果用的removeClaa和addClass，今天发现了一个更简洁的方法。直接上代码吧！

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



#### toggleClass() ####