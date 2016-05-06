/*
Title: screenLock
Description: screenLock
*/

<p style="color: #ccc;margin-bottom: 30px;">来自于：开发者</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[show](#1)

[set](#2)

</div>

#**概述**

screenLock 封装图案解锁功能，使用此模块可轻松实现图案解锁功能，本模块主要实现九宫格图案解锁功能，可自定义背景颜色，只需要通过 set 方法设置图案密码，并通过 show 方法显示图案解锁界面即可简单实现，可用在某些进入时需要验证图案密码的应用，例如支付类 APP。使用图案解锁前，请先通过 set 方法让 app 使用者设置图案密码。


#**show**<div id="1"></div>

显示图案解锁界面

show({params}, callback(ret, err))

##params

color：

- 类型：字符串
- 默认值：#ff0000
- 描述：背景颜色，支持 argb，rgb，# 可为空

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	status:111           //111：表示密码正确，110：表示密码错误，112:表示取消了操作
}
```

err：

- 类型：JSON 对象

内部字段：

```js
{
    code:0    //错误码
    msg:''    //错误描述
}
```

##示例代码

```js
var screenLock = api.require('screenLock');
screenLock.show({
   color : '#f00'
}, function(ret, err){		
	if( ret ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```

##可用性

Android 系统

可提供的1.0.0及更高版本


#**set**<div id="2"></div>

设置图案解锁密码

set({params}, callback(ret, err))

##params

color：

- 类型：字符串
- 默认值：#ff000000
- 描述：背景颜色，支持argb，rgb，#可为空

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	status:111		//111:表示图案密码设置成功
}
```

err：

- 类型：JSON 对象

内部字段：

```js
{
    code:0       //错误码（详见错误码常量）
    msg: ''      //错误描述
}
```

##示例代码

```js
var screenLock = api.require('screenLock');
screenLock.set({
   color : '#f0f'
}, function(ret, err){		
	if( ret ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```

##可用性
Android 系统

可提供的1.0.0及更高版本
