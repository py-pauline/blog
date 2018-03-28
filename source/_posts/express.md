---
title: 使用express框架搭建简单服务器
date: 2018-03-27 21:08:03
tags: nodejs
categories: programming
---

[gitbub项目地址](https://github.com/77ya/weApp)

开发前准备：安装node.js

#### 安装 ####

创建文件，并安装express模块

	$ mkdir wechat 创建wechat文件
	$ cd wechat
	
	$ npm init package.json 文件（存储module模块记录）
	
	$ npm install express --save 安装express并保存到依赖列表中

创建好后目录结构如下



#### 简单实例 （应用级中间件）####

启动一个服务器，并监听端口3000进入连接请求。

app.js代码如下：
	
	
	var express = require("express");
	var app = express();
	
	//app.use(express.static('web'));//静态文件的目录作为参数传递给express.static中间件 就可以访问静态资源的访问
	
	/**
	 * 增加虚拟路径时，静态页面可以正常访问，当页面增加虚拟路径时，请求链接不变
	 */
	app.use("/index",express.static('web'));
	
	
	//含有字符串 a 的路由,结果返回字符串
	 app.get(/a/,function(req,res,next){
	    console.log("response will be send by next function");
	    next();
	 },function(req,res){ 
	     res.send("这是关于首页的介绍");
	 });
	
	 /**
	  * 应用级中间件绑定到app对象使用 app.use()和app.METHOD()
	  * METHOD需要处理http请求的方法：get post put等
	  */
	
	//没有挂载的中间件，应用的每个请求都会执行该中间件。
	app.use(function (req, res, next) {
	    console.log('Time:', Date.now());
	    next();
	});
	
	/**
	 * app.all() 是一个特殊的路由方法，没有任何 HTTP 方法与其对应，它的作用是对于一个路径上的所有请求加载中间件。
	 */
	app.all('/allmethod', function (req, res) {
	    res.send("all路由方法测试");
	});
	
	//接口返回json格式  结果封装处理result();
	function result(obj,msg,status){
	    return {
	        data: obj,
	        status: status,
	        msg: msg
	    }
	};
	app.post("/indexuser",function(req,res){
	    var obj = result({
	        user: "pauline",
	        age: "18",
	        sex: "女",
	        intro: "web开发"
	    },
	    0,
	    "访问成功"
	    )
	    res.json(obj);
	 });
	
	 /**
	  * get请求带参数name
	  */
	 app.get('/updata',function(req,res){
	     res.send(req.params.name);  //暂不明白
	 })
	
	/**
	 * app.route() 创建路由路径的链式路由句柄
	 */
	app.route('/book')
	.get(function(req,res){
	    res.send('这是get请求');
	})
	.post(function(req,res){
	    res.send('这是post请求');
	})
	
	
	
	var server = app.listen(3000, function () {
	    var host = server.address().address;
	    var port = server.address().port;
	
	    console.log('Example app listening at http://%s:%s', host, port);
	}) 

 index.html js代码如下

	<script>
	        $.post({
	            url: "/indexuser",
	            success: function (res) {
	                console.log(res);
	                //返回以下json对象
	                // {
	                //     data: {
	                //         user: "pauline",
	                //         age: "18",
	                //         sex: "女",
	                //         intro: "web开发"
	                //     },
	                //     status:0,
	                //     msg:'访问成功'
	                // }
	            }
	        })
	
	        /**
	         * app.route() 创建路由路径的链式路由句柄
	         * 
	        */
	        $.get({
	            url: '/book',
	            success: function (res) {
	                console.log(res);//这是get请求
	            }
	        });
	        $.post({
	            url: '/book',
	            success: function (res) {
	                console.log(res);//这是get请求
	            }
	        });
	        /**
	         * 带参数name的get请求
	        */
	         $.get({
	             url:'/updata',
	             data:{
	                 name:'pauline'
	             },
	             success:function(res){
	                 console.log(`${res}这是get带参数返回结果`);
	             }
	         })
	
	    </script>

启动服务器

	$ node app.js	

浏览器中访问该路径即可访问


#### 路由级中间件 ####

birds.js 代码如下：
	
	/**
	 * express.Router
	 */
	var express = require("express");
	var app = express();
	
	app.use("/static", express.static('web')); //express.static  是express唯一内置的中间件，负责在express中托管静态资源
	
	/**
	 * 错误处理中间件
	 */
	app.use(function(err,req,res,next){
	    console.log(err.stack);
	    res.status(500).send('内部错误');
	})
	/**
	 * 创建一个路由模块
	 */
	var express = require ('express');
	var router = express.Router(); //它是完整的中间件和路由系统，”mini-app“
	/**
	 * 加载路由级一个中间件
	 */
	router.use(function timelog(req,res,next){
	    console.log('time:',Date.now());
	    next();
	})
	/**
	 * 定义一些路由，并且将他们挂载至应用路径上
	 * 定义网站主页的路由
	 */
	router.get('/',function(req,res){
	    res.send('获得菜单信息');
	});
	/**
	 * 定义about页面的路由
	 */
	router.get('/about',function(req,res){
	    res.send('获得介绍页信息');
	})
	
	
	
	module.exports = router;
	
	//将路由挂载至应用
	app.use('/',router);
	
	var server = app.listen(3000, function () {
	    var host = server.address().address;
	    var port = server.address().port;
	
	    console.log('Example app listening at http://%s:%s', host, port);
	}) 


至此，一个express搭建的后台服务器完毕