---
title: react学习记录
date: 2017-06-15 11:45:07
tags: javascript
categories: programming
---

#### 更新ui的唯一方法 ####

ReactDOM.render() 
#### export  ####

export导出时要特别注意！！！默认导出时不需要加中括号

export default TopBar; // 默认导出
mport TopBar from './components/top-bar/topBar'; // 不加中括号 

#### react提高性能的方式 ####

参考项目省市区 
D:\workspace\platform-frontend\src\container\content\basic-data\basic-data.js

#### form表单中 ####


	<FormItem
      {...formItemLayout}
      label="Confirm Password"
    >
      {getFieldDecorator('confirm', {
		initialValue:'默认值',
        rules: [{
          required: true, message: 'Please confirm your password!',
        }, {
          validator: this.compareToFirstPassword,
        }],
      })(
        <Input type="text"/>
      )}
    </FormItem>

	// 直接使用

	<Input defaultValue='我是默认值' type="text"/>



注意！！！

用了getFieldDecorator，直接用initialValue就是初始值的意思，Input之类的组件上就不要用defaultValue。 


#### react优化state ####

这种不需要更新DOM的参数 全部不定义在state中

state --->render更新DOM

	
	constructor(props){
	    super(props);
	    this.params = {
	        pageNum:1,
	        pageSize:10,
	        order:'asc',
	        roleId:this.props.match.params.id
	    }
	}

#### 获取src参数 ####
	
	this.props.match.params.roleId;

#### table分页封装 便于修改样式 ####

	<Table style={{background:'#fff'}}
        rowKey="taskNo" 
        columns={this.columns} 
        dataSource={taskList.rows} 
        onRow={(record) => {
            return {
                onClick:()=> {
                    // console.log(record)
                }
            }
        }}
        pagination={
            Utils.pagination({...taskList,pageNum:this.params.pageNum},(current) =>{
                this.params.pageNum =current;
                this.request();
            })
        }
    />

#### state优化  不涉及dom节点的改变，不存储再state中 ####

存在state中，监测到props有改变，会重新render，降低性能

	 this.setState((prevState) => ({
	        visible:true,
	        editCurrentId:''
	  	})()=>{
		这里才可以取到setstate之后的值
	 })

	this.setState (
      {
        clearModalVisible: false,
        editModalVisible: true,
        eventName: eventName,
      },
      () => {
        console.log (this.state);
        console.log (eventName);
      }
    );


componentWillReceiveProps 每次props更新会触发

#### react路由返回上一级 ####

	@withRouter

    goBack = () => {
        // console.log(this.props)
        this.props.history.go(-1);
    }

