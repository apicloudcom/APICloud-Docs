/*
Title: mico
Description: mico
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
    
</ul>
<div id="method-content">

<div class="outline">
[getSSID](#1)

[startEasyLink](#2)

[stopEasyLink](#3)

[startMDNS](#4)

[stopMDNS](#5)

[startMqtt](#6)

[stopMqtt](#7)

[recvMqttMsg](#8)

[stopRecvMqttMsg](#9)

[publishCommand](#10)

[addSubscribe](#11)

[rmSubscribe](#12)

</div>


#**概述**

mico封装了物联网中最重要的接口，如果你使用的是庆科的WIFI设备，那么此模块可助你极快地开发一个智能硬件设备的APP，最主要的功能如下：<br/>
1、让设备联网，我们称之为EasyLink<br/>
2、通过mDNS发现局域网的设备<br/>
3、通过MQTT控制远程设备<br/>
开发时候，按照以下接口的顺序开发即可，或者直接[参考开源项目](http://git.oschina.net/bringmehome/MiCOSDK)项目里也包含完整的开发手册，如果您没有智能硬件，也可以[申请硬件设备](http://mico.io/)。
<br/><br/>
首先，我们需要通过___getSSID___获取设备的SSID，然后将ssid和wifi的密码通过__startEasyLink__发送给设备，如果需要发现局域网的设备我们可以使用___startMDNS___，当设备连上网络，并与自己绑定上时，我们就可以通过___startMqtt___开启mqtt通道，并通过___publishCommand___将指令发送给设备。
<br/><br/>接口清单如下：<br/><br/>
___EasyLink配网___

* [getSSID](#1)
* [startEasyLink](#2)
* [stopEasyLink](#3)

___mDNS发现设备___

* [startMDNS](#4)
* [stopMDNS](#5)

___MQTT控制设备___


* [startMqtt](#6)
* [stopMqtt](#7)
* [recvMqttMsg](#8)
* [stopRecvMqttMsg](#9)
* [publishCommand](#10)
* [addSubscribe](#11)
* [rmSubscribe](#12)

___错误返回码说明___

* [错误码](#13)


#**getSSID**<div id="1"></div>

获取当前手机所连接的WIFI的SSID

getSSID(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    ssid:wifi           //WIFI的名字
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
    error:0    //错误码
}
```

##示例代码

```js
var mico = api.require('mico');
mico.getSSID(function( ret, err ){		
	if( ret ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```

##可用性

Android系统

可提供的1.0.0及更高版本


#**startEasyLink**<div id="2"></div>

将当前的WIFI名称和密码发送给设备，有些设备带回连的这里就会有返回值，不带回连的设备就不会返回任何信息

startEasyLink({params}, callback(ret, err))

##params

wifi_ssid：

- 类型：字符串
- 描述：WIFI的名称，即SSID，不能为空

wifi_password：

- 类型：字符串
- 描述：WIFI的密码，手动输入，不能为空

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	devip:ip		//设备的ip地址
    devinfo:{}      //设备的所有信息，包括名称、状态、属性等
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
    error:0       //错误码（错误返回码说明）
}
```

##示例代码

```js
var mico = api.require('mico');
mico.startEasyLink({
    wifi_ssid : 'mico',
    wifi_password : '88888888'
}, function( ret, err ){        
    if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```
##可用性

Android系统

可提供的1.0.0及更高版本

#**stopEasyLink**<div id="3"></div>

停止EasyLink配网

stopEasyLink(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
    无返回值
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
    error:0      //错误码
}
```

##示例代码

```js
var mico = api.require('mico');
mico.stopEasyLink(function( ret, err ){		
	if( ret ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```

##可用性

Android系统

可提供的1.0.0及更高版本

#**startMDNS**<div id="4"></div>

通过mDNS来搜索局域网设备，需要传入服务的名称

startMDNS({params}, callback(ret, err))

##params

servicename：

- 类型：字符串
- 默认值："_easylink._tcp.local."
- 描述：服务的名称

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    deviceinfo:{}   		//mDNS搜索到的设备的全部信息
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
    error:0      //错误码
}
```

##示例代码

```js
var mico = api.require('mico');
mico.startMDNS({
    servicename: 'mico'
},function( ret, err ){		
	if( ret ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```

##可用性

Android系统

可提供的1.0.0及更高版本

#**stopMDNS**<div id="5"></div>

停止mDNS，不再搜索局域网设备

stopMDNS(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status:Stop      //操作成功
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
    error:0      //错误码
}
```

##示例代码

```js
var mico = api.require('mico');
mico.stopMDNS(function( ret, err ){		
	if( ret ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```

##可用性

Android系统

可提供的1.0.0及更高版本

#**startMqtt**<div id="6"></div>

开启MQTT通道，同时订阅一个主题

startMqtt({params}, callback(ret, err))

##params

host：

- 类型：字符串
- 描述：MQTT服务器的域名，不能为空

port：

- 类型：字符串
- 描述：服务器MQTT的端口，不能为空

username：

- 类型：字符串
- 描述：用户名，不能为空

password：

- 类型：字符串
- 描述：密码，不能为空

clientID：

- 类型：字符串
- 描述：客户机的ID，v1_app_[MAC] //版本号_app_USERTOKEN(截取12位必须小写)，不能为空

topic：

- 类型：字符串
- 描述：订阅的主题

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status:    		//操作成功状态洗洗脑
    payload：{}         //服务器返回的消息
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
    error:0      //错误码
}
```

##示例代码

```js
var mico = api.require('mico');
mico.startMqtt({
    host: 'api.easylink.io',
    port: '1883',
    username: 'admin',
    password: 'admin',
    clientID: 'clientId-999abcdedf',
    topic: 'd64f517c/c8934691813c/out/read'
},function( ret, err ){		
	if( ret.status ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```
##可用性

Android系统

可提供的1.0.0及更高版本

#**stopMqtt**<div id="7"></div>

关闭MQTT订阅服务

stopMqtt(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status:Stop         //操作成功
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
    error:0      //错误码
}
```

##示例代码

```js
var mico = api.require('mico');
mico.stopMqtt(function( ret, err ){		
	if( ret.status ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```
##可用性

Android系统

可提供的1.0.0及更高版本

#**recvMqttMsg**<div id="8"></div>

开始接收服务器push的消息，startMQTT的时候会自动启用，所以startMQTT之后不需要再次执行此方法，只有在_stopRecvMqttMsg_之后，想再次接收时，才需要再次启用

recvMqttMsg(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
    无返回值
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
    error:0      //错误码
}
```

##示例代码

```js
var mico = api.require('mico');
mico.recvMqttMsg(function( ret, err ){		
	if( ret.status ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```
##可用性

Android系统

可提供的1.0.0及更高版本
#**stopRecvMqttMsg**<div id="9"></div>

停止接收服务器push的信息

stopRecvMqttMsg(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
    无返回值
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
    error:0      //错误码
}
```

##示例代码

```js
var mico = api.require('mico');
mico.stopRecvMqttMsg(function( ret, err ){		
	if( ret.status ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```
##可用性

Android系统

可提供的1.0.0及更高版本
#**publishCommand**<div id="10"></div>

发送指令控制设备

publishCommand({params}, callback(ret, err))

##params

topic：

- 类型：字符串
- 描述：发送指令的地址，不能为空

command：

- 类型：字符串
- 描述：指令，json类型的字符串，不能为空

qos：

- 类型：字符串
- 描述：消息发布服务质量，0

retained：

- 类型：字符串
- 描述：false=实时，false

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
   无返回值
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
    error:0      //错误码
}
```

##示例代码

```js
var mico = api.require('mico');
mico.publishCommand({
    topic: 'd64f517c/c8934691813c/in/write',
    command: '{"4":true}',
    qos: 0,
    retained: false
},function( ret, err ){		
	if( ret ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```
##可用性

Android系统

可提供的1.0.0及更高版本

#**addSubscribe**<div id="11"></div>

增加MQTT订阅主题

addSubscribe({params}, callback(ret, err))

##params

topic：

- 类型：字符串
- 描述：需要订阅的topic地址，不能为空

qos：

- 类型：字符串
- 描述：QOS，不能为空

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    无返回值
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
    error:0      //错误码
}
```

##示例代码

```js
var mico = api.require('mico');
mico.addSubscribe({
    topic : 'd64f517c/c8934691813c/out/err',
    qos : 0
},function( ret, err ){		
	if( ret ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```
##可用性

Android系统

可提供的1.0.0及更高版本

#**rmSubscribe**<div id="12"></div>

移除一个MQTT订阅主题

rmSubscribe({params}, callback(ret, err))

##params

topic：

- 类型：字符串
- 描述：MQTT服务器的域名，不能为空

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    无返回值
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
    error:0      //错误码
}
```

##示例代码

```js
var mico = api.require('mico');
mico.rmSubscribe({
    topic : 'd64f517c/c8934691813c/out/err'
},function( ret, err ){		
	if( ret ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```
##可用性

Android系统

可提供的1.0.0及更高版本

#**错误返回码说明**<div id="13"></div>

**90000** 手机未联网<br/>
**90001** 参数不能为空<br/>
**90002** EasyLink服务已经开启<br/>
**90003** EasyLink服务尚未打开<br/>
**90004** MQTT服务已经开启<br/>
**90005** MQTT服务尚未打开<br/>
**90006** 已经在接收MQTT消息了<br/>
**90007** 尚未开始接收MQTT消息<br/>
**90008** MQTT服务已经开启<br/>
**90009** MQTT服务尚未打开<br/>


