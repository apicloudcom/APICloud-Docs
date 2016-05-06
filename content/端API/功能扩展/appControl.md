/*
Title: appControl
Description: appControl
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：开发者</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>

<div class="outline">
[JumpApp](#a1)

[BindService](#a2)

[GetAppRunTime](#a3)

[SetUpAppShopTime](#a4)

[getAllAppNames](#a5)
</div>

#**概述**

appControl 封装了在 android 系统上跳转应用、检测本机上的应用在前台运行的时间，以及检测应用是否安装等功能。


#**JumpApp**<div id="a1"></div>

直接跳转进入应用

JumpApp({params}, callback(ret, err))

##params

packageName:

- 类型：字符串
- 描述：要跳转应用的包名


##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    result:            //数字类型：是否跳转成功, `1` 成功跳转, `0` 未成功跳转
}
```

##示例代码

```js
var appControl = api.require('appControl');
appControl.JumpApp({
	packageName: 'com.apicloud.xxx'
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


#**BindService**<div id="a2"></div>

用于开启检测应用在前台跑的时长的服务

BindService({params}, callback)

##params

packageName:

- 类型：字符串
- 描述: 要查看的应用的包名


##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	parms:		//数字类型：`0` 表示已经开启过这个服务, `1` 表示正在开启服务,都会把要检测的包名放入列表中
}
```


##示例代码

```js
var appControl = api.require('appControl');
appControl.BindService({
	packageName: 'com.apicloud.xxx'
}, function(ret, err){	
    if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##补充说明

可以检测多个，会把要检测的包名放入队列中，在 android 5.0 之后需要开启应用的权限( 有权查看其他应用使用 )

##可用性

Android 系统

可提供的1.0.0及更高版本

#**GetAppRunTime**<div id="a3"></div>

获得应用在前台运行的时长

GetAppRunTime({params}, callback(ret, err))

##params

packageName:

- 类型：字符串
- 描述：要查看的 app 的包名


##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
 	parms:         //字符串类型：如果没有开启服务或服务已停止，会返回 "Server Stoped" 否则返回 ""
	SumTime:       //数字类型：app 在开启计时到当前的时间长度（单位毫秒）
}
```

##示例代码

```js
var appControl = api.require('appControl');
appControl.GetAppRunTime({
	packageName: 'com.apicloud.xxxx'
}, function(ret, err){
	if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##补充说明

需要先调用 BindService 开始检测一个 APP

##可用性

Android 系统

可提供的1.0.0及更高版本

#**SetUpAppShopTime**<div id="a4"></div>

关闭没有必要检测的 APP

SetUpAppShopTime({params}, callback(ret, err))

##params

packageName:

- 类型：字符串
- 描述：要停止检测的应用包名


##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
        parms:              //字符串类型：如果没有服务则返回 Server Stoped
                            //有开启过此包名的检测则停止并返回 Stop success
                            //没有检测过返回 No PackageName Data
}
```
##示例代码

```js
var appControl = api.require('appControl');
appControl.SetUpAppShopTime({
	packageName: 'com.apicloud.xxxx'
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

#**getAllAppNames**<div id="a5"></div>

查看本机是否安装了这个应用

getAllAppNames({params}, callback(ret, err))

##params

packageName:

- 类型：字符串
- 描述：要检测的应用包名

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    result:            //数字类型：查找应用, `1` 存在此应用, `0` 不存在此应用
}
```
##示例代码

```js
var appControl = api.require('appControl');
appControl.getAllAppNames({
	packageName: 'com.apicloud.xxxx'
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