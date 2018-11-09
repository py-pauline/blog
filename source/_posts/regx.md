---
title: 表单中常用正则表达式
date: 2018-04-16 16:32:56
tags:
categories:
---

完整参考
- 只能输入数字

	  <input type="text" onkeyup="this.value=this.value.replace(/\D/g,'')" onafterpaste="this.value=this.value.replace(/\D/g,'')">

	  function sortEdit(value) {
	        var reg = /^[1-9]\d*$/;
	        if (reg.test(value)) {
	            return value;
	        } else {
	            return '';
	        }
	    }
		<input onkeyup="value=sortEdit(value)" type="text" class="form-control" value="2">



