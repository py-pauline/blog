---
title: margin，padding百分比
date: 2017-08-14 11:35:54
tags: css
categories: programming
---

对于前端的html，css自我感觉基础知识掌握的还可以，最近在牛客网网做题，深受打击，html可不能小瞧它呀！这不，稍不注意就踩着坑了。

回归正题：当margin，padding的值是百分比时，值得依据都是相对最近的父级块级元素的**宽度**。

**注意：是宽度 宽度 宽度！！！** 重要的事说3遍。

<!-- more -->

实践出真知，chrome浏览器调试的：

css+html代码

    <style type="text/css">
    	.demo{width:500px; height:400px;border:1px #f00 solid;background:pink;}
    	.demo a{width:200px;height:200px;display:block;margin-top:10%;padding-top:10%;margin-left:10%;padding-left:10%;background:#ffa000;}
    </style>
    <div class="demo">
    	<a href="javascript:;"></a>
    </div>

js代码

    <script type="text/javascript">
     	var childmt = $('a').css('margin-top'); //50
     	var childml = $('a').css('margin-left'); //50
     	var childpt = $('a').css('padding-top'); //50
     	var childpl = $('a').css('padding-left'); //50
    </script>

    

