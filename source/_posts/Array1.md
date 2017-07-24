---
title: 深入理解JavaScript系列：数组（array）
date: 2017-06-25 23:10:57
tags: javascript
categories:
---

js中的数组

<!-- more -->



##### 验证对象是否是数组

##### 数组方法简单分类

>原数组不变，做值的选取处理

* slice（）//返回取到值得数组，原数组不变，选之间
* 

>改变原数组，不会复制，对原数组直接数组

* sort（）
* shift() //返回删除的元素；
* unshift() //返回改变后数组长度
* delete //返回布尔值，原数组长度不变，删除项变为undefined
* pop() //返回删除的元素
* push() //返回改变后数组长度
* result() //返回倒叙后的数组
*  





##### for……in声明

	var arr = new Array();
	arr[0] = 'tony';
	arr[1] = 'tom';
	arr[2] = 'lily';
	for(x in arr){
		console.log(x); // 0 1 2
		console.log(arr[x]); //tony tom lily
	}

>对象中的for……in
		
		Object.prototype.bar = 1;
		var foo= {moo:2};
		for(var i in foo){
			if(foo.hasOwnProperty(i)){
				console.log(i)//moo
			}
		}

##### sort()排序：改变原数组

>从字面上对数组排序

	var arr = new Array();
	arr[0] = 'tony';
	arr[1] = 'tom';
	arr[2] = 'aily';
	console.log(arr.sort()); //[ 'aily', 'tom', 'tony' ]

>从数值上进行排序

	function sortnum(a,b){
		var c = a-b;
		return c;
	}
	var arr = new Array();
	arr[0] = 20;
	arr[1] = 2;
	arr[2] = 88;
	console.log(arr.sort(sortnum)); //[ 2, 20, 88 ]

##### prototype 向模型函数添加属性

	function employee(name,job,born){
		this.name = name;
		this.job = job;
		this.born = born;
	}
	var bil = new employee('toby','dd','1994');
	employee.prototype.salary = null;
	bil.salary = 3333;
	console.log(bil.salary) //333


#### shift() 删除第一个元素，返回删除的元素,原数组改变
	
	var arr = new Array('lily','tony','daming','jack');
	var result = arr.shift();
	console.log(result); //lily
	console.log(arr); //['lily','tony','daming','jack']

##### delete 删除数组中指定某一个元素，长度不变，删除项置为undefined

	var array = [1, 2, 3];
	delete array[1]; //  2  移除下标为1
	console.log(array); // "1,,3"
	
	console.log(array.length); // but the length is still 3
	
	array.forEach(console.log); // 弹出的仅仅是1和3

##### unshift（），向数组开头添加一个或更多元素，并返回新的长度，改变原数组

	var arr = new Array('lily','tony','daming','jack');
	
	var result = arr.unshift('lingling','emily');
	
	console.log(result); //6
	console.log(arr) //['lingling','emily','lily','tony','daming','jack']

##### pop（）删除末尾元素，返回删除的元素

	var arr = new Array('lily','tony','daming');
	var result = arr.pop();
	console.log(result); //daming

##### push（）向末尾增加元素，返回新数组长度
	
	var arr = new Array('lily','tony','daming');
	var result = arr.push('jone');
	console.log(result); //4

##### reverse() 颠倒数组中的元素顺序

	var arr = new Array('lily','tony','daming','jack');
	var result = arr.reverse();
	console.log(result); //[ 'jack', 'daming', 'tony', 'lily' ]

##### slice(start,end) 返回新数组，不会修改原数组

start:必须，第几个开始，若是-3，后面3个。

end：下标，第二个数必须大于第一个参数。

	var arr = new Array('lily','tony','daming','jack');
	var result = arr.slice(1,2);
	console.log(result); //['tony']

##### splice() 从数组中添加/删除项目，返回被删除的项目，改变数组

数组下标1开始，数1个，再添加tonyyy
	var arr = new Array('lily','tony','daming','jack');
	
	var result = arr.splice(1,1,'tonyyy');
	
	console.log(result); //['tony']
	console.log(arr) //['lily','tonyyy','daming','jack']

##### toString() 数组转化为字符串，并返回结果，不改变数组，与不加参数的join（）方法同义
##### pop（）删除末尾元素，返回删除的元素

	var arr = new Array('lily','tony','daming');
	var result = arr.pop();
	console.log(result); //daming

##### join（）指定的分隔符进行分割，默认用 ，分割

	var arr = new Array('lily','tony','daming');
	var result = arr.join();
	console.log(result); //lily,tony,daming

##### valueOf() 返回valueOf的原始值

<font color='#ff0000' size='5'>ES5中新增的Array方法</font>

[点击查看原文](http://www.zhangxinxu.com/wordpress/2013/04/es5%E6%96%B0%E5%A2%9E%E6%95%B0%E7%BB%84%E6%96%B9%E6%B3%95/#foreach)

##### forEach（）语法： array.forEach(callback,[ thisObject])

>三个参数：（遍历数组的内容），（对应的数组索引），（数组本身）
		
		[].forEach(function(value, index, array) {
		    // ...
		});

>对比jQuery中$.each方法

		$.each([], function(index, value, array) {
		    // ...
		});

###### 第一个参数和第二个参数正好相反
	 
	  var data = [1,2,3,4];
	  var result = data.forEach(function(value,index,array){
	    console.log(value);  //1 2 3 4
	    console.log(index); //0 1 2 3
	    console.log(array); //[1,2,3,4] [1,2,3,4] [1,2,3,4] [1,2,3,4]
	  })
		// 与map的区别，map方法必须有返回
	    var data = [1,2,3,4];
	    var result = data.forEach(function(value,index,array){
	      return value;  
	    })
	    console.log(result) //undefined

直接打印

	var arr = new Array('tony','lily','daming','jane');
	arr.forEach(console.log)

终端返回：
	
	tony 0 [ 'tony', 'lily', 'daming', 'jane' ]
	lily 1 [ 'tony', 'lily', 'daming', 'jane' ]
	daming 2 [ 'tony', 'lily', 'daming', 'jane' ]
	jane 3 [ 'tony', 'lily', 'daming', 'jane' ]

> 例子

	var database = {
	  users: ["张含韵", "江一燕", "李小璐"],
	  sendEmail: function (user) {
	    if (this.isValidUser(user)) {
	      console.log("你好，" + user);
	    } else {
	      console.log("抱歉，"+ user +"，你不是本家人");	
	    }
	  },
	  isValidUser: function (user) {
	    return /^张/.test(user);  //test()正则中的匹配，返回布尔值
	  }
	};
	
	// 给每个人法邮件
	database.users.forEach(  // database.users中人遍历
	  database.sendEmail,    // 发送邮件
	  database               // 使用database代替上面标红的this  这个不懂
	);
	
	// 结果：
	// 你好，张含韵
	// 抱歉，江一燕，你不是本家人
	// 抱歉，李小璐，你不是本家


##### map() 映射 array.map(callback,[ thisObject]);
	
	[].map(function(value, index, array) {
	    // return ...
	});

>callback需要有return值

	  var data = [1,2,3,4];
	  var result = data.map(function(value,index,array){
	    console.log(value);  //1 2 3 4
	    return value * value
	  })
	  console.log(result) [1,4,9,16]

>实例
	
	var user = [
	  {name:'王凯','email':"2323432.@qq.com"},
	  {name:'胡歌','email':"2323432.@qq.com"},
	  {name:'胡八一','email':"2323432.@qq.com"},
	  {name:'步子','email':"2323432.@qq.com"},
	  {name:'家具','email':"2323432.@qq.com"}
	]
	var result = user.map(function(value){
	  return value.name
	})
	console.log(result) //['王凯','胡歌','胡八一','步子','家具',]
 
##### filter（） 过滤，指数组filter后，返回过滤后的新数组。用法与map极为相似
 
>语法：array.filter(callback,[ thisObject]);
 
返回值只要是弱等于== true/false就可以了，而非非得返回 === true/false.

	    var data = [0,2,3,4];
	    var result = data.filter(function(value,index,array){
	      return value;  
	    })
	    console.log(result) //[2,3,4];

##### some（），指某些项符合条件，every（）表示是否每一项都符合，返回布尔值

>语法：array.some(callback,[ thisObject]);



	    var data = [0,2,3,8,10];
	    var current = 7;
	    function result(item){
	      return item < current
	    }
	    if(data.some(result)){
	      console.log('数据中有小于7的数字')
	    }

	//打印出了全部，与some的区别在判断所有，some是存在一个
	    var data = [0,2,3,8,10,4];
	    data.map(function(value){
	      if(value<8){
	        console.log('我小于8')  //我小于8  我小于8 我小于8  我小于8 
	      }
	    })


我们自然可以使用forEach进行判断，不过，相比some, 不足在于，some只有有true即返回不再执行了。

#####  every(),每一项都符合，返回布尔值，执行false里的判断

      var data = [0,2,3,8,10];
      var current = 88;
      function result(item){
        return item > current
      }
      if(data.every(result)){
        console.log('数据中有大于88的数字')
      }else{
        console.log("大于88的一个都没有") //大于88的一个都没有
      }


##### indexOf(),在字符串中的使用方法：string.indexOf(searchString, position) 返回下标值

>array.indexOf(searchElement[, fromIndex])

		var data = [2, 5, 7, 3, 5];
		
		console.log(data.indexOf(5, "x")); // 1 ("x"被忽略)
		console.log(data.indexOf(5, "3")); // 4 (从3号位开始搜索)
		
		console.log(data.indexOf(4)); // -1 (未找到)
		console.log(data.indexOf("5")); // -1 (未找到，因为5 !== "5")

##### lastIndexOf（）

>array.lastIndexOf(searchElement[, fromIndex])
		
		var data = [2, 5, 7, 3, 5];
		
		console.log(data.lastIndexOf(5, "x")); // -1 ("x"被忽略)
		console.log(data.lastIndexOf(7, 3)); // 2 (从3号位开始搜索) 倒数第一位，倒数第二位，倒数第三位
		
		console.log(data.lastIndexOf(4)); // -1 (未找到)

##### reduce（）

>语法：array.reduce(callback[, initialValue])

后续补充……