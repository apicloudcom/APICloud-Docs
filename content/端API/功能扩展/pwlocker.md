/*
Title: pwlocker
Description: pwlocker
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">方法</a></li>
</ul>
<div id="method-content">

<div class="outline">

[openSetView](#openSetView)
[openEnterView](#openEnterView)

</div>

# 概述 #

本模块是一个矩阵锁，可加锁屏幕，让用户通过输入特定的矩阵路线来解锁屏幕。

## openSetView<div id="openSetView"></div>

打开设置密码页面

openSetView (params, callback)

## params ##
bg：

- 类型：字符串
- 默认值：rgba(0,0,0,0)
- 描述：背景设置，支持img，#，rgb，rgba，可为空

tips：

- 类型：json对象
- 默认值：见内部字段
- 描述：提示文字配置，可为空 
- 内部字段：

   		size：	//提示文字大小，数字类型，默认16，可为空
    	color:   //提示文字颜色，字符串,默认#FFFFFF,支持#,rgb,rgba，可为空

matrix：

- 类型：json对象
- 默认值：见内部字段
- 描述：矩阵配置，可为空
- 内部字段:

```
{
    row://矩阵行数，数字类型，默认3，可为空
    column: //矩阵列数，数字类型，默认3，可为空
}
```

anim：

- 类型：布尔值
- 默认值：true
- 描述：打开时是否添加从下往上弹出的动画，可为空

## callback(ret, err)
ret：

- 类型：JSON对象
- 内部字段：

```
	{
		status:       //设置手势密码成功
    }
```
    

err：

- 类型：JSON对象
- 内部字段：
{
	msg:        //错误描述
}


### 示例代码 ###

```js
var pwlocker = api.require("pwlocker");
var param = {
			bg:'#232736',
			tips : {
				text:'我是一个提示',
				size:16,
				color:'#696969'
			},
			matrix:{
				row:4,
				column:4
			},
			anim : true
		};
	
var resultCallback = function(ret, err){
    if(ret.status){
        alert("设置的密码为:" + ret.key);
        key = ret.key;
    } else{
        alert({msg:err.msg});
    }
}

pwlocker.openSetView(param,resultCallback);
```			

### 可用性 ###

Android系统

可提供的 1.0.0 及更高版本

## openEnterView<div id="openEnterView"></div>
打开验证手势密码视图

openSetView (params, callback)

## params ##
bg：

- 类型：字符串
- 默认值：rgba(0,0,0,0)
- 描述：背景设置，支持img，#，rgb，rgba，可为空

tips：

- 类型：json对象
- 默认值：见内部字段
- 描述：提示文字配置，可为空 
- 内部字段：

```
{
   		size：	//提示文字大小，数字类型，默认16，可为空
    	color:   //提示文字颜色，字符串,默认#FFFFFF,支持#,rgb,rgba，可为空
}
```

matrix：

- 类型：json对象
- 默认值：见内部字段
- 描述：矩阵配置，可为空
- 内部字段:

```
{
    row://矩阵行数，数字类型，默认3，可为空
    column: //矩阵列数，数字类型，默认3，可为空
 }
```

anim：

- 类型：布尔值
- 默认值：true
- 描述：打开时是否添加从下往上弹出的动画，可为空

key：

- 类型：字符串
- 默认值：无
- 描述：要验证的密码

## callback(ret, err) ##
ret：

- 类型：JSON对象
- 内部字段：

```
{
	status:       //设置手势密码成功
}    
```

err：

- 类型：JSON对象
- 内部字段：

```
{
	msg:        //错误描述
}
```

### 示例代码 ###

```js
var pwlocker = api.require("pwlocker");

var param = {
			bg:'#232736',
			tips : {
				size:16,
				color:'#696969'
			},
			matrix:{
				row:4,
				column:4
			},
			anim : true,
			key : key
		};
	
var resultCallback = function(ret, err){
    if(ret.status){
    	if(key == ret.key){
    		alert("密码正确");
    	}else{
    		alert("密码错误");
    	}
    } else{
        alert({msg:err.msg});
    }
};

pwlocker.openEnterView(param,resultCallback);
```	

### 可用性 ###

Android系统

可提供的 1.0.0 及更高版本