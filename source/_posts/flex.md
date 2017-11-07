---
title: flex-弹性盒子模型
date: 2017-06-15 11:41:45
tags: css flex
categories: programming
---
#### 开始准备 ####
开始之前，头部需添加以下meta：

	<meta name="viewport" content="width=device-width, 
	initial-scale=1.0, maximum-scale=1.0, user-scalable=0">


**<font color="#ff7f50">注意，设为 Flex 布局以后，子元素的float、clear和vertical-align属性将失效。</font>**

#### flex属性介绍 ####
 
> 定义在flex弹性容器内 

	.box{
		display: -webkit-flex;
	    display: flex;
		flex-flow:row-reverse wrap;
		flex-direction:row-reverse;
		flex-wrap:wrap;
		align-content:center;
		align-items:center;
		justify-content:center;
	}

1. flex-flow
	
	复合属性，flex-direction、flex-wrap，子项元素的排列顺序、是否拆行或拆列

2. flex-direction

	子项元素方向，默认值是row
	
	row：水平显示

	row-reverse：水平相反的顺序

	column：垂直显示

	column-reverse：垂直相反顺序显示

	initial：设置为默认值

	inherit：从父元素继承该属性

<!-- more -->


3. flex-wrap

	是否拆行或拆列，默认值是nowrap
	
	nowrap：默认值，不拆行或不拆列

	wrap：必要的时候拆行或拆列

	wrap-reverse：必要的时候拆行或拆列，但以相反的顺序

	initial：设置为默认值

	inherit：从父元素继承

4. align-content

	所有可用空间对齐容器内的各项（垂直方向）,默认值：stretch
	
	stretch；默认值，项目被拉伸以适应容器

	center：位于容器的中心

	flex-start：开头

	flex-end:结尾

	space-between：各行之间有空白

	space-around：各行之前、之间、之后都留有空白

5. align-items

	在纵轴上的对齐方式，（垂直方向）默认值：stretch;
	
	stretch:项目拉伸以适应容器，默认值
	
	center：容器中心
	
	flex-start：容器开头
	
	flex-end：容器结尾
	
	baseline：容器基线上



6. justify-content

	在横轴上的对齐方式，（水平方向），默认值：stretch
	
	flex-start：容器开头，默认值
	
	flex-end：结尾
	
	center：中心
	
	space-between：各行之间留有空白
	
	space-around：各行之前、之间、之后有空白



> 定义在flex子项 

	.items{ 
		flex:1;
		flex-grow:1;
		flex-shrink:1;
		flex-basis:20px;
		align-self:center;
	}

1. flex 

 	复合属性。设置模型对象的资源的子元素如何分配空间flex-grow、flex-shrink、flex-basis

2. flex-grow
 
	数字，扩展的量

3. flex-shrink

	数字，收缩的量

4. flex-basis

	长度单位或者百分比，规定初始长度

5. align-self

	子项单独在侧轴（垂直方向）的对齐方式。默认值，继承父容器：align-items属性的值，如果没有父容器则为stretch
	
	stretch：元素拉伸以适应容器
	
	center：中心
	
	flex-start：开头
	
	flex-end：结尾
	
	baseline：基线上
	

6. order

	盒模型对象的子元素出现顺序，默认值：0
	
	number：默认值为0，规定灵活项目的顺序


#### flex示例一 ####





	<style>
		.box{display:-webkit-flex;display:flex;justify-content:space-between;/* display: inline-flex;行内元素 */align-items:baseline;height: 300px;border:1px solid red;}
		.item{background-color:pink;width:100px;}
	</style>
	<div class="box">
		<span class="item" style="background-color: pink;width: 50px;">注意，设为 Flex 布局以后，子元素的float、clear和vertical-align属性将失效。</span>
		<span class="item" style="background-color: #008cee;height: 50px;line-height: 50px;">我是的发的发的发</span>
		<span class="item" style="background-color: #ffa000;height: 80px;">我是的发的</span>
	</div>

![](http://oibijaovc.bkt.clouddn.com/flex.png)


#### 百分比示例一 ####

将外层元素按照百分比铺满的方式，里面的子元素固定或者左右浮动。
![](http://oibijaovc.bkt.clouddn.com/float.png)

		<body>
		<style>
			.div{width: 100%;height: 100px;border:1px solid;}
			.child1{float:left;background-color: pink;width: 50%;}
			.child2{float:right;background-color: #008cee;width: 50%;}
		</style>
			<div class="div">
				<p class="child1">这是左边的</p>
				<p class="child2">这是右边的</p>
			</div>
		</body>

#### flex示例 ####
一个页面上两个div左右铺满整个浏览器，要保证左边的div一直为100px，右边的div跟随浏览器大小变化（比如浏览器为500，右边div为400，浏览器为900，右边div为800），请写出大概的css代码。


