---
title: webpack
date: 2018-04-03 14:39:10
tags: webpack
categories:
---


1. 创建文件夹初始化并安装webpack

		mkdir project
		npm init
		npm install webpack --save-dev


// module.exports = {
//     entry:'./app.js',
//     output:{
//         filename:'bundle.js'
//     }
// };

/**
 * 入口 entry
 * 
 */
//单个入口的简写
//  const config = {
//      entry:'./app.js'
//  }

 //单个入口语法完整写法
//  const config = {
//      entry:{
//          main:'./app.js'
//      }
//  } 
 //多个入口（对象语法）
//  const config = {
//      entry:{
//          app:'/app.js',
//          pageone:'/pageone.js'
//      }
//  }
//  module.exports = config;

/**
 * 输出 output
 * ps:即使多个入口起点，但只指定一个输出配置
 * 值为一个对象:filename(输出文件的文件名)+path（目标输出目录的绝对路径）
 * 
 */
// const config = {
//     output:{
//         filename:'bundle.js',
//         path:'/webpack'
//     }
// }
// module.exports = config;
/**
 * loader
 * webpack处理css文件或者将typescript转为javascript，首先安装相对应的loader
 * npm install --save-dev css-loader
 * npm install --save-dev ts-loader
 * 然后指示webpack对每个d.css使用css-loader,对所有的.ts文件使用ts-loader
 */
// module.exports= {
//     module:{
//         rules:[
//             {test:/\.css$/,use:'css-loader'},
//             {test:/\.ts$/,use:'ts-loader'}
//         ]
//     }
// }

/**
 * 插件是webpack的支柱功能
 */
/**
 * 源代码（/src）:书写和编辑的代码
 * 分发代码（/dist）：构建过程产生的代码最小化和优化后的输出目录
 */

