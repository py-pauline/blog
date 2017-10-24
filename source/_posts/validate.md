---
title: jQuery validate学习笔记
date: 2017-10-23 14:17:40
tags: jquery validate
categories: programming
---
目前手头上正在做的一个项目是关于微信服务号的，所以这个validate验证基于WEUI样式库的。

<!-- more -->

#### 导入js库 ####

使用bootstrap提供的cdn引入js库和css库；
	
	<link href="https://cdn.bootcss.com/weui/1.1.2/style/weui.min.css" rel="stylesheet">
	<script src="https://cdn.bootcss.com/jquery/3.2.1/jquery.min.js"></script>
	<script src="https://cdn.bootcss.com/jquery-validate/1.17.0/jquery.validate.js"></script>

#### 使用方式 ####

方式一：将校验规则写在控件中

	<div class="weui-cell">
	    <div class="weui-cell__hd"><label for="firstname" class="weui-label">名字</label></div>
	    <div class="weui-cell__bd">
	    	<input id="firstname" name="firstname" maxlength="10" minlength="2" class="weui-input" type="text">
	    </div>
	</div>


方式二：将校验方法写在js中

	rules:{
		firstname:"required",
		lastname:"required",
		username:{
		required:true,
		minlength:2,
		maxlength:10
		}
	}

#### 具体使用介绍 ####

html代码

 	<form action="" method="" id="commentForm">
        <div class="weui-cells weui-cells_form">
                <div class="weui-cell">
                    <div class="weui-cell__hd"><label for="firstname" class="weui-label">名字</label></div>
                    <div class="weui-cell__bd">
                        <input id="firstname" name="firstname" maxlength="10" minlength="2" class="weui-input" type="text">
                    </div>
                </div>
                <div class="weui-cell">
                    <div class="weui-cell__hd">
                        <label for="lastname" class="weui-label">姓氏</label>
                    </div>
                    <div class="weui-cell__bd">
                        <input name="lastname" id="lastname" class="weui-input"  type="text">
                    </div>
                </div>
              
                <div class="weui-cell">
                        <div class="weui-cell__hd">
                            <label for="username" class="weui-label">用户名</label>
                        </div>
                        <div class="weui-cell__bd">
                            <input name="username" id="username" class="weui-input"  type="text">
                        </div>
                </div>
                <div class="weui-cell">
                    <div class="weui-cell__hd">
                        <label for="password" class="weui-label">密码</label>
                    </div>
                    <div class="weui-cell__bd">
                        <input name="password" id="password" class="weui-input"  type="text">
                    </div>
                </div>
                <div class="weui-cell">
                    <div class="weui-cell__hd">
                        <label for="confirm_password" class="weui-label">验证密码</label>
                    </div>
                    <div class="weui-cell__bd">
                        <input name="confirm_password" id="confirm_password" class="weui-input"  type="text">
                    </div>
                </div>
                <div class="weui-cell">
                    <div class="weui-cell__hd">
                        <label for="email" class="weui-label">Email</label>
                    </div>
                    <div class="weui-cell__bd">
                        <input name="email" id="email" class="weui-input"  type="email">
                    </div>
                </div>
                <label for="agree" class="weui-agree">
                        <input name="agree" id="agree" type="checkbox" class="weui-agree__checkbox">
                        <span class="weui-agree__text">
                            阅读并同意<a href="javascript:void(0);">《相关条款》</a>
                        </span>
                </label>
                <label for="newsletter" class="weui-agree">
                        <input name="newsletter" id="newsletter" type="checkbox" class="weui-agree__checkbox">
                        <span class="weui-agree__text">随便你勾选不</span>
                </label>
                <h4>至少选择两个</h4>
                <div>
                    <label for="topic_marketflash" class="weui-agree">
                            <input name="topic[]" id="topic_marketflash" type="checkbox" value="diyige" class="weui-agree__checkbox">
                            <span class="weui-agree__text">苹果</span>
                    </label>
                    <label for="topic_marketflash2" class="weui-agree">
                            <input name="topic[]" id="topic_marketflash2" type="checkbox" value="1" class="weui-agree__checkbox">
                            <span class="weui-agree__text">梨</span>
                    </label>
                    <label for="topic_marketflash3" class="weui-agree">
                            <input name="topic[]" id="topic_marketflash3" type="checkbox"  value="1" class="weui-agree__checkbox">
                            <span class="weui-agree__text">香蕉</span>
                    </label>
                    <label for="topic_marketflash4" class="weui-agree">
                            <input name="topic[]" id="topic_marketflash4" type="checkbox"   value="1" class="weui-agree__checkbox">
                            <span class="weui-agree__text">西瓜</span>
                    </label>
                </div>

            </div>
            <input type="submit" value="submit提交">
            <input type="button" onclick="savedate()" value="ajax提交">
            <button id="test">click me</button>
    </form>
 

style样式（报错提示）

  	input.error { border: 1px solid red; }
    label.error {
        background:url("../image/page/unchecked.gif") no-repeat 0px 0px;
        padding-left: 16px;
        padding-bottom: 2px;
        font-size: 14px;
        color: #EA5200;
    }
    label.checked {
    background:url("../image/page/checked.gif") no-repeat 0px 0px;
    }

js代码

 	 $("#test").bind("click",test())
        function test(){
            var a = $("form").serializeArray();
                var objparm = new Object();
                for(var i =0;i<a.length;i++){
                    objparm[a[i].name]=a[i].value;
                }
                console.log(objparm);
        }
        $.validator.setDefaults({
            submitHandler:function(){
                alert("submit提交事件成功") ;
                //form.submit();//submit提交
                //$(form).savedate();//ajax提交
               
            }
        });
        $(function(){
            $("#commentForm").validate({//校验规则写在js代码中
                // 在键盘按下并释放及提交后验证提交表单
               // ignore: ".ignore",//忽略验证的的input，但未生效
                errorPlacement:function(error,element){//更改错误信息显示的位置
                    $(element).closest("form").find("label[for='"+element.attr("id")+"']").append(error);
                },
                //debug:true,//只验证不提交表单(多用于调试的时候)
               // errorElement:"span", //提示的标签
                rules:{
                    firstname:"required",
                    lastname:"required",
                    username:{
                        required:true,
                        minlength:2,
                        maxlength:10
                    },
                    password:{
                        required:true,
                        minlength:5
                    },
                    confirm_password:{
                        required:true,
                        minlength:5,
                        equalTo:"#password"
                    },
                    email:{
                        required:true,
                        email:true
                    },
                    "topic[]":{
                        required:"#newsletter:checked",
                        minlength:2
                    },
                    agree:{
                        required:true
                    }
                },
                messages:{
                    firstname: "请输入您的名字",
                    lastname: "请输入您的姓氏",
                    username: {
                      required: "请输入用户名",
                      minlength: "用户名必需由两个字母组成"
                    },
                    password: {
                      required: "请输入密码",
                      minlength: "密码长度不能小于 5 个字母"
                    },
                    confirm_password: {
                      required: "请输入密码",
                      minlength: "密码长度不能小于 5 个字母",
                      equalTo: "两次密码输入不一致"
                    },
                    email: "请输入一个正确的邮箱",
                    agree: "请接受我们的声明",
                    topic: "请选择两个主题"
                  }
            });
        })
        //ajax提交
        //参数设置
        function savedate(){
            //获取data方法一：
            var data = {};
            var myname = $("#cname").val();
            data["name"] = myname;
            //获取data方法二
            //获取所有的参数数组
            var paramArr = $("form").serializeArray();
            //拼接参数对象
            var paramObj =new Object();  
            for(var i = 0 , len = paramArr.length ; i < len ; i++){
                paramObj[paramArr[i].name] = paramArr[i].value;
            }
            $.ajax({
                url:"../../update",
                data: data,
                dataType:"json",
                success:function(result){
                    if(result.status != 0){
                        alert(result.msg);
                        result;
                    }
                    alert("数据提交成功")
                },
                error:function(data,status,e){//服务器响应失败处理函数
                    alert(e);
                }
            })
        }

#### 点击submit提交后的页面效果 ####

![](http://oibijaovc.bkt.clouddn.com/QQ%E6%88%AA%E5%9B%BE20171024172804.png)