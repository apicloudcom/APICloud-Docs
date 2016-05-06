/*
Title: alarmNotification
Description: alarmNotification
*/

<p style="color: #ccc;margin-bottom: 30px;">来自于：开发者</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[setAlarm](#a1)

[cancelOneAlarm](#a2)

[cancelAllAlarm](#a3)


</div>

#**概述**

alarmNotification 模块封装了定时本地通知提醒功能，开发者可以根据需要设定在一定时间后触发本地通知提醒，设定的提醒可取消，并可设定震动、LED 等参数。

#**setAlarm**<div id="a1"></div>

设定定时本地通知，时间到后触发提醒。

可定制 LED 和震动开关（ LED 和震动仅支持 Android ）。

Android 会在通知栏显示本地通知。

iPhone 会在应用程序运行在后台时进行提示（由于 iPhone 系统限制）。

setAlarm({params}, callback(ret, err))

##params

tickerText：

- 类型：字符串
- 默认值：通知栏提示文字
- 描述：提示时显示的文字，仅对 Android 有效，Android 会将此文本显示在通知栏中

title：

- 类型：字符串
- 默认值：提示标题
- 描述：提示时显示的标题，仅对 Android 有效，iPhone 会自动将标题填写为当前应用程序名称

content：

- 类型：字符串
- 默认值：提示内容
- 描述：提示时显示的内容

interval：

- 类型：数字
- 默认值：10000
- 描述：触发定时本地通知的定时时间，单位为毫秒

isClearOldNotifiy：

- 类型：布尔值
- 默认值：true
- 描述：在设置本条定时本地通知时，是否清除之前所设置的所有通知

isViberate：

- 类型：布尔值
- 默认值：true
- 描述：提示时，是否同时进行震动，仅对 Android 有效

isLed：

- 类型：布尔值
- 默认值：true
- 描述：提示时，是否同时进行 LED 闪烁提醒，仅对 Android 有效

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	status:        // 事件处理状态
	id:            // 如成功设定定时本地通知，id 为当前通知的编号，可用于以后取消通知时使用
}
```

err：

- 类型：JSON 对象

内部字段：

```js
{
    code: 0         //错误码（详见错误码常量）
    msg: ''         //错误描述
}
```

##示例代码

```js
var alarmNotification = api.require('alarmNotification');
alarmNotification.setAlarm({
	isLed: true
}, function(ret, err){		
    if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##补充说明

Android 中尚未实现点击通知后进入应用的功能。

Android 中通知栏提示的图片尚未实现可定制。

##可用性

iOS系统，Android系统

#**cancelOneAlarm**<div id="a2"></div>

取消之前发布的某一条定时本地通知

setAlarm({params}, callback(ret, err))

##params

id：

- 类型：整型
- 默认值：无
- 描述：待取消的定时本地通知 ID，ID 为 setAlarm 方法返回的 ID

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	status: // 事件处理状态
}
```

err：

- 类型：JSON 对象

内部字段：

```js
{
    msg: ''     //错误描述
}
```

##示例代码

```js
var alarmNotification = api.require('alarmNotification');
alarmNotification.cancelAlarm({
	id: 1
}, function(ret, err){		
    if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

#**cancelAllAlarm**<div id="a3"></div>

取消之前发布的所有定时本地通知

cancelAllAlarm(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	status: // 事件处理状态
}
```

err：

- 类型：JSON 对象

内部字段：

```js
{
    msg: ''      //错误描述
}
```

##示例代码

```js
var alarmNotification = api.require('alarmNotification');
alarmNotification.cancelAlarm(function( ret, err ){		
    if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本