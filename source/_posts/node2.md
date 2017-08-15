---
title: node.js学习笔记二（npm使用介绍）
date: 2017-06-15 11:51:17
tags: nodejs
categories: programming
---
### 关于npm
npm是随同NodeJS一起安装的包管理工具，能解决nodejs代码部署的很多问题
<font color="#FF7F50"></font>  
使用场景有以下几种方式：

* 允许用户从NPM服务器下载别人编写的第三方包到本地使用
* 允许用户从NPM服务器下载并安装别人编写的命令行程序到本地使用
* 允许用户将自己编写的包或命令行产业内需上传到NPM服务器供人使用

<!--more-->

### 常用命令

	npm -v //查看安装版本
	npm install npm -g //升级npm
	cnpm install npm -g //升级npm（淘宝镜像）
	npm install <module name>  //如安装node.js web框架模块express； npm install express
	npm install express  //本地安装
	npm install express -g //全局安装
	npm list -g //查看所有全局安装的模块
	$ npm list grunt //查看某个模块的版本号
	npm uninstall express //卸载模块
	npm update express //更新模块
	
	
	
	
### 使用npm命令安装模块

	npm install express //安装express框架模块
	
安装好之后，express包就放在了工程目录下的node_modules目录中，因此在代码中只需要通过require（'express'）

	var express = require(express);

### 使用package.json
package.json位于模块的目录下，用户定义包的属性。位于node_modules/express/package.json 。

### 淘宝npm镜像

你可以使用cnpm命令行工具代替默认的npm

	npm install -g cnpm --registry=https://registry.npm.taobao.org

这样就可以使用cnpm命令来安装模块了

	cnpm install [name]
	
	
	
	
	


 

