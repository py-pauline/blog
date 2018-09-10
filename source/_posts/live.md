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



