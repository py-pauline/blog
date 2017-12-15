---
title: new Date 在ios上的兼容
date: 2017-12-11 13:10:57
tags: 工作问题
categories: programming
---

new Date（），开发中经常用到的方法，今天在做微信服务号开发发现居然在ios上有兼容问题，在此记录下解决方案。

<!-- more -->
	
	var time = new Date("2017-12-05 17:53:42");

但是在ios中new Date方法并不不支持“-”连接日期，所以该用“/”替换。
	
	var time = new Date("2017-12-05 17:53:42".replace(/-/g, "/"));

