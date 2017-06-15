---
title: hexo常用命令
date: 2017-06-15 11:35:54
tags:
categories:
---
参考来源：[https://segmentfault.com/a/1190000002632530](https://segmentfault.com/a/1190000002632530 "笔记参考")
### hexo

	npm install hexo -g  安装
	npm update hexo -g 升级
	hexo init  初始化

<!--more-->

### 操作中常用

	hexo n '新建博客' == hexo new '新建博客'  //新建文章
	hexo p == hexo publish	  //生成页面
	hexo g == hexo generate  //生成静态页面至public目录（发布）
	hexo s == hexo server   //启动服务预览
	hexo d == hexo deploy  //部署

### 完成后部署（两个命令作用相同，相当于发布）
	hexo g == hexo generate  //生成静态页面至public目录
	hexo d == hexo deploy  //部署

