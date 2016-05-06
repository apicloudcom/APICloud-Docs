/*
Title: push
Description: push
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[bind](#1)

[unbind](#2)

[joinGroup](#3)

[leaveGroup](#4)

[leaveAllGroup](#5)

[setListener](#6)

[removeListener](#7)

[setPreference](#8)
</div>

#**概述**

push模块提供官方推送的相关操作，包括推送设置、监听推送消息、绑定用户、加入群组、退出群组等功能

#**bind**<div id="1"></div>

将来自第三方业务系统（比如您自己的商城、O2O、OA、CRM系统等）的用户信息绑定至APICloud推送服务器，实现推送给指定用户的功能（即“单推”）。

bind({params}, callback(ret, err))

##params

userId：

- 类型：字符串
- 默认值：无
- 描述：用户Id，来自第三方业务系统

userName：

- 类型：字符串
- 默认值：无
- 描述：用户名称，来自第三方业务系统

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	status:true           //操作成功状态值
}
```

err：

- 类型：JSON 对象

内部字段：

```js
{
	msg:””    //错误描述
}
```

##示例代码

```js
var push = api.require('push');
push.bind({
	userName: 'testName',
	userId: 'testId'
}, function(ret, err){
	if( ret ){
        alert( JSON.stringify( ret) );
    }else{
        alert( JSON.stringify( err) );
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**unbind**<div id="2"></div>

解除已绑定用户的绑定状态，解除绑定后，无法再指定该用户推送消息。

unbind({params}, callback(ret, err))

##params

userId：

- 类型：字符串
- 默认值：无
- 描述：用户Id，来自业务系统

userName：

- 类型：字符串
- 默认值：无
- 描述：（可选项）用户名称，来自业务系统

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	status:true           //操作成功状态值
}
```

err：

- 类型：JSON 对象

内部字段：

```js
{
	msg:””    //错误描述
}
```

##示例代码

```js
var push = api.require('push');
push.unbind({
	userName: 'testName',
	userId: 'testId'
}, function(ret, err){
	 if( ret ){
        alert( JSON.stringify( ret) );
     }else{
        alert( JSON.stringify( err) );
     }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**joinGroup**<div id="3"></div>

加入某个群组。加入该群组后，当服务器向该群组推送消息时，所有在该群组内的用户都会收到推送，非该群组用户不会收到推送。默认所有用户都加入"all"群组。

joinGroup({params}, callback(ret, err))

##params

groupName：

- 类型：字符串
- 默认值：无
- 描述：群组名称

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	status:true           //操作成功状态值
}
```

err：

- 类型：JSON 对象

内部字段：

```js
{
	msg:””    //错误描述
}
```

##示例代码

```js
var push = api.require('push');
push.joinGroup({
	groupName: 'department'
}, function(ret, err){
	 if( ret ){
        alert( JSON.stringify( ret) );
     }else{
        alert( JSON.stringify( err) );
     }
});
```

##补充说明

绑定群组

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**leaveGroup**<div id="4"></div>

退出某个群组。退出该群组后，服务器向该群组推送消息时，此用户将不再收到推送。

leaveGroup({params}, callback(ret, err))

##params

groupName：

- 类型：字符串
- 默认值：无
- 描述：群组名称

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	status:true           //操作成功状态值
}
```

err：

- 类型：JSON 对象

内部字段：

```js
{
	msg:””    //错误描述
}
```

##示例代码

```js
var push = api.require('push');
push.leaveGroup({
	groupName: 'department'
}, function(ret, err){
	 if( ret ){
        alert( JSON.stringify( ret) );
     }else{
        alert( JSON.stringify( err) );
     }
});
```

##补充说明

移除群组绑定

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**leaveAllGroup**<div id="5"></div>

一次性退出所有通过joinGroup加入的群组。

leaveAllGroup(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	status:true           //操作成功状态值
}
```

err：

- 类型：JSON 对象

内部字段：

```js
{
	msg:””    //错误描述
}
```

##示例代码

```js
var push = api.require('push');
push.leaveAllGroup(function( ret, err ){
	 if( ret ){
        alert( JSON.stringify( ret) );
     }else{
        alert( JSON.stringify( err) );
     }
});
```

##补充说明

移除所有群组绑定

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**setListener**<div id="6"></div>

注册监听推送消息。
注册该监听后，在应用启动的状态下，“消息”类型的推送，将直接交给该函数的回调，由开发人员自行处理推送消息，不自动弹出通知到手机状态栏。如果移除监听，则又会自动弹出通知到手机状态栏；在应用退出的状态下，“消息”类型的推送，APICloud引擎也会自动弹出通知到手机状态栏。
“通知”类型的推送则会直接弹出通知到手机状态栏，不会交给监听函数的回调。

setListener(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	data:[]           //消息内容，对象数组
}
```

##示例代码

```js
var push = api.require('push');
push.setListener(function( ret, err ){
	 if( ret ){
        alert( JSON.stringify( ret) );
     }else{
        alert( JSON.stringify( err) );
     }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**removeListener**<div id="7"></div>

移除对推送消息的监听。移除监听后，收到“消息”类型的推送，APICloud引擎将自动弹出通知到手机状态栏

removeListener()

##示例代码

 ```js
var push = api.require('push');
push.removeListener();
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**setPreference**<div id="8"></div>

推送偏好设置，如是否允许弹出通知到手机状态栏，推送静默时间，通知提示类型等。

setPreference({param})

##params

notify：

- 类型：布尔
- 默认值：true
- 描述：（可选项）是否弹出消息通知。若设置false，则即使收到推送，也将不再有通知弹出到手机状态栏

updateCurrent：

- 类型：布尔
- 默认值：false
- 描述：（可选项）本次弹出通知是否覆盖更新上一个通知。仅Android平台生效

silenceTime：

- 类型：JSON 对象
- 默认值：无
- 描述：（可选项）设置通知的静默时间段。在设置的时间段内收到推送时，将有通知弹出到手机状态栏，但不会有响铃，震动等行为。设置0，0，0，0则清除设置。仅Android平台生效
- 内部字段：

```js
{
	startHour://静默开始时，取值范围0-23，默认0
	startMinute://静默开始分，取值范围0-59，默认59
	endHour://静默结束时，取值范围0-23，默认0
	endMinute://静默结束分，取值范围0-59，默认59
};
```

defaults：

- 类型：字符串
- 默认值："all"
- 描述：（可选项）设置弹出通知到手机状态栏时伴随的提示类型。仅Android平台生效
- 取值范围："all"-震动和响铃；"sound"-仅响铃；"vibrate"-仅震动。

##示例代码

```js
var push = api.require('push');
push.setPreference({
    notify: true,
    updateCurrent: false,
	silenceTime: {//晚上10点30到第二天上午9点之间静默
		startHour: 22,
		endHour: 9,
		startMinute: 30,
		endMinute: 0
	},
	defaults: 'all'
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
