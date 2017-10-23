---
title: json.parse()和json.stringify()
date: 2017-10-18 23:10:57
tags: javascript
categories: programming
---


#### parse（） ####

字符串解析为json对象<font color="#ff7f50">单引号写在{}外，每个属性名都必须用双引号</font>

	var str = '{"name":"jone","age":"18"}'
	JSON.parse(str);
	//结果
	name:"jone",
	age:"18"

#### stringify（） ####

对象解析成字符串

	var a = {name:"jone",age:"18"}
	JSON.stringify(a)
	//结果
	'{name:"jone",age:"18"}'
