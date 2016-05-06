/*
Title: micoMqtt
Description: MQTT连接
*/

<p style="color: #ccc;margin-bottom: 30px;">来自于：开发者</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[startMqtt](#1)

[recvMqttMsg](#2)

[stopRecvMqttMsg](#3)

[publish](#4)

[stopMqtt](#5)
</div>

#**概述**

micoMqtt 模块封装了标准的 MQTT 方法，可实现订阅，publish 和停止订阅

#**startMqtt**<div id="1"></div>

打开 MQTT，如果未连接成功，则自动重连直到连接上为止。

startMqtt({params}, callback(ret, err))

##params

host：

- 类型：字符串
- 默认值：无
- 描述：服务器地址，不可为空

username：

- 类型：字符串
- 默认值：无
- 描述：用户名，可为空

password：

- 类型：字符串
- 默认值：无
- 描述：用户密码，可为空


clientID：

- 类型：字符串
- 默认值：无
- 描述：客户端连接mqtt所用到的唯一ID，不可为空


topic：

- 类型：字符串
- 默认值：五
- 描述：订阅的主题，不可为空

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	status: false		//是否成功，布尔类型
}
```

err：

- 类型：JSON 对象

内部字段：

```js
{
	msg: ''    			//错误描述
}
```

##示例代码

```js
var micoMqtt = api.require('micoMqtt');
micoMqtt.startMqtt({
	host: 'http://api.easycc.io',
	username: 'admin',
	password: 'admin',
	clientID: 'aca213caec5c',
	topic: 'd64f517c/out/read/#'
}, function(ret, err){		
	if( ret.status ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```

##补充说明

打开 MQTT 连接

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**recvMqttMsg**<div id="2"></div>

接收消息

recvMqttMsg(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	subs:		 //消息内容，JSON 对象
}
```

err：

- 类型：JSON 对象

内部字段：

```js
{
	msg:''    //错误描述
}
```

##示例代码

```js
var micoMqtt = api.require('micoMqtt');
micoMqtt.recvMqttMsg(function( ret, err ){		
	if( ret.status ){
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


#**stopRecvMqttMsg**<div id="3"></div>

停止接收消息。

stopRecvMqttMsg()

##示例代码

```js
var micoMqtt = api.require('micoMqtt');
micoMqtt.stopRecvMqttMsg();
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**publish**<div id="4"></div>

向服务发送消息并获取回执

publish({params}, callback(ret, err))

##params

topic：

- 类型：字符串
- 默认值：无
- 描述：发布消息的主题，不可为空

command：

- 类型：字符串
- 默认值：无
- 描述：发布消息的指令，不能为空

##callback(ret, err)
ret：

- 类型：JSON 对象

内部字段：

```js
{
	status:false		//是否成功，布尔类型
}
```

err：

- 类型：JSON 对象

内部字段：

```js
{
	msg:''    //错误描述
}
```
##示例代码

```js
var micoMqtt = api.require('micoMqtt');
micoMqtt.publish({
	topic: 'd64f517c/in/read/app1',
	command: '{}'
}, function(ret, err){		
	if( ret.status ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```

##补充说明

发送消息

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**stopMqtt**<div id="5"></div>

关闭 MQTT 连接

stopMqtt(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	status: false		//是否成功，布尔类型
}
```

err：

- 类型：JSON 对象

内部字段：

```js
{
	msg:''    //错误描述
}
```
##示例代码

```js
var micoMqtt = api.require('micoMqtt');
micoMqtt.stopMqtt(function( ret, err ){		
	if( ret.status ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```

##补充说明

关闭 MQTT 连接

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本