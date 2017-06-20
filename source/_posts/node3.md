---
title: node.js学习笔记三（REPL）
date: 2017-06-18 15:28:17
tags:
categories:
---
### REPL(交互式解释器)
* REPL表示一个电脑的环境，类似window系统的终端或Unix/linux shell，可以在终端输出命令，并接收系统的响应。
* REPL可以执行以下任务
 * 读取-读取用户输入，解析输入了JavaScript数据结构并储存在内存中。
 * 执行-执行输入的数据结构
 * 打印-输出结果
 * 循环-循环操作以上步骤知道用户两次按下Ctrl+c按钮退出。
 <!-- more -->
**启动node终端**

![](http://oibijaovc.bkt.clouddn.com/%E5%90%AF%E5%8A%A8node%E7%BB%88%E7%AB%AF.png)
 
**使用变量简单表达式**

![](http://oibijaovc.bkt.clouddn.com/%E7%AE%80%E5%8D%95%E8%BF%90%E7%AE%97.png)

### REPL命令
	ctrl + c - 退出当前终端。
	ctrl + c 按下两次 - 退出 Node REPL。
	ctrl + d - 退出 Node REPL.
	向上/向下 键 - 查看输入的历史命令
	tab 键 - 列出当前命令
	.help - 列出使用命令
	.break - 退出多行表达式
	.clear - 退出多行表达式
	.save filename - 保存当前的 Node REPL 会话到指定文件
	.load filename - 载入当前 Node REPL 会话的文件内容。