---
title: 模板引擎系列：artTemplate
date: 2017-07-04 09:57:54
tags: javascript模板引擎
categories:
---

# art-template 

[原文查看](https://aui.github.io/art-template/)

## 介绍

art-template采用作用域预声明的技术来优化模板渲染速度。

##### 模板

###### 两种模板语法

* 标准语法（更容易读写）

		{{if user}}
		   <h2>{{user.name}}</h2>
		{{/if}}

<!-- more -->

* 原始语法（强大的逻辑处理能力）：兼容EJS、Underscore、loDash
		
		<% if (user) { %>
		  <h2><%= user.name %></h2>
		<% } %>

##### 渲染模板

	var template = require('art-template');
	var html = template(__dirname + '/tpl-user.art', {
	    user: {
	        name: 'aui'
	    }
	});

## 安装

* 安装nodeJs
* 安装模块插件
 * Webpack: art-template-loader
 * Express: express-art-template
 * Koa: koa-art-template

## 语法

* 标准语法


  	{{value}}
    {{data.key}}
    {{data['key']}}
    {{a ? b : c}}
    {{a || b}}
    {{a+b}}

* 原始语法


	<%= value %>
	<%= data.key %>
	<%= data['key'] %>
	<%= a ? b : c %>
	<%= a || b %>
	<%= a + b %>

>不懂

	{{$data['user list']}}
	模板一级特殊变量可以使用 $data 加下标的方式访问

##### 条件

* js中

		//a=1等同于value、v1
		 if(a=1){
		   ……
		 }else if(a=2){
		   ……
		 }

* 标准

		{{if value}} ... {{/if}}
		{{if v1}} ... {{else if v2}} ... {{/if}}

* 原始

	
		<% if (value) { %> ... <% } %>
		<% if (v1) { %> ... <% } else if (v2) { %> ... <% } %>

##### 循环


* js

		for(var i=0;i<$("p").length);i++{
		  ……
		}

* jQuery

		//index:下标  self：this,$(self)改变遍历元素样式
		 $('p').each(function(index,self){
		  ……
		 })

* 标准


		{{each target}}
		    {{$index}} {{$value}}
		{{/each}}

* 原始

>target 支持 array 与 object 的迭代，其默认值为 $data。
>
>$value 与 $index 可以自定义：{{each target val key}}。

		<% for(var i = 0; i < target.length; i++){ %>
		    <%= i %> <%= target[i] %>
		<% } %>

##### 变量

* 标准

		{{set temp = data.sub.content}}

* 原始

		<% var temp = data.sub.content; %>

##### 模板继承

* 标准

		{{extend './layout.art'}}
		{{block 'head'}} ... {{/block}}

* 原始

		<% extend('./layout.art') %>
		<% block('head', function(){ %> ... <% }) %>


##### 子模板

* 标准

		{{include './header.art'}}
		{{include './header.art' data}}

* 原始

		<% include('./header.art') %>
		<% include('./header.art', data) %>

##### 过滤器

>注册过滤器：过滤器函数第一个参数接受目标值。


		template.defaults.imports.dateFormat = function(date, format){/*[code..]*/};
		template.defaults.imports.timestamp = function(value){return value * 1000};

* 标准

		{{date | timestamp | dateFormat 'yyyy-MM-dd hh:mm:ss'}}

{{value | filter}} 过滤器语法类似管道操作符，它的上一个输出作为下一个输入。

* 原始

		<%= $imports.dateFormat($imports.timestamp(date), 'yyyy-MM-dd hh:mm:ss') %>

## 调试 template.defaults.debug

art-template 内建调试器，能够捕获到语法与运行错误，并且支持自定义的语法。在 NodeJS 中调试模式会根据环境变量自动开启：process.env.NODE_ENV !== 'production'

>设置 template.defaults.debug=true 后，等同于：


		{
		    "cache": false,
		    "minimize": false,
		    "compileDebug": true
		}

## 模板变量 

###### 内置变量清单

* $data 传入模板的数据
* $imports 外部导入的变量以及全局变量
* print 字符串输出函数
* include 子模板载入函数
* extend 模板继承模板导入函数
* block 模板块声明函数