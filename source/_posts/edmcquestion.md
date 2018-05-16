---
title: edmcquestion
date: 2018-05-15 19:51:18
tags:
categories:
---

- 参数解构


		actions: {
   	 		increment (context) {
      		context.commit('increment')
    		}
  		}
		//解构后
		actions: {
  			increment ({ commit }) {
    		commit('increment')
  			}
		}

Q:变量的解构赋值

- actions中对象形式分发失败

		actions: {
    		reduce(state) {
      		// setTimeout(()=>{
      		//   state.commit('incrementpayload');
      		// },20)
    		},
    		reduceobj(state, payload) {
      		state.count += 2;//???该方法执行失败
      		// state.commit('incrementpayload');
    		}
  		}

Q:action必须配合mutations一起使用吗

- 对象解构的嵌套结构对象

		let obj = {
		  p: [
		    'Hello',
		    { y: 'World' }
		  ]
		};
		
		let { p, p: [x, { y }] } = obj;
		x // "Hello"
		y // "World"
		p // ["Hello", {y: "World"}]

Q:应该只有一个p变量对象，第2个应该为undefined。
A:应该是变量重复赋值

- 函数参数的解构

action函数接收一个
		 actions: {
		    increment (context) {
		      context.commit('increment')
		    }
		  }
		//参数解构方式
		actions: {
		  increment ({ commit }) {
		    commit('increment')
		  }
		}

Q:不明白参数解构方式