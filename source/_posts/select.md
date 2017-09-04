---
title: select下拉值的选取
date: 2017-09-03 20:27:02
tags: html
categories: programming
---
 select的下拉框的值一般通过value直接获取就可以，但在项目中遇到了需要设置特定选项的选取，这时可以采用 selectedIndex 属性。

#### 直接获取 ####
  
js方法

    var obj = document.getElementsByTagName('select')[0]; //select
	obj.value();

jquery方法

	var obj = $('select');
	obj.val();
	//或者将fn（）绑定select节点的onchange事件
	function fn(){
		var obj = $('select');
		var text = obj.find('option:selected').text();
		var value = obj.find('option:selected').val();
	}

<!-- more -->

#### selectedIndex索引号属性 ####

	var obj = document.getElementsByTagName('select')[0]; //select
	var index = obj.selectedIndex;//属性可设置或返回下拉列表中被选选项的索引号。
	var text = obj.options[index].text; // 选中文本
	var value = obj.options[index].value; // 选中值



