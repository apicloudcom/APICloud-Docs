/*
Title: pasteboard
Description: pasteboard
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

#**概述**

pasteboard封装了iOS和Android平台的数据复制功能

#**paste**

调用复制功能

paste({params}，callback(ret, err))

##params

value：

- 类型：字符串
- 默认值：无
- 描述：需要复制的内容，不能为空，否则复制失败

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:true           //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    code:0    //错误码
    msg:""    //错误描述
}
```

##示例代码

```js
var paste = api.require('pasteboard');
var param = {value:'Hello paste'};
demo.paste(param,function(ret,err){
	if (ret.status){
		api.alert({
			title: '返回信息',
			msg: 'statues:'+ret.status,
			buttons:['确定']
		},function(ret,err){
		});
	} else{
	api.alert({
		title: '返回信息',
		msg: 'msg:'+ret.msg+' code:'+err.code,
		buttons:['确定']
	},function(ret,err){
		});
	}
})
```

##补充说明

数据复制

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

