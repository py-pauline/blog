---
title: 问题汇总
date: 2018-03-22 13:10:57
tags: 问题汇总
categories: query
---
[ 
原文地址](http://obkoro1.com/2018/03/18/3%E6%9C%88%E5%88%9D%E4%B8%8A%E6%B5%B7%E5%89%8D%E7%AB%AF%E9%81%87%E5%88%B0%E7%AC%94%E8%AF%95%E9%A2%98%E9%9D%A2%E8%AF%95%E9%A2%98%E8%AE%B0%E5%BD%95/#more)

#### 跨域问题 ####
 浏览器为了安全实施的同源策略导致的，同源：两个URL的域名、协议、端口要完全相同

解决方案：

script标签jsonp跨域、nginx反向代理、nodejs中间件代理跨域、后端在头部信息设置安全域名

- JSONP
- CORS
- 服务端代理

JSONP的原理：

利用script标签支持跨域的属性，用script标签拿到包裹了数据的方法（相当于是返回了一段js代码），在请求中包含callback，服务端注入参数后返回这个回调函数，然后script标签拿到返回的js代码跨域直接运行回调，需要前后端的配合。
 
jsonp不可以用post请求，因为script标签只支持get请求。


---

<!-- more -->
	
#### 定时器的执行顺序和机制 ####

因为js是单线程的，浏览器遇到setTimeout或者setInterval会先执行完当前的代码块,在此之前会把定时器推入浏览器的待执行事件队列里面,执行完当前代码才会执行定时器代码。


	 for(var i=0;i<10;i++){
      setTimeout(function(){
        console.log(i);
      },1000)
    }
    //打印出10個10

	 setTimeout(function(){
	     console.log("定时器");
	   },0)
	  console.log("先执行此条语句");

---

#### html中title属性和alt属性的区别 ####

	<img src="#" alt="alt信息" title="title信息"/>

图片不输出信息时：显示“alt信息“，鼠标放上去显示”title信息“


title属性可以用在除了base，basefont，head，html，meta，param，script和title之外的所有标签

title属性的主要功能是为了提示，比如一些链接本身未清楚表达链接的目的，此时就可以添加title属性

#### http状态码 ####
1xx：1开头的是信息状态码
2xx：2开头的是请求成功
3xx：3开头的是重定向
4xx：4开头的是客户端错误
5xx：5开头的是服务器错误

#### 面向对象编程 ####

面向对象的三大特性：继承，封装，多态

面向对象：

 	//面向对象
    //定义人（姓名，性别，年龄）
    let people = function(name){
        this.name = name;
    }
    //动作
    people.prototype={
        eat:function(something){
            console.log(`${this.name}吃${something}`)
        }
    }
    //创建一个人(new一次People)
    var pauline = new people('彭彭');
    pauline.eat("火锅"); //彭彭吃火锅
    //后续动作
    pauline.coding=function(){
        console.log(this.name+'写代码')
    }
    pauline.coding();//彭彭写代码

面向过程：

	//面向过程
    let eat = function(name,something){
        console.log(`${name}吃${something}`);
    }
    eat('彭彭','火锅'); //彭彭吃火锅
    //后续动作
    let coding = function(name){
        console.log(`${name}写代码`);
    }
    coding('彭彭')//彭彭写代码

**面向对象更加的灵活，复用性和扩展性更好。面向对象是针对对象（彭彭）来执行某些动作，并且动作可以自定义扩展**

**面向过程是定义很多的动作，来指定谁来执行这个动作**

---

#### javascript作用域 ####



- 全局作用域

- 函数作用域

ES5之前没有块级作用域，ES6提出了这个概念

#### let和var区别 ####

- var 能重复声明，let不能
- let的变量作用范围不同，不存在变量提升

#### ES6常用特性 ####

- 箭头函数
- 模板字符串
- Class
- module
- 对象解构
- Promise

有三种状态：pending、fulfilled、reject

两个过程：

pending -> fulfilled

pending -> rejectd

#### react生命周期 ####
初始化

- constructor
- getInitialState
- getDefaultProps
- componentWillMount
- render
- componentDidMount


更新过程

- componentWillReceiveProps
- shouldComponentUpdate
- componentWillUpdate
- render
- componentDidUpdate


卸载过程

- componentWillUnmount
- 
#### 构建工具webpack的loader是干什么的 ####

loader是用来编译和处理资源的

#### vue和react使用起来有什么区别 ####

vue数据双向绑定的原理

#### 什么情况下会返回304状态码  ####

这个问题比较复杂吧，这里回答了一个Etag

ETag是HTTP1.1产物，服务器通过某种算法，给资源计算出一个唯一的标志符，可能是一个资源的MD5值，在把资源响应给客户端的时候，会在实体首部加上"ETag: 值"，一起返回给客户端
客户端会保留这个字段，并在下次请求的时候一并带过去给服务端，服务端接受客户端传来的ETag的值，然后进行比较前后的ETag的值是否一致，就能判断资源相对客户端是否被修改了
如果匹配上了，服务端会返回304状态码，并告诉客户端直接使用本地缓存即可，反之，则以正常的GET200形式返回资源
对应的首部字段

If-None-Match：ETag-value
If-Match：ETag-value


还有一种就是下面问的Last-Modified

#### http缓存，cache-control和etag有什么区别 ####

- 服务器将资源传递给客户端时，会将资源最后更改的时间以"Last-Modified: GMT"的形式加在实体首部上一起返回给客户端
- 客户端为该资源标记上信息，下次请求时，会将该信息带在请求报文中一起返回给服务端，服务端去做检查，若服务器上该资源最终修改时间是一致的，则资源没有被修改过，直接返回304状态码，不返回内容
- 对应的首部字段

	- If-Modified-Since: Last-Modified-value

	- If-Unmodified-Since: Last-Modified-value

---

#### css盒模型 ####

- 标准盒模型（w3c标准）

总宽度为：width+margin（左右）+padding(左右)+border（左右）

- 怪异模式（ie）

总宽度为：width+margin（左右） 即width已经包含了padding和border的值

#### 实现水平居中 ####

- flexbox
- 绝对定位+margin负值（已知宽高）
- 绝对定位+transfrom负值（未知宽高）
- 绝对定位top left right bottom 0 + margin auto