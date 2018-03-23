---
title: 问题汇总
date: 2018-03-22 13:10:57
tags: 问题汇总
categories: query
---
[ 
原文地址](http://obkoro1.com/2018/03/18/3%E6%9C%88%E5%88%9D%E4%B8%8A%E6%B5%B7%E5%89%8D%E7%AB%AF%E9%81%87%E5%88%B0%E7%AC%94%E8%AF%95%E9%A2%98%E9%9D%A2%E8%AF%95%E9%A2%98%E8%AE%B0%E5%BD%95/#more)

#### 跨域问题 ####
 浏览器为了安全实施的同源策略导致的，同源：两个URL的域名、协议、端口要完全相同

解决方案：

script标签jsonp跨域、nginx反向代理、nodejs中间件代理跨域、后端在头部信息设置安全域名


<!-- more -->
	
#### 定时器的执行顺序和机制 ####

因为js是单线程的，浏览器遇到setTimeout或者setInterval会先执行完当前的代码块,在此之前会把定时器推入浏览器的待执行事件队列里面,执行完当前代码才会执行定时器代码。


	 for(var i=0;i<10;i++){
      setTimeout(function(){
        console.log(i);
      },1000)
    }
    //打印出10個10

	 setTimeout(function(){
	     console.log("定时器");
	   },0)
	  console.log("先执行此条语句");

#### html中title属性和alt属性的区别 ####

	<img src="#" alt="alt信息" title="title信息"/>

图片不输出信息时：显示“alt信息“，鼠标放上去显示”title信息“


title属性可以用在除了base，basefont，head，html，meta，param，script和title之外的所有标签

title属性的主要功能是为了提示，比如一些链接本身未清楚表达链接的目的，此时就可以添加title属性

#### http状态码 ####
1xx：1开头的是信息状态码
2xx：2开头的是请求成功
3xx：3开头的是重定向
4xx：4开头的是客户端错误
5xx：5开头的是服务器错误