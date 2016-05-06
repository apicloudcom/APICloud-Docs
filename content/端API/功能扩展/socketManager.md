/*
Title: socketManager
Description: socketManager
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>
<div id="method-content">

<div class="outline">
[createSocket](#1)

[closeSocket](#2)

[write](#3)
</div>

#**概述**

socketManager 模块封装了 socket 的创建、关闭、发送数据等操作，使用此模块能实现即时通讯数据收发功能。

#**createSocket**<div id="1"></div>

创建 socket 并进行连接，连接状态以及接收到数据都通过回调返回

createSocket({params}, callback(ret, err))

##params

type：

- 类型：字符串
- 默认值：tcp
- 描述：socket 类型，tcp 或 udp

udpMode：

- 类型：字符串
- 默认值：unicast
- 描述：udp 通讯模式，取值范围为（unicast-单播、multicast-组播、broadcast-广播）

host：

- 类型：字符串
- 默认值：无
- 描述：主机地址，IP 或者域名，不能为空

port：

- 类型：数字
- 默认值：80
- 描述：主机端口

localPort：

- 类型：数字
- 默认值：8282
- 描述：本机绑定的端口，用于udp

timeout：

- 类型：数字
- 默认值：5
- 描述：连接超时时间，单位秒

bufferSize：

- 类型：数字
- 默认值：16
- 描述：缓冲大小，客户端根据自己传输的数据可能的最大值进行设置，单位kb

charset：

- 类型：字符串
- 默认值：utf-8
- 描述：字符集，发送和接收数据时使用此字符集进行编码

returnBase64：

- 类型：布尔
- 默认值：false
- 描述：收到数据时是否返回base64编码后的数据

##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
	sid:			//socket的唯一标识，字符串类型
	state:			//socket状态码，见常量里面的socket状态码，数字类型
	data:			//state为接收数据时的数据，字符串类型
	host：			//udp收到数据时发送方地址
	port：			//udp收到数据时发送方端口
}
```

##示例代码

```js
var socketManager = api.require('socketManager');
socketManager.createSocket({
	host: '192.168.1.100',
	port: 8282
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

可提供的1.0.0及更高版本


#**closeSocket**<div id="2"></div>

关闭 socket 连接

closeSocket({params}, callback(ret, err))

##params

sid：

- 类型：字符串
- 默认值：无
- 描述：通过 createSocket 方法获取得到的 socket 的唯一标识，不能为空

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
	msg:''    //错误描述
}
```
##示例代码

```js
var socketManager = api.require('socketManager');
socketManager.closeSocket({
	sid: '1'
}, function(ret, err){		
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


#**write**<div id="3"></div>

往某个 socket 写入数据

write({params}, callback(ret, err))

##params

sid：

- 类型：字符串
- 默认值：无
- 描述：通过 createSocket 方法获取得到的 socket 的唯一标识，不能为空

data：

- 类型：字符串
- 默认值：无
- 描述：发送的数据，不能为空

base64：

- 类型：布尔
- 默认值：false
- 描述：标识 data 是否是经过 JS 层 base64 处理后的数据，如果是，模块中会将其 decode 后再发送

host：

- 类型：字符串
- 默认值：createSocket 方法里面传的 host
- 描述：主机地址，IP 或者域名，udp 时有效

port：

- 类型：数字
- 默认值：createSocket 方法里面传的 port
- 描述：主机端口，udp 时有效

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
	msg:''    //错误描述
}
```

##示例代码

```js
var socketManager = api.require('socketManager');
socketManager.write({
	sid: '1',
	data: '你好'
}, function(ret, err){		
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
</div>

<div id="const-content">
#**socket状态码**

socket状态码。数字类型

##取值范围：

- 101         //创建成功
- 102         //连接成功
- 103         //收到数据
- 201         //创建失败
- 202         //连接失败
- 203         //异常断开
- 204         //正常断开
- 205         //发生未知错误断开
