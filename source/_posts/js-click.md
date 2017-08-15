---
title: 移动端实现类似hover事件
date: 2016-12-20 11:27:21
tags: [javascript,css]
---

### 移动端在点击按钮瞬间

	document.body.addEventListener('touchstart', function(){ 
	document.getElementsByClassName('searBtn')[0].style.background='#fff';
	});

### 移开按钮的瞬间
	document.body.addEventListener('touchend', function(){ 
	document.getElementsByClassName('searBtn')[0].style.background='#0089de';
	});

