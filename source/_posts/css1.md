---
title: input type="radio"自定义样式
date: 2016-12-21 11:08:57
tags: css
categories: programming
---
	input[type="radio"] {
	  display: inline-block;
	  background: url(../input.png) no-repeat left -115px;
	  width: 20px;
	  height: 21px;
	  background-size: 20px auto;
	  -webkit-appearance: none;
	  outline:none;
	  border:none;
	}
	input[type="radio"]:checked {
	  background: url(../input.png) no-repeat left -168px;
	  background-size: 20px auto;
	  outline:none;
	  border:none;
	}

图片素材链接：http://oibijaovc.bkt.clouddn.com/input.png
### 效果展示

![Aaron Swartz](http://oibijaovc.bkt.clouddn.com/input1.gif)