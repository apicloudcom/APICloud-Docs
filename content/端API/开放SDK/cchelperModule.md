/*
Title: cchelperModule
Description: cchelperModule
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">
<div class="outline">
[start](#a1)

[stop](#a2)
</div>

#**概述**

CChelper模块封装了领通科技CChelper移动应用远程桌面客服的SDK。开发者在其APP中嵌入CChelper SDK，当用户需要求助时，即可让企业的IT人员或客服对该APP进行远程操作，帮助用户解决APP的使用问题。它具有远程桌面操作， VoIP语音，以及远程启动摄像头等功能。它非常适合于企业级App的IT技术支持，智能硬件的App、游戏、电商等App的售后客服。

此模块使用前需要先去领通科技的CChelper SDK开放平台注册管理员账户（http://www.cutecomm.com/Home/Index/download.html ），并且需要在管理系统中录入相关的应用信息，获取到唯一的appKey。另外，还需要使用PC主控端服务软件，可以去领通科技官网的下载中心下载。利用你的管理员账号，可在领通科技后台管理系统中添加客服人员账户，通过客服账户登录PC主控端实现对用户的服务。


#**start**<div id="a1"></div>

启动CChelper远程协助服务

start({params},callback(ret,err))

##params

userId:

- 类型：字符串
- 默认值：无
- 描述：应用的注册用户ID，如果没有可用为空

appKey:

- 类型：字符串
- 默认值：无
- 描述：领通科技CChelper SDK平台为应用生产的appKey，不可以为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

    {
    	status:				//操作状态
    	result:1				// 登陆结果只用status为4时，才不为空
    	resultMsg:””			// 登陆结果描述只有status为4时，才不为空
    }
    
- 描述：status为操作状态，有如下类型的值：
	
	- 0 表示因为appKey为空，启动失败，同时err对象有错误数据
	- 1 表示调用start方法成功，err对象没有返回数据
	- 2 表示为监听登陆与连接服务器的状态，err对象携带状态数据
	- 3 表示为监听登陆与连接代理服务器的状态，err对象携带状态数据
	- 4 表示为登陆结果，err对象不携带任何数据
	- 5 表示启动连接，err对象不携带任何数据
	- 6 表示主动停止服务器，err对象不携带任何数据
	- 7 表示正在等待空闲的服务人员，err对象不携带任何数据

err：

- 类型：JSON对象

内部字段：

    {
    	errorCode:		// 错误代码
    	errorMsg:””		// 错误描述
    }

##示例代码

```js
var cchelper = api.require('cchelperModule');

cchelper.start({
    userId:"",
    appKey: "apicloud#apploader"
}, function(ret, err){
    alert(JSON.stringify(ret) + JSON.stringify(err));
});
```


##补充说明

无。

##可用性

Android系统

可提供的1.0.0及更高版本


#**stop**<div id="a2"></div>

停止CChelper远程协助服务

stop()


##示例代码

```js
var cchelper = api.require("cchelperModule");

cchelper.stop();
```


##补充说明

无。

##可用性

Android系统

可提供的1.0.0及更高版本
