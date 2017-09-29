---
title: 初识vue
date: 2017-09-20 23:10:57
tags: Vue
categories: programming
---

vue data 的简单操作

<!-- more -->

	  export default {
	  name: 'hello123',
	  data() {
	    return {
	      name: '王小二',
	      age: 0,
	      sex: '女',
	      status: true,
	      url: 'https://www.baidu.com/',
	      fn1: function() {
	       alert(假数据)
	      },
	      class1: true,
	      class2: false,
	      classobj: {
	        active: true,
	        'tex2': true
	      },
	      lists: [
	        { color: 'yellow' },
	        { color: 'blue' },
	        { color: 'red' }
	      ],
	      result:['王一','网二','网顺丰速递']
	    }
	  },
	  computed:{
	    myfn:function(){
	      return this.name + "生命周期呀"
	    }
	  }
	}

 
> 模板基础语法

##### 简单数据绑定 #####

 	<p>{{name}}</p>

#### v-if ####(问题：age=5，输出10到20之间)

	<p v-if="age>20">年级大于20——{{age}}</p>
    <p v-else-if ="9<age<19">10到20之间——{{age}}</p>
    <p v-else>年龄小于10—— {{age}}</p>

##### 表达式 #####

	<p>{{ status ? '显示' : '不显示' }}</p>

##### v-bind:href 更新属性#####

	 <a v-bind:href='url'>点击这里调到百度去</a>

简写 ：href='url'

##### v-on:click 监听dom #####

	<button v-on:click='fn1'>点击我</button>

简写 @click='fn1'

##### v-for #####	
	
	<p v-for = '(list,index) of lists' v-bind:key='list.color'>
      {{list.color}}_{{index}}
    </p>

#### 生命周期 ####

	<p>{{myfn}}</p>

> 计算属性和观察者

#### 计算属性（对data里的数据进行操作） ####

	 computed:{//这是计算属性（对data中的数据进行处理）
	    myfn:function(){
	      return this.name='计算属性操作name';
	    }
	  }

#### 方法 ####