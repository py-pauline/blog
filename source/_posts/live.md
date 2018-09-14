---
title: 项目中遇到得问题
date: 2017-06-15 11:45:07
tags: javascript
categories: programming
---

#### js是单线程 ####
#### 什么情况下引起跨域 ####
#### 还有浏览器输入网址之后从按回车，到加载完发生了什么事 ####
#### js的第七种数据类型Symbol ####
#### ES6新增方法数组方法find() findIndex() ####
#### 接口对接 ####

场景描述：后端确认接口无误，前端参数确认无误，接口返回500
解决方案：参数中有空格，在复制接口文档中的参数要格外注意，细心检查空格；


#### 标签自定义属性取值 ####

在选取一个动态数据渲染出来的节点会很有用，不用一层一层去找。

$('[_name]="myself"')

#### 数组拼接 ####

	var arr1= [1,2,2];
	var arr2 = [1,11,1];
	var arrcontact = arr1.push(arr2);
	console.log(arrcontact);//[1,2,2,1,11,1]

#### 电话号码星号标记 ####

 	if (str.length > 7) {
        var strend = str.substring(4, str.length - 4);
        var newstr = str.replace(strend, "***");
        $('#num').html(newstr);
    };

#### 根据对象属性渲染对应值 ####

	<p class='node' _name="age"></p>
    <p class='node' _name="age"></p>
    <p class='node' _name="like"></p>

 	var res = { name: 'pauline', age: '11', like: 'wew' }

	// 方法一：节点遍历
    $('.node').each(function(i,item){
        _name = $(item).attr('_name')
        $(item).text(res[_name])
    })

	// 方法二：对象枚举
 	for(var i in res){
        $('[_name='+i+']').text(res[i]);
    }

#### 函数去抖和函数节流 ####

https://blog.csdn.net/flqbestboy/article/details/77750598

#### input:radio 常用操作 ####

	//name值是为了标注这是一组单选

	<input type="radio" name="sex" value="0" checked>男
    <input type="radio" name="sex" value="1">女

  	// 获取选中的值
    var checkedVal = $('input[name="sex"]:checked').val();
    // 判断选中 true或false
    var res = $("#checkbtn").is(":checked"); 
    // 设置特定的值的选中情况
    $('input:radio[name="sex"][value="1"]').prop('checked',true);
    $('input:radio[name="sex"][value="1"]').prop('checked',false);

#### input:checkbox 常用操作 ####



#### select 常用操作 ####

	 <select name="" id="">
        <option _name = '第一' value="1">第一</option>
        <option _name = '第二' value="2">第二</option>
        <option _name = '第三' value="3">第三</option>
	 </select>


1. 获取选中的value值
	
	$('select').val();
    $('select option:selected').val();

2. 获取选中的文本值

	$('select option:selected').text();

3. 根据value设置选中

	$('select').val('1');

4. 根据text设置选中

	$('select').find('option:contains("第一")').attr('selected',true);

5. 特定值设置选中

	var selected = $('option[_name="第二"]').val();
    $('select').val(selected);
