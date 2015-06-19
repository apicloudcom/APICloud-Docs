/*
Title: tencentPush
Description: 封装腾讯信鸽推送的SDK.
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#basic-content">方法</a></li>
	<li class=""><a href="#const-content">常量</a></li>
</ul>
<div id="basic-content">

<div class="outline">
[registerPush](#a1)
[config](#a2)
[unregisterPush](#a3)
[setTag](#a4)
[delTag](#a5)
[addlocalNotification](#a6)
[clearLocalNotifications](#a7)
[cancelNotifaction](#a8)
[setListener](#a9)
</div>

#**概述**

本模块封装腾讯信鸽推送 [http://xg.qq.com](http://xg.qq.com) 的SDK，只需要1行代码便可实现免费、实时、专业的推送功能，支持通知、消息透传、本地通知、账号绑定、默认标签等。

暂仅支持安卓.

#**快速接入**
## 配置
腾讯信鸽官方网站：[http://xg.qq.com](http://xg.qq.com)
使用本模块之前，需要先配置config文件的Feature，见下
- 名称：tencentPush
- 参数：urlScheme
- 描述：配置腾讯信鸽用于标识APP身份的accessId和accessKey，需要事先在信鸽官方注册
- 配置示例：

```
<feature name="tencentPush">
	<param name="android_accessId" value="2100064624" />
    <param name="android_accessKey" value="AZ4EZQ533X9A" />
</feature>
```
字段描述：
- param-urlScheme：声明此字段为URL Scheme类型
- param-value：对应urlScheme类型的值。通过腾讯信鸽官方网站申请
	A) android_accessId：信鸽Android平台的accessId，21开头的Int类型
	
	B）android_accessKey：信鸽Android平台的accessKey，A开头的字符串
```
	
## 1行代码接入
// 具体细节见registerPush说明
// 若需要打开信鸽debug日志，见config说明

```js
api.require('tencentPush').registerPush(function(ret, err){
    if(ret.status){
        alert("注册成功，token为："+ret.token);
    }else{
        alert("注册失败，错误码："+err.code+"，错误信息："+err.msg);
    }
});
```

#**registerPush**<div id="a1"></div>

向后台注册设备信息，使得该终端能够接收推送
本API根据不同的参数可以实现以下3个功能: 
- 将设备注册到信鸽后台
- 注册设备并绑定账号（需要通过参数传递）
- 注册设备并解除账号的绑定关系

registerPush(params, callback)

##params

### account

- 类型：字符串
- 默认值: 无; 若为”*”表示取消账号绑定.
- 描述: 注册设备时需要绑定的账号；若为空表示只注册设备不绑定账号.

##callBack

### ret

- 类型：JSON 对象
- 默认值: 无
- 内部字段: 

```
	{
		status:true ,// 操作状态值，成功：true；失败：false		token: ""	 // 操作成功后，返回设备的唯一标识符token；Android为40位长度字符串；
	}
```

### err：

- 类型：JSON对象

内部字段：

```js
{
    msg:""       //错误描述
}
```

##示例代码

```js
// 注册设备
var tencentPush = api.require('tencentPush');

var resultCallback = function(ret, err){
    if(ret.status){
        alert("注册成功，token为："+ret.token);
    }else{
        alert("注册失败，错误码："+err.code+"，错误信息："+err.msg);
    }
};

tencentPush.registerPush(resultCallback);


// 注册设备并绑定用户账号
var tencentPush = api.require('tencentPush');

var resultCallback = function(ret, err){
    if(ret.status){
        alert("注册成功，token为："+ret.token);
    }else{
        alert("注册失败，错误码："+err.code+"，错误信息："+err.msg);
    }
};

// 需要绑定的账号，若为"*"表示解除之前的账号绑定
var params = {account:"testAccount"};
tencentPush.registerPush(params, resultCallback);

// 解除设备绑定的账号
var tencentPush = api.require('tencentPush');
var resultCallback = function(ret, err){
    if(ret.status){
        alert("注册成功，token为："+ret.token);
    }else{
        alert("注册失败，错误码："+err.code+"，错误信息："+err.msg);
    }
};

// 需要绑定的账号，若为"*"表示解除之前的账号绑定
var params = {account:"*"};
tencentPush.registerPush(params, resultCallback);
```

##补充说明

- registerPush实现设备在后台的注册，只要注册成功，便可接收推送；
- registerPush可以多次调用；
- 账号指的是APP本身的账号体系，可以是任意的字符串；只有绑定账号才能针对账号的推送；建议有登陆或自动登陆功能的APP在用户登陆时，绑定账号；
- 一个设备一个应用只能绑定一个账号，若多个账号绑定，以最后一个绑定成功的为准；
- 一个账号可以对应多个设备，最多10个；

##可用性

Android系统

可提供的1.1.0及更高版本

#**config**<div id="a2"></div>

配置相关的内容, 如是否打开调试模式.

config(params)

##params

### debug

- 类型：布尔
- 默认值: false
- 描述: 是否打开信鸽debug；true：开启；false：关闭；上线时请保持关闭.

##示例代码

```js
// 打开信鸽调试模式
var tencentPush = api.require('tencentPush');
var param = {debug:true};
tencentPush.config(param);
```

##补充说明

上线时请保持关闭.

##可用性

Android系统

可提供的1.1.0及更高版本

#**unregisterPush**<div id="a3"></div>

向后台发送反注册包，将该设备从后台的注册信息表中删除，不再接收推送。

unregisterPush(callback)

##callBack

### ret

- 类型：JSON 对象
- 默认值: 无
- 内部字段: 

```
	{
		status:true // 操作状态值，成功：true；失败：false
	}
```

### err：

- 类型：JSON对象

内部字段：

```js
{
    code:1001,       //错误码（详见错误码常量）
    msg:""       	//错误描述
}
```

##示例代码

```js
// 反注册设备
var tencentPush = api.require('tencentPush');
var resultCallback = function(ret, err){
    if(ret.status){
        alert("反注册成功，token："+ret.token);
    }else{
        alert("反注册失败，错误码："+err.code+"，错误信息："+err.msg);
    }
};
tencentPush.unregisterPush(resultCallback);
```

##补充说明

反注册后，将不再接收任何的推送.

##可用性

Android系统

可提供的1.1.0及更高版本

#**setTag**<div id="a4"></div>

设置标签

setTag(params, callback)

##params

### tag

- 类型：字符串
- 默认值: 无
- 描述: 待设置的标签名字，不能为空 

##callBack

### ret

- 类型：JSON 对象
- 默认值: 无
- 内部字段: 

```
{
	status:true,    // 操作状态值，成功：true；失败：false
	tag:""			 // 设置成功的标签名
}
```

### err：

- 类型：JSON对象

内部字段：

```js
{
    code:1001,      //错误码（详见错误码常量）
    msg:""       	//错误描述
}
```

##示例代码

```js
// 设置标签
var tencentPush = api.require('tencentPush');

var resultCallback = function(ret, err){
    if(ret.status){
        alert("标签设置成功，标签名："+ret.tag);
    }else{
        alert("标签设置失败，错误码："+err.code+"，错误信息："+err.msg);
    }
};
var param = {tag:"tagName"};

tencentPush.setTag(param, resultCallback);
```

##补充说明

无

##可用性

Android系统

可提供的1.1.0及更高版本

#**delTag**<div id="a5"></div>

删除标签

delTag(params, callback)

##params

### tag

- 类型：字符串
- 默认值: 无
- 描述: 待删除的标签名字，不能为空 

##callBack

### ret

- 类型：JSON 对象
- 默认值: 无
- 内部字段: 

```
{
	status:true,    // 操作状态值，成功：true；失败：false
	tag:""			 // 删除成功的标签名
}
```

### err：

- 类型：JSON对象

内部字段：

```js
{
    code:1001,       //错误码（详见错误码常量）
    msg:""       	//错误描述
}
```

##示例代码

```js
// 设置标签
var tencentPush = api.require('tencentPush');
var resultCallback = function(ret, err){
	if(ret.status){
		alert("标签删除成功，标签名："+ret.tag);
	}else{
		alert("标签删除失败，错误码："+err.code+"，错误信息："+err.msg);
	}
};
var param = {tag:"tagName"};
tencentPush.delTag(param, resultCallback);
```

##补充说明

无

##可用性

Android系统

可提供的1.1.0及更高版本

#**addlocalNotification**<div id="a6"></div>

添加本地通知

addlocalNotification(params, callback)

##params

### title

- 类型：字符串
- 默认值: 无
- 描述: 通知栏中展示的通知标题，不能为空

### content

- 类型：字符串
- 默认值: 无
- 描述: 通知栏中展示的正文内容，不能为空

### date

- 类型：字符串
- 默认值: 无
- 描述: 通知展示的日期，格式YYYYMMDD，如”20150127”，不能为空

### hour

- 类型：字符串
- 默认值: 无
- 描述: 通知展示的时间，小时，格式HH，如”15”，不能为空

### min

- 类型：字符串
- 默认值: 无
- 描述: 通知展示的时间，分钟，格式MM，如”15”，不能为空

### customContent

- 类型：JSON字符串
- 默认值: 无
- 描述: 点击通知时，activity获取到的自定义key-value

### activity

- 类型：字符串
- 默认值: 无
- 描述: 待打开的activity，默认为lancher

### ring

- 类型：数字
- 默认值: 1
- 描述: 是否响铃，1：是；0：否

### vibrate

- 类型：数字
- 默认值: 1
- 描述: 是否振动，1：是；0：否

##callBack

### ret

- 类型：JSON 对象
- 默认值: 无
- 内部字段: 

```
{
	status:true,        // 操作状态值，成功：true；失败：false
	notiId: ""			// 通知的id；
}
```

### err：

- 类型：JSON对象

内部字段：

```js
{
    code:-1,       	//错误码
    msg:""       	//错误描述
}
```

##示例代码

```js
// 添加本地通知
var tencentPush = api.require('tencentPush');
var params = {
    title : "title", // 标题
    content : "test content",  // 内容
    date : "20150127",  // 日期
    hour : "15",  // 时间
    min	: "15",   // 分钟
    customContent : "{\"key\":\"value\"}",  // 自定义key-value
    activity : "",  // 打开的activity
    ring : 1,       // 是否响铃
    vibrate : 1    // 是否振动
};
var resultCallback = function(ret, err){
    if(ret.status){
        alert("添加通知成功，通知id："+ret.notiId);
    }else{
        alert("添加本地通知失败，错误码："+err.code+"，错误信息："+err.msg);
    }
};
tencentPush.addlocalNotification(params, resultCallback);
```

##补充说明

无

##可用性

Android系统

可提供的1.1.0及更高版本

#**clearLocalNotifications**<div id="a7"></div>

删除本地通知

clearLocalNotifications()

##示例代码

```js
// 删除本地通知
var tencentPush = api.require('tencentPush');
tencentPush.clearLocalNotifications();
```

##补充说明

无

##可用性

Android系统

可提供的1.1.0及更高版本

#**cancelNotifaction**<div id="a8"></div>

在通知栏清除已展示的通知

cancelNotifaction(params)

##params

### nid

- 类型：数字
- 默认值: -1
- 描述: 待清除的通知id号，-1表示清除所有的通知

##示例代码

```js
// 清除展示的通知
var tencentPush = api.require('tencentPush');
var params = {nid: -1};	
tencentPush.cancelNotifaction(params);
```

##补充说明

无

##可用性

Android系统

可提供的1.1.0及更高版本

#**setListener**<div id="a9"></div>

设置JS的回调函数，一般只用于设置消息透传的回调。

setListener(params, callback)

##params

### name

- 类型：字符串
- 默认值: ”message”，取值具体见下
  - message：设置消息透传的回调
  - notifactionShow：设置通知被展示的回调
  - notifactionClick：设置通知被点击的回调
  - notifactionClear：设置通知被清除的回调
  
- 描述: 设置回调函数，当操作发生时（通常是接收到透传消息，又称消息命令字）的回调接口 

##callBack(ret)

### ret

- 类型：JSON 对象
- 默认值: 无
- 内部字段: 

```
{
 title: "",			// 标题，
 content: "",		// 内容，对于消息透传，前台只有本字段
 customContent: "", // 自定义key-value信息
 /* 以下只有通知相关 */
 msgid: "",			// 消息id
 activity: "",		// 通知打开的activity名称
 actionType: 1,		// 通知打开的类型，1：打开某个activity， 默认值；2：打开url；3：打开intent
}
```

##示例代码

```js
// 注册消息透传（消息命令字）的接收回调
var tencentPush = api.require('tencentPush');
var resultCallback = function(ret, err){
	alert("收到透传消息，title："+ret.title+"，content："+ret.content+
"，customContent："+ret.customContent);
};
var params = {name:"message"};	
tencentPush.setListener(params, resultCallback);

// 注册通知被展示的回调
var tencentPush = api.require('tencentPush');
var resultCallback = function(ret, err){
	alert("收到通知被展示的回调，title："+ret.title+"，content："+ret.content+"，customContent："+ret.customContent 
	+ ",activity:"+ret.activity+",actionType:"+ret.actionType+",msgid:"+ret.msgid);
};
var params = {name:"notifactionShow"};	
tencentPush.setListener(params, resultCallback);
tencentPush.registerPush(params, resultCallback);


// 注册通知被点击的回调
var tencentPush = api.require('tencentPush');
var resultCallback = function(ret, err){
	alert("收到通知被点击的回调，title："+ret.title+"，content："+ret.content+"，customContent："+ret.customContent 
	+ ",activity:"+ret.activity+",actionType:"+ret.actionType+",msgid:"+ret.msgid);
}
var params = {name:"notifactionClick"};	
tencentPush.setListener(params, resultCallback);

// 注册通知被清除的回调
var tencentPush = api.require('tencentPush');
var resultCallback = function(ret, err){
	alert("收到通知被清除的回调，title："+ret.title+"，content："+ret.content+"，customContent："+ret.customContent 
	+ ",activity:"+ret.activity+",actionType:"+ret.actionType+",msgid:"+ret.msgid);
}
var params = {name:"notifactionClear"};	
tencentPush.setListener(params, resultCallback);
```

##补充说明

无

##可用性

Android系统

可提供的1.1.0及更高版本

</div>

<div id="const-content">

<div class="outline">
[返回码](#1)
</div>


#**错误码**<div id="3"></div>

错误类型

##取值范围：

值 |含义
----|----
0 |调用成功
2 |参数错误，例如绑定了单字符的别名，或是ios的token长度不对，应为64个字符
20	|鉴权错误
10000|	起始错误
10001	|操作类型错误码，例如参数错误时将会发生该错误
10002	|正在执行注册操作时，又有一个注册操作到来，则回调此错误码
10003	|权限出错
10004	|so出错
10100	|当前网络不可用
10101	|创建链路失败
10102	|请求处理过程中， 链路被主动关闭
10103	|请求处理过程中，服务器关闭链接
10104	|请求处理过程中，客户端产生异常
10105	|请求处理过程中，发送或接收报文超时
10106	|请求处理过程中， 等待发送请求超时
10107 |请求处理过程中， 等待接收请求超时
10108	|服务器返回异常报文
10109	|未知异常，请在QQ群中直接联系管理员，或前往论坛发帖留言
10110	|创建链路的handler为null

</div>