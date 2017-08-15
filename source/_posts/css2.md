---
title: 默认样式总结
date: 2016-12-28 15:57:31
tags: [css,html]
---
移动ios端有很多默认样式，可在全局样式中添加如下样式：
### 移动端
ios手机号识别样式覆盖

	通过添加Safari私有属性解决
	<meta name="format-detection" content="telephone=no" />
	

ios按钮默认为灰色

	-webkit-appearance: none;

<!--more-->

圆角

	button{ border-radius: 0; }
禁止textarea拖拽放大

	textarea {
	    resize: none;
	} 


ios点击时出现高光

	input:focus{
	    -webkit-tap-highlight-color:rgba(0,0,0,0);
	    -webkit-user-modify:read-write-plaintext-only;
	}
### pc端
chrome等浏览器文本框默认发光边框

	input:focus, textarea:focus {
	    outline: none;
	}





	