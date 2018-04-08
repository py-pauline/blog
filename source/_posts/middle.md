---
title: css布局——水平垂直居中
date: 2018-04-08 10:11:28
tags: css 
categories:
---



#### 方法一：display：table和display：table-cell实现多行文本垂直居中 ####

单行文本垂直居中我们会用line-height，而多行文本垂直水平居中刚如何实现呢？

效果如下

![](http://oibijaovc.bkt.clouddn.com/QQ%E6%88%AA%E5%9B%BE20180408112812.png)


css+html


	//父容器和子容器定义样式

	.box {
	    display: table;
	    height: 300px;
	    padding: 15px;
	    background-color: paleturquoise;
	    width: 100%;
    }

    .introduce {
        display: table-cell;
        vertical-align: middle;
    }

	//html结构

 	<div class='box'>
        <div class='introduce'>
            <p>你来自哪里</p>
            <p>你来自哪里</p>
            <p>你来自哪里</p>
        </div>
    </div>


####  ####