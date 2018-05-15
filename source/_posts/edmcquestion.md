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