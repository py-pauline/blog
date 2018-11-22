---
title: 项目中遇到得问题
date: 2017-06-15 11:45:07
tags: javascript
categories: programming
---

#### js是单线程 ####
#### 什么情况下引起跨域 ####
#### 还有浏览器输入网址之后从按回车，到加载完发生了什么事 ####
#### js的第七种数据类型Symbol ####
#### ES6新增方法数组方法find() findIndex() ####
#### 接口对接 ####

场景描述：后端确认接口无误，前端参数确认无误，接口返回500
解决方案：参数中有空格，在复制接口文档中的参数要格外注意，细心检查空格；


#### 标签自定义属性取值 ####

在选取一个动态数据渲染出来的节点会很有用，不用一层一层去找。

$('[_name]="myself"')

#### 数组拼接 ####

	var arr1= [1,2,2];
	var arr2 = [1,11,1];
	var arrcontact = arr1.push(arr2);
	console.log(arrcontact);//[1,2,2,1,11,1]

#### 电话号码星号标记 ####

 	if (str.length > 7) {
        var strend = str.substring(4, str.length - 4);
        var newstr = str.replace(strend, "***");
        $('#num').html(newstr);
    };

#### 根据对象属性渲染对应值 ####

	<p class='node' _name="age"></p>
    <p class='node' _name="age"></p>
    <p class='node' _name="like"></p>

 	var res = { name: 'pauline', age: '11', like: 'wew' }

	// 方法一：节点遍历
    $('.node').each(function(i,item){
        _name = $(item).attr('_name')
        $(item).text(res[_name])
    })

	// 方法二：对象枚举
 	for(var i in res){
        $('[_name='+i+']').text(res[i]);
    }

#### 函数去抖和函数节流 ####

https://blog.csdn.net/flqbestboy/article/details/77750598

#### input:radio 单选常用操作 ####

	//name值是为了标注这是一组单选

	<input type="radio" name="sex" value="0" checked>男
    <input type="radio" name="sex" value="1">女

  	// 获取选中的值
    var checkedVal = $('input[name="sex"]:checked').val();
    // 判断选中 true或false
    var res = $("#checkbtn").is(":checked"); 
    // 设置特定的值的选中情况
    $('input:radio[name="sex"][value="1"]').prop('checked',true);
    $('input:radio[name="sex"][value="1"]').prop('checked',false);

___

#### input:checkbox 多选常用操作 ####



- 全选、取消全选、反选操作

		<input type="checkbox" name="sel">芒果
	    <input type="checkbox" name="sel">芒果
	    <input type="checkbox" name="sel">芒果
	    <input type="checkbox" name="sel">芒果
	
	    <input type="checkbox" id="allSel" name='allSel'>全选
	    <input type="button" value="取消" id="selCancel" name='selCancel'>
	    <input type="button" value="反选" id="toggleSel" name='toggleSel'>



- 全选操作

 		$('#allSel').change(() => {
            if ($('input[name="allSel"]').is(':checked')) {
                $('input[name="sel"]').prop('checked', true);
            } else {
                $('input[name="sel"]').prop('checked', false);
            }
        })


- 取消全选

        $('#selCancel').click(() => {
            $('input[name="sel"]').prop('checked', false);
        })



- 反选

        $("#toggleSel").click(function () {
            $("input[name='sel']").each(function () {
                this.checked = !this.checked;
            });
        });


___

#### select 常用操作 ####

	 <select name="" id="">
        <option _name = '第一' value="1">第一</option>
        <option _name = '第二' value="2">第二</option>
        <option _name = '第三' value="3">第三</option>
	 </select>


- 获取选中的value值
	
	$('select').val();
    $('select option:selected').val();

- 获取选中的文本值

	$('select option:selected').text();

- 根据value设置选中

	$('select').val('1');

- 根据text设置选中

	$('select').find('option:contains("第一")').attr('selected',true);

- 特定值设置选中

	var selected = $('option[_name="第二"]').val();
    $('select').val(selected);

___

#### 图片渲染失败 ####

img 图片加载时，后端数据返回为无效图片链接，此时可将无效图片路径统一设置为默认图片路径。

- 方法一：onerror属性
    <img src="无效链接" alt="" onerror="this.src='../images/test2.jpg'">


- 方法二：jquery的error函数

	$('img').error(()=>{
		$(this).attr('src','default.png');
	})
___	

#### border-radius和border同时使用问题 ####

两个属性作用于同一个元素时，border显示不完整，解决方案如下：

用box-shadow代替border。

	.box{
		box-shadow: 0px 0px 0px 2px #1890ff;
		border-radius:50%;
	}

---

#### DOM 0级事件和DOM级事件的认识 ####


- 0级DOM:标签内写onclick事件和直接onclick


	 	<button id='btn' onclick="foo()"></button>
	    <script>
	       function foo(){
	           alert('this is 0 DOM')
	       }

	       document.getElementById('btn').onclick=function(){
	           alert('this is 0 DOM');
	       }
	    </script>

- 2级DOM(可绑定多个函数，默认采用事件冒泡机制)

	 	<button id='btn'></button>
	    <script>
	      var btn = document.getElementById('btn');
	      btn.addEventListener('click',e=>{
	          alert('二级DOM');
	      })
	      btn.on('click',e=>{
	          alert('二级DOM');
	      })
	    </script>
-----

#### input[file]文件上传 ####

  	let files = $(this)[0].files,
    fileNamepointLen = (files[0].name).lastIndexOf("."),//取到文件名开始到最后一个点的长度
    fileNameLength = files[0].name.length,//取到文件名长度
    name = files[0].name.substring(fileNamepointLen + 1, fileNameLength);//截
	if (!['jpg', 'png', 'jpeg', 'gif'].includes(name)) {
	    $.api.meg('只支持jpg,png,jpeg,gif格式的图片上传!');
	    return false;
	}

___	


#### 变量类型 ####


- Boolean
- string
- number
- null
- undefined
- symbol
- Object

**总共7种，定义了6种原始类型，Object属于引用类型**

> typeof判断类型

	typeof Symbol() //symbol
	
	typeof 1 //number
	
	typeof [1,2] //object 引用类型除了function，其他均为object
 	
	typeof null //object 所以判断的时候要过滤掉此种情况

**判断数组**
	
	[1,2] instanceof Array //true

> 值类型和引用类型的区别

值类型：6种原始类型

引用类型：包括了Object类的所有：Date、Array、Funciton

在参数传递方式上，值类型是按照值传递，引用类型按共享传递。

---

#### trigger()触发指定元素的指定事件类型 ####

点击A触发B的点击事件

$A.on('click',function(){
	$B.trigger('click');
})

#### 原型和原型链 ####

- 所有的引用类型（类型、对象、函数），都具有对象特性，即可自由扩展属性（null除外）
- 所有的引用类型（数组、对象、函数），都有一个_proto_属性，属性值是一个普通的对象，__proto__属性值指向它的构造函数的prototype属性值
- 所有的函数，都有一个prototype属性，属性值也是一个普通的对象。

---

#### ajax.set 统一字符串更改为formdata提交 ####
	 function isJsonString (str) {
	    try {
	      if (typeof JSON.parse (str) == 'object') {
	        return true;
	      }
	    } catch (e) {}
	    return false;
	  }
	  $.ajaxSetup ({
		beforeSend: function (jqXHR, settings) {
		        // 配合请求头修改json数据格式
		      if (isJsonString(settings.data)) {
		         var data = JSON.parse(settings.data);
		        settings.data = Qs.stringify(data);
		      }
		）｝


#### 作用域 ####
#### es6 class定义类 ####

定义“类”的方法的时候，前面不需要加上function这个关键字，直接把函数定义放进去了就可以了。另外，方法之间不需要逗号分隔，加了会报错。


- 类的所有方法都定义在类的prototype属性上（所有的方法都有一个prototype属性，它是一个普通对象）

		class Point {
		  constructor() {
		    // ...
		  }
		
		  toString() {
		    // ...
		  }
		
		  toValue() {
		    // ...
		  }
		}
	
		// 等同于
	
		Point.prototype = {
		  constructor() {},
		  toString() {},
		  toValue() {},
		};


- 在类的实例上面调用方法，就是调用原型上的方法。
	
		class B {}
		let b = new B();
		
		b.constructor === B.prototype.constructor // true


- prototype对象的constructor属性，直接指向类本身。子类在constructor方法中需调用super方法，否则报错，因为子类自己的this对象，必须先通过负累的构造函数完成塑造，得到父类的属性和方法。

		Point.prototype.constructor === Point // true
		class Point {}
		
		class ColorPoint extends Point {
		  constructor(x, y, color) { // 指向类本身
		    super(x, y); // 调用父类的constructor(x, y)，指向当前对象的原型对象
		    this.color = color;
		  }
		
		  toString() {
		    return this.color + ' ' + super.toString(); // 调用父类的toString()
		  }
		}


注意！！！super关键字，表示父类的构造函数，用来新建父类的this对象

#### super关键字 ####

- 作为函数调用，代表父类的构造函数，es6要求，子类的构造函数必须执行一次super函数
	
		class A {}
		
		class B extends A {
		  constructor(props) {
		    super(props);
		  }
		}

注意！！！，super虽然代表了父类A的构造函数，但是返回的是子类B的实例，即super内部的this指的是B，因此super()在这里相当于A.prototype.constructor.call(this)。

作为函数时，super()只能用在子类的构造函数之中。

		class A {}
		
		class B extends A {
		  m() {
		    super(); // 报错
		  }
		}

上面代码中，super()用在B类的m方法之中，就会造成句法错误。

- super作为对象时，在普通方法中，指向父类的原型对象；在静态方法中，指向父类。

#### 转义符拼接  ####

 	onclick=\"getMembers('" + value + "')\"

#### 装饰器 ####

修饰器（Decorator）函数，用来修改类的行为。

修饰器是一个对类进行处理的函数。修饰器函数的第一个参数，就是所要修饰的目标类。

	@testable
	class MyTestableClass {
	  // ...
	}
	
	function testable(target) {
	  target.isTestable = true; // target指向目标类
	}
	
	MyTestableClass.isTestable // true

mapStateToProps:建立组件和store的state的映射关系
	
	@connect(mapStateToProps, mapDispatchToProps)

先走action.js  再走reducer更新state

#### 判断对象是否是空对象 ####

	Object.keys({}).length

#### 深度判断类型 ####

Object.prototype.toString.call({}) 

 proLableVal&&Array.isArray (proLableVal)

#### chrome调试代码 ####

linux 系统：ctrl+shift+I或者f12

// 完成更新后 this.props 最新的
  componentDidUpdate (prevProps) {
	