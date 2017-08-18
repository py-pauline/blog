---
title: 移动端常用meta标签总结
date: 2016-12-28 14:41:22
tags: html
categories: programming
---
ios手机号码识别样式覆盖

	<meta name="format-detection" content="telephone=no" />


) <meta name="viewport" content="width=device-width; initial-scale=1.0; maximum-scale=1.0; user-scalable=0;" />   
 //强制让文档的宽度与设备的宽度保持1:1，   
 //文档初始化缩放比例是1:1，   
 //不允许用户点击屏幕放大浏览，    
//允许用户缩放到的最大比例，   
 //尤其要注意的是content里多个属性的设置一定要用逗号+空格来隔开，如果不规范将不会起作用。其他属性有：width;height; initial-scale; minimum-scale; maximum-scale; user-scalable;
2) <meta name="apple-mobile-web-app-capable" content="yes" />    
 //iPhone私有标签，它表示：允许全屏模式浏览
3) <meta name="apple-mobile-web-app-status-bar-style" content="black" />    
//iPhone私有标签，它指定的iPhone中safari顶端的状态条的样式
4) <meta name="format-detection" content="telephone=no; email=no" />    //不识别邮件和不把数字识别为电话号码