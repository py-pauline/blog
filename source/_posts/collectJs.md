---
title: javascript刷题记录
date: 2017-07-10 21:24:16
tags:
categories:
---
牛客网刷题错题记录

<!-- more -->

* defer属性：延迟脚本执行，只支持IE浏览器
* js基本数据类型（6种原始类型+Object）:String Boolean Number Null Undefined Symbol和Object
* js获取select下拉框的值：

 			<select id="musicTypes" name="musicTypes" multiple="multiple">
              <option selected="selected">R&B</option>
              <option selected="selected">爵士</option>
              <option>布鲁斯</option>
              <option>新纪元</option>
              <option>古典</option>
              <option>戏剧</option>
            </select>
			<script>
			var obj = document.getElementById('musicTypes');
			  for(var i = 0;i<obj.options.length;i++){
			    if (obj.options[i].selected) {
			      console.log(obj.options[i].value) //R&B 爵士
			    }
			  }
			</script>

* 