---
title: HTML5中input元素的种类
date: 2016-11-20 22:05:05
tags: html5 
---
在html5中，大幅度增加与改良了input元素的种类，对于这些input的种类来说，支持得最多、最全面的是Opera 10浏览器。

### 1. URL类型 ###

url类型的input元素是一种专门用来输入url地址的文本框。提交时如果该文本框中内容不是url地址格式的文字，则不允许提交。

### 2. email类型 ###

专门用来输入email地址的文本框。提交时如果该文本框中的内容不是email地址格式的文字则不允许提交，但是它并不检查该email地址是否存在。提交时该文本框可以为空，除非加上require属性。

<!--more-->

### 3. date类型 ###

	<input type="datetime" value="输入UTC日期和时间">
	<input type="date" value="年月日">
	<input type="month" value="年月">
	<input type="week" value="年周">
	<input type="time" value="小时">
	<input type="datetime-local" value="输入本地日期和时间">

#### 预览效果 ####

datetime:<input type="datetime" value="输入UTC日期和时间"><br>
date:<input type="date" value="年月日"><br>
month:<input type="month" value="年月"><br>
week:<input type="week" value="年周"><br>
time:<input type="time" value="小时"><br>
datetime-local:<input type="datetime-local" value="输入本地日期和时间">

### 4. number类型 ###

提交时会检查是否为数字。有max，min，step属性。

	<input type="number" max="80" min="50" step="5">

### 5. range类型 ###

	<input type="range"  max="80" min="50" step="5">

### 6. search类型 ###

在外观上与text类型有区别，在safari4浏览器中是圆角矩形文本框。

### 7. tel类型 ###

输入电话号码的专用文本框，不强制输入数字，可以通过pattern属性来制定对于输入的电话号码格式的验证。

	<input type="tel" value="输入11位的数字" pattern="[0-9]{11}">

### 8. color类型 ###


