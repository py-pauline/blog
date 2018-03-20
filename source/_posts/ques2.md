---
title: tab下内容随菜单切换
date: 2018-03-11 13:10:57
tags: 工作问题
categories: programming
---
目的效果：菜单切换，内容也切换，页面跳转会让用户感受到卡顿，所以这种效果通常是在一个页面通过控制目标元素的显示与隐藏来实现的。

#### 效果图预览

![](http://oibijaovc.bkt.clouddn.com/tabchange.gif)

<!-- more -->
	
#### 代码如下：

	<body>
	    <style>
	        ul {height: 50px;padding: 0;}
	        .tab1 {float: left;text-align: center;}
	        .tab2 {float: right;text-align: center;}
	        .tab {width: 50%;list-style: none;padding: 0;}
	        .bottomline {border-bottom: 3px solid #008cee;}
	        .hide {display: none;}
	    </style>
	    <div class="wrapper">
	        <div class="maincontent">
	            <ul id="ul">
	                <li class="tab1 bottomline tab">标签一</li>
	                <li class="tab2 tab">标签二</li>
	            </ul>
	            <div class="thecontent">
	                <div class="content">
	                    这是页面一
	                </div>
	                <div class="content hide">
	                    这是页面二
	                </div>
	            </div>
	
	        </div>
	    </div>
	    <script src="../../plugin/jquery/jquery-3.2.0.js"></script>
	    <script>
	        $("#ul li").click(function () {
	            $(this).addClass("bottomline").siblings().removeClass("bottomline");
	            console.log($(this));
	            $(".thecontent div").eq($(this).index()).removeClass("hide").siblings().addClass("hide");
	        })
	    </script>
	</body>