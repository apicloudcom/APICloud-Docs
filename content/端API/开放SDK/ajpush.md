/*
Title: ajpush
Description: 极光推送模块
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：极光</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[init](#1)

[setListener](#2)

[removeListener](#3)

[bindAliasAndTags](#4)

[onResume](#5)

[onPause](#6)

[clearNotification](#7)

[setPushTime](#8)

[setSilenceTime](#9)

[stopPush](#10)

[resumePush](#11)

[isPushStopped](#12)

[setBadge](#13)

[getRegistrationId](#14)

[其他重要信息](#15)
</div>

#**概述**

ajpush模块封装了极光推送平台的SDK，使用此模块可实现接收推送通知和透传消息功能。

注意：使用了ajpush或者其他非APICloud提供的push服务，如个推等，请登录官网，在推送设置界面将官方的推送关闭，避免因同时使用多个推送服务而带来设备资源的更多消耗，如耗电量增加等。

###使用极光推送基本流程说明：

1.在极光推送网站（ https://www.jpush.cn ）注册帐号，并创建应用，获取APP_KEY

2.在[config.xml](/APICloud/技术专题/app-config-manual)中配置ajpush feature，填写app_key及channel参数

3.前端调用ajpush模块方法，初始化和监听推送消息。

**使用此模块之前需先配置config文件的Feature，方法如下**

	名称：ajpush
	参数：app_key, channel
	描述：配置极光推送应用信息
```js
	<feature name="ajpush">
		<param name="app_key" value="123456789" />
		<param name="channel" value="your channel" />
	</feature>
```
字段描述:

		1. app_key：通过极光推送网站获得
		2. channel: 渠道号

#**init**<div id="1"></div>

初始化推送服务，只Android有效，ios上会自动初始化

init(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	status:1       //操作成功状态值，1-成功，0-失败
}
```


##示例代码

```js
var ajpush = api.require('ajpush');
	    	
ajpush.init(function(ret) {
	if (ret && ret.status){
		//success
	}
});
```

##补充说明

无。

##可用性

Android系统

可提供的1.0.0及更高版本


#**setListener**<div id="2"></div>

设置消息监听，若iOS应用在前台运行，此时收到推送后也通过此方法回调

setListener(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	id:''               //消息id，可能为空
	title:''     		//消息标题，可能为空
	content:''          //消息内容
	extra:{}            //额外键值对，可能为空
}
```


##示例代码

```js
var ajpush = api.require('ajpush');
ajpush.setListener(
    function(ret) {
	     var id = ret.id;
	     var title = ret.title;
	     var content = ret.content;
	     var extra = ret.extra;
    }
);
```

##补充说明

无。

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**removeListener**<div id="3"></div>

移除消息监听

removeListener()

##示例代码

```js
var ajpush = api.require('ajpush');
ajpush.removeListener();
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**bindAliasAndTags**<div id="4"></div>

绑定用户别名和标签。服务端可以指定别名和标签进行消息推送

bindAliasAndTags({params}, callback(ret, err))

##params

alias：

- 类型：字符串
- 默认值：无
- 描述：别名

tags：

- 类型：字符串数组
- 默认值：无
- 描述：标签列表

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	statusCode:0               //极光推送返回的状态码
}
```

##示例代码

```js
var ajpush = api.require('ajpush');
var param = {alias:'myalias',tags:['tag1','tag2']};
ajpush.bindAliasAndTags(param,function(ret) {
		var statusCode = ret.statusCode;
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**onResume**<div id="5"></div>

通知极光推送SDK当前应用恢复到前台。

本API用于极光推送做“用户使用时长”，“活跃用户”，“用户打开次数”的统计，并上报到服务器，在Portal上展示给开发者。只Android有效

onResume()

##示例代码

```js
api.addEventListener({name:'resume'}, function(ret,err) {
    var ajpush = api.require('ajpush');
	ajpush.onResume();
});
```

##补充说明

无

##可用性

Android系统

可提供的1.0.0及更高版本


#**onPause**<div id="6"></div>

通知极光推送SDK当前应用退入到后台。

本API用于极光推送做“用户使用时长”，“活跃用户”，“用户打开次数”的统计，并上报到服务器，在Portal上展示给开发者。只Android有效

onPause()

##示例代码

```js
api.addEventListener({name:'pause'}, function(ret,err) {
    var ajpush = api.require('ajpush');
	ajpush.onPause();
});
```

##补充说明

无

##可用性

Android系统

可提供的1.0.0及更高版本


#**clearNotification**<div id="7"></div>

清除极光推送发送到状态栏的通知。

clearNotification({params}, callback(ret, err))

##params

id：

- 类型：数字
- 默认值：无
- 描述：待清除的通知id（等同于消息ID），为-1时清除所有，iOS只支持清除所有，不能为空

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	status:1               //操作成功状态值，1-成功，0-失败
}
```

##示例代码

```js
var ajpush = api.require('ajpush');
var param = {id:-1};
ajpush.clearNotification(param,function(ret) {
	if(ret && ret.status){
		//success
	}
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**setPushTime**<div id="8"></div>

设置允许推送时间，只Android有效

setPushTime(params,callback(ret, err))

##params

days：

- 类型：数字数组
- 默认值：无
- 描述：允许推送的日期，0表示星期天，1表示星期一，以此类推，（7天制，数组里面的每项范围为0到6），不能为空

startHour：

- 类型：数字
- 默认值：无
- 描述：允许推送的开始时间（24小时制：startHour的范围为0到23），不能为空

endHour：

- 类型：数字
- 默认值：无
- 描述：允许推送的结束时间（24小时制：endHour的范围为0到23），不能为空

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	status:1               //操作成功状态值，1-成功，0-失败
}
```

##示例代码

```js
var ajpush = api.require('ajpush');
var params = {};
params.days = [1,2];
params.startHour = 8;
params.endHour = 20;
ajpush.setPushTime(params, function(ret) {
	if(ret && ret.status){
		//success
	}
});
```

##补充说明

默认情况下用户在任何时间都允许推送。即任何时候有推送下来，客户端都会收到，并展示。开发者可以调用此 API 来设置允许推送的时间。如果不在该时间段内收到消息，当前的行为是：推送到的通知会被扔掉。

##可用性

Android系统

可提供的1.0.0及更高版本


#**setSilenceTime**<div id="9"></div>

设置通知静默时间，只Android有效

setSilenceTime(params,callback(ret, err))

##params

startHour：

- 类型：数字
- 默认值：无
- 描述：静音时段的开始小时（24小时制，范围：0~23），不能为空

startMinute：

- 类型：数字
- 默认值：无
- 描述：静音时段的开始分钟（范围：0~59），不能为空

endHour：

- 类型：数字
- 默认值：无
- 描述：静音时段的结束小时（24小时制，范围：0~23），不能为空

endMinute：

- 类型：数字
- 默认值：无
- 描述：静音时段的结束分钟（范围：0~59），不能为空

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	status:1               //操作成功状态值，1-成功，0-失败
}
```

##示例代码

```js
var ajpush = api.require('ajpush');
var params = {};
params.startHour = 8;
params.startMinute = 0;
params.endHour = 20;
params.endMinute = 59;
ajpush.setPushTime(params, function(ret) {
	if(ret && ret.status){
		//success
	}
});
```

##补充说明

默认情况下用户在收到推送通知时，客户端可能会有震动，响铃等提示。但用户在睡觉、开会等时间点希望为 "免打扰" 模式，也是静音时段的概念。开发者可以调用此 API 来设置静音时段。如果在该时间段内收到消息，则：不会有铃声和震动。

##可用性

Android系统

可提供的1.0.0及更高版本


#**stopPush**<div id="10"></div>

停止Push推送。只Android有效。

stopPush(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	status:1               //操作成功状态值，1-成功，0-失败
}
```

##示例代码

```js
var ajpush = api.require('ajpush');
ajpush.stopPush(function(ret) {
	if(ret && ret.status){
		//success
	}
});
```

##补充说明

无

##可用性

Android系统

可提供的1.0.0及更高版本


#**resumePush**<div id="11"></div>

恢复Push推送。只Android有效。

resumePush(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	status:1               //操作成功状态值，1-成功，0-失败
}
```

##示例代码

```js
var ajpush = api.require('ajpush');
ajpush.resumePush(function(ret) {
	if(ret && ret.status){
		//success
	}
});
```

##补充说明

无

##可用性

Android系统

可提供的1.0.0及更高版本


#**isPushStopped**<div id="12"></div>

查询当前推送服务是否停止。只Android有效

isPushStopped(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	isStopped:1                  //推送服务是否停止状态，1-停止，0-未停止
}
```

##示例代码

```js
var ajpush = api.require('ajpush');
ajpush.isPushStopped(function(ret) {
	if(ret && ret.isStopped){
		
	}
});
```

##补充说明

无

##可用性

Android系统

可提供的1.0.0及更高版本


#**setBadge**<div id="13"></div>

设置应用图标右上角数字，只iOS有效。

setBadge({params})

##params

badge：

- 类型：数字
- 默认值：无
- 描述：为0时清除应用图标数字，大于0时设置应用图标数字，同时该值会更新到激光推送服务器，不能为空

##示例代码

```js
var ajpush = api.require('ajpush');
ajpush.setBadge({
	badge:0
});
```

##补充说明

无

##可用性

iOS系统

可提供的1.0.0及更高版本


#**getRegistrationId**<div id="14"></div>

集成了JPush SDK的应用程序在第一次成功注册到JPush服务器时，JPush服务器会给客户端返回一个唯一的该设备的标识RegistrationID。JPush SDK会以广播的形式发送RegistrationID到应用程序。应用程序可以把此RegistrationID保存于自己的应用服务器上，然后就可以根据 RegistrationID来向设备推送消息或者通知

getRegistrationId(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	id:''               //RegistrationID
}
```

##示例代码

```js
var ajpush = api.require('ajpush');
ajpush.getRegistrationId(function(ret) {
	var registrationId = ret.id;
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**其他重要信息**<div id="15"></div>

在Android平台，使用极光推送发送通知、消息等类型推送时，极光推送模块会往设备状态栏上发送通知，当通知被点击后，APICloud会将本次推送的内容通过事件监听回调的方式交给开发者。具体使用如下：

```js
api.addEventListener({name:'appintent'}, function(ret,err) {
	if(ret && ret.appParam.ajpush){
		var ajpush = ret.appParam.ajpush;
		var id = ajpush.id;
		var title = ajpush.title;
		var content = ajpush.content;
		var extra = ajpush.extra;
	}
})
```

在iOS平台，使用极光推送发送通知时，若应用在前台运行，则推送内容可以通过setListener方法监听到，若应用在后台，系统会往设备通知栏发送通知，当通知被点击后，APICloud会将本次推送的内容通过事件监听回调的方式交给开发者。具体使用如下：

```js
api.addEventListener({name:'noticeclicked'}, function(ret,err) {
	if(ret && ret.value){
		var ajpush = ret.value;
		var content = ajpush.content;
		var extra = ajpush.extra;
	}
})
```
