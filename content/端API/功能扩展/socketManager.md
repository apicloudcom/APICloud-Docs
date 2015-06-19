/*
Title: socketManager
Description: socketManager
*/

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

socketManager模块封装了socket的创建、关闭、发送数据等操作，使用此模块能实现即时通讯数据收发功能。

#**createSocket**<div id="1"></div>

创建socket并进行连接，连接状态以及接收到数据都通过回调返回

createSocket({params}, callback(ret, err))

##params

type：

- 类型：字符串
- 默认值：tcp
- 描述：socket类型，tcp或udp

udpMode：

- 类型：字符串
- 默认值：unicast
- 描述：udp通讯模式，取值范围为（unicast-单播、multicast-组播、broadcast-广播）

host：

- 类型：字符串
- 默认值：无
- 描述：主机地址，IP或者域名，不能为空

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

- 类型：JSON对象

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
	if(ret){
		var state = ret.state;
		var sid = ret.sid;
		var data = ret.data;
		var stateStr = "";
		if(101 === state){
			stateStr = "创建成功";
		}else if(102 === state){
			stateStr = "连接成功";
		}else if(103 === state){
			stateStr = "收到消息";
		}else if(201 === state){
			stateStr = "创建失败";
		}else if(202 === state){
			stateStr = "连接失败";
		}else if(203 === state){
			stateStr = "异常断开";
		}else if(204 === state){
			stateStr = "正常断开";
		}else if(205 === state){
			stateStr = "发生未知错误";
    	}
		var msg = 'sid: '+sid+'\nstate: '+stateStr+'\ndata: '+(data?data:'');
		api.alert({msg:msg});
	}
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**closeSocket**<div id="2"></div>

关闭socket连接

closeSocket({params}, callback(ret, err))

##params

sid：

- 类型：字符串
- 默认值：无
- 描述：通过createSocket方法获取得到的socket的唯一标识，不能为空

##callback(ret, err)
ret：

- 类型：JSON对象

内部字段：

```js
{
	status:true           //操作成功状态值
}
```
err：

- 类型：JSON对象

内部字段：

```js
{
	msg:""    //错误描述
}
```
##示例代码

```js
var socketManager = api.require('socketManager');
socketManager.closeSocket({
	sid: '1'			//由createSocket方法获取得到
}, function(ret, err){
	if(ret.status){
		api.alert({msg:'关闭成功'});
    }else{
		api.alert({msg:'error'});
    }
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**write**<div id="3"></div>

往某个socket写入数据

write({params}, callback(ret, err))

##params

sid：

- 类型：字符串
- 默认值：无
- 描述：通过createSocket方法获取得到的socket的唯一标识，不能为空

data：

- 类型：字符串
- 默认值：无
- 描述：发送的数据，不能为空

base64：

- 类型：布尔
- 默认值：false
- 描述：标识data是否是经过JS层base64处理后的数据，如果是，模块中会将其decode后再发送

host：

- 类型：字符串
- 默认值：createSocket方法里面传的host
- 描述：主机地址，IP或者域名，udp时有效

port：

- 类型：数字
- 默认值：createSocket方法里面传的port
- 描述：主机端口，udp时有效

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:true           //操作成功状态值
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:""    //错误描述
}
```

##示例代码

```js
var socketManager = api.require('socketManager');
socketManager.write({
	sid: '1',			//由createSocket方法获取得到
	data: '你好'
}, function(ret, err){
	if(ret.status){
		api.alert({msg:'发送成功'});
    }else{
		api.alert({msg:'error'});
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
