/*
Title: clipBoard
Description: clipBoard
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>
<div id="method-content">

<div class="outline">
[set](#a1)

[get](#a2)

[setListener](#a3)

[removeListener](#a4)

</div>

#**概述**

clipBoard模块封装剪切板的相关功能，可实现向剪切版复制、读取字符串相关操作。

#**set**<div id="a1"></div>

设置剪切板内容

set({params}, callback(ret, err))

##params

value：

- 类型：字符串
- 默认值：无
- 描述：要复制到剪切板的字符串，可为空，若为空则清空剪切板

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status://操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg: ""    //错误描述
}
```

##示例代码

```js
var clipBoard = api.require('clipBoard');
clipBoard.set({
	value: 'test'
}, function( ret, err ){
	if( ret ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```

##补充说明

往剪切板复制数据

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**get**<div id="a2"></div>

获取剪切板中的数据

get(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	value:		//从剪切板获取的字符串
	type:		//数据类型，取值范围见数据类型
}
```

##示例代码

```js
var clipBoard = api.require('clipBoard');
clipBoard.get(function( ret, err ){
	if( ret ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```

##补充说明

从剪切板获取值

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**setListener**<div id="a3"></div>

设置剪切板监听

setListener(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	value：//从剪切板获取的字符串
	type：//数据类型，取值范围见数据类型
}
```

##示例代码

```js
var clipBoard = api.require('clipBoard');
clipBoard.setListener(function( ret, err ){
	if( ret ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```

##补充说明

剪切板数据发生变化则触发此函数回调

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**removeListener**<div id="a4"></div>

移除剪切板监听

removeListener()

##示例代码

```js
var clipBoard = api.require('clipBoard');
clipBoard.removeListener ();
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


</div>

<div id="const-content">

#**数据类型**

从剪切板获取的字符串的类型。字符串类型

##取值范围：

- email		//邮箱地址
- phone		//手机号码
- url		//网址
- licence_plate_number //车牌号
- ip_address   //IP地址
- string        //普通字符串


