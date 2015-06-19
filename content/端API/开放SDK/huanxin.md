/*
Title: huanxin
Description: huanxin
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>
<div id="method-content">

<div class="outline"> 
[init](#1)
[register](#2)
[login](#3)
[logout](#4)
[setAppInited](#5)
[registerReceiver](#6)
[registerNewMessageBroadcastReceiver](#7)
[registerAckMessageBroadcastReceiver](#8)
[registerDeliveryAckMessageBroadcastReceiver](#9)
[sendTextMessage](#10)
[sendImageMessage](#11)
[sendVoiceMessage](#12)
[sendFileMessage](#13)
[sendLocationMessage](#14)
[sendVideoMessage](#15)
[getUnreadMsgCount](#16)
[resetUnreadMsgCount](#17)
[resetAllUnreadMsgCount](#18)
[getMsgCount](#19)
[clearConversation](#20)
[deleteConversation](#21)
[removeMessage](#22)
[deleteAllConversation](#23)
[getContactUserNames](#24)
[addContact](#25)
[deleteContact](#26)
[acceptInvitation](#27)
[refuseInvitation](#28)
[getBlackListUsernames](#29)
[addUserToBlackList](#30)
[deleteUserFromBlackList](#31)
[createPublicGroup](#32)
[createPrivateGroup](#33)
[addUsersToGroup](#34)
[removeUserFromGroup](#35)
[joinGroup](#36) 
[exitFromGroup](#37)
[exitAndDeleteGroup](#38)
[blockGroupMessage](#39) 
[blockUser](#40)
[getBlockedUsers](#41)
[changeGroupName](#42)
[getAllGroups](#43)
[getGroup](#44)
[addGroupChangeListener](#45)
[addEMConnectionListener](#46)
[getMessage](#47)
[getMessages](#48)
[loadMoreMsg](#49)
[registerListener](#50)
[unregisterReceiver](#51)
[unregisterListener](#52)
[acceptInvitationGroup](#53)
[declineApplicationGroup](#54)
[acceptApplicationGroup](#55)
[setNotifyBySoundAndVibrate](#56)
[setNoticeBySound](#57)
[setNoticedByVibrate](#58)
[setUseSpeaker](#58)
[setShowNotificationInBackgroud](#59)
[setAcceptInvitationAlways](#60)
[updateCurrentUserNick](#61)
</div>

# 概述 #
环信将基于移动互联网的即时通讯能力，如单聊、群聊、发语音、发图片、发位置、实时音频、实时视频等，通过云端开放的 Rest API 和客户端 SDK包的方式提供给开sendImageMessage发者和企业。让App内置聊天功能和以前网页中嵌入分享功能一样简单。

环信全面支持Android、iOS、Web等多种平台，在流量、电量、长连接、语音、位置、安全等能力做了极致的优化，让移动开发者摆脱繁重的移动IM通讯底层开发，极大限度地缩短产品开发周期，极短的时间内让App拥有移动IM能力。

使用huanxin模块之前，请先注册[注册](https://console.easemob.com/)环信的开发者帐号并申请创建 App，创建 App 后，可以在开发者后台获取 AppKey 和 client_secret 用于开发。

开发前请先认真阅读相关的环信开发文档和视频。

		var uzmoduledemo = null;
		apiready = function(){
		
	    	uzmoduledemo = api.require('huanxin');
	    }


#**init**<div id="1"></div>
初次化操作,在使用其它功能前,请先调用该方法进行初始化

## params ##
### appkey： ###

- 类型：字符串
- 默认值：无
- 描述：环信appkey

## 示例代码 ##

	var param = {appkey:"xxxxx"};
	uzmoduledemo.init(param);

## 补充说明 ##

在使用其它功能前,请先调用该方法进行初始化

## 可用性 ##

 android系统

可提供的1.0.0及更高版本

#**register**<div id="2"></div>
注册

register ({params}, callback(ret, err))

## params ##
### username： ###

- 类型：字符串
- 默认值：无
- 描述：用户名

### pwd： ###

- 类型：字符串
- 默认值：0
- 描述：密码

## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
    	status: true, // 状态码：true / false,
		result: "成功"//文本信息
	}
### err: ###

- 类型：JSON 对象
- 描述：返回参数

###  内部字段： ###

	{
    	status: true, // 状态码：true / false,
		result: "失败"//文本信息
	}

## 示例代码 ##
	
	var param = {username:"so123456",pwd:"123456"};
	var resultCallback = function(ret, err){
		if(ret){
			alert(JSON.stringify(ret));
		}else{
			alert(JSON.stringify(err));
		}
	}
	uzmoduledemo.register(param, resultCallback);

## 补充说明 ##
注册


## 可用性 ##

 android系统

可提供的1.0.0及更高版本

#**login**<div id="3"></div>
登录

login ({params}, callback(ret, err))

## params ##
### username： ###

- 类型：字符串
- 默认值：无
- 描述：用户名

### pwd： ###

- 类型：字符串
- 默认值：0
- 描述：密码

## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
    	status: true, // 状态码：true / false,
		result: "登录成功"//文本信息
	}
### err: ###

- 类型：JSON 对象
- 描述：返回参数

###  内部字段： ###

	{
    	status: true, // 状态码：true / false,
		result: "登录失败"//文本信息
	}


### 示例代码 ###
    var param = {username:"so123456",pwd:"123456"};
	var resultCallback = function(ret, err){
		if(ret){
			alert(JSON.stringify(ret));
		}else{
			alert(JSON.stringify(err));
		}
	}
	uzmoduledemo.login(param, resultCallback);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**logout**<div id="4"></div>
登出

logout (callback(ret, err))

## params ##
无

## callback(ret, err) ##
### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

#### onSuccess ####

	{
	    status: 'onSuccess'
	}

#### onError ####

	{
	    status: 'onError', // 状态码
		code : 
		message:
	}

#### onProgress ####

	{
	    status: 'onProgress', // 状态码
		progress : 
		status:
	}


### 示例代码 ###
	var resultCallback = function(ret, err){
		if(ret.status == "onSuccess"){
			alert(JSON.stringify(ret));
		}else if(ret.status == "onError"){
			alert(JSON.stringify(err));
		}
	}
	uzmoduledemo.logout(resultCallback);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本


#**setAppInited**<div id="5"></div>
通知sdk，UI 已经初始化完毕，注册了相应的receiver和listener, 可以接受广播了
在registerReceiverAndListener和界面完成后使用

setAppInited ()

## params ##
无

## callback(ret, err) ##
无


### 示例代码 ###
	
	uzmoduledemo.setAppInited();

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**registerReceiver**<div id="6"></div>
##
注册主要的广播

registerReceiver ()

## params ##
无

## callback(ret, err) ##
无


### 示例代码 ###
	
	uzmoduledemo.registerReceiver();

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**registerNewMessageBroadcastReceiver**<div id="7"></div>
添加一个接收消息的广播

registerNewMessageBroadcastReceiver ()

## params ##
无

## callback(ret, err) ##
### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: 'onReceive',
		from:
		msgId:
	}


### 示例代码 ###
	
	uzmoduledemo.registerNewMessageBroadcastReceiver(function (ret, err) {
        	if (ret.status == 'onReceive'){
			
			}
    	});

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**registerAckMessageBroadcastReceiver**<div id="8"></div>
添加一个消息回执的广播

registerAckMessageBroadcastReceiver ()

## params ##
无

## callback(ret, err) ##
### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: 'onReceive',
		from:
		msgId:
	}


### 示例代码 ###
	
	uzmoduledemo.registerAckMessageBroadcastReceiver(function (ret, err) {
        	if (ret.status == 'onReceive'){
			
			}
    	});

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**registerDeliveryAckMessageBroadcastReceiver**<div id="9"></div>
添加一个消息送达的广播

registerDeliveryAckMessageBroadcastReceiver ()

## params ##
无

## callback(ret, err) ##
### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: 'onReceive',
		from:
		msgId:
	}


### 示例代码 ###
	
	uzmoduledemo.registerDeliveryAckMessageBroadcastReceiver(function (ret, err) {
        	if (ret.status == 'onReceive'){
			
			}
    	});

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**sendTextMessage**<div id="10"></div>
发送文本信息

sendTextMessage ({params}, callback(ret, err))

## params ##
### chatType： ###

- 类型：字符串
- 默认值：无
- 描述：类型,单聊类型值为"CHAT",群聊类型值为"GROUPCHAT",默认是单聊

### toUser： ###

- 类型：字符串
- 默认值：0
- 描述：接收对象,单聊类型值为"userid",群聊类型值为"groupid"

### content： ###

- 类型：字符串
- 默认值：0
- 描述：发送内容

## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: 'success', // 状态码：success / progress
	    result:
	    {
	        msgId: 'xxx' // 当前消息ID,
			progress: 'xxx' // 进度,当状态码为progress是才有
			status: 'xxx' // 消息的状态,当状态码为progress是才有
	    }
	}
### err: ###

- 类型：JSON 对象
- 描述：返回参数

###  内部字段： ###

	{
    	status: "error", // 状态码
		result:
	    {
	        msgId: 'xxx' // 当前消息ID,
			errormsg: 'xxx' // 错误原因
	    }
	}


### 示例代码 ###
    
	uzmoduledemo.sendTextMessage({
        chatType: 'CHAT',
        toUser: 'xxxx',
        content: '我是环信'
    	}, function (ret, err) {
        	if (ret.status == 'progress'){
			
			}else if (ret.status == 'success'){
				
			}
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**sendImageMessage**<div id="11"></div>
发送图片信息

sendImageMessage ({params}, callback(ret, err))

## params ##
### chatType： ###

- 类型：字符串
- 默认值：无
- 描述：类型,单聊类型值为"CHAT",群聊类型值为"GROUPCHAT",默认是单聊

### toUser： ###

- 类型：字符串
- 默认值：0
- 描述：接收对象,单聊类型值为"userid",群聊类型值为"groupid"

### imagePath： ###

- 类型：字符串
- 默认值：0
- 描述：图片的路径

## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: 'success', // 状态码：success / progress
	    result:
	    {
	        msgId: 'xxx' // 当前消息ID,
			progress: 'xxx' // 进度,当状态码为progress是才有
			status: 'xxx' // 消息的状态,当状态码为progress是才有
	    }
	}
### err: ###

- 类型：JSON 对象
- 描述：返回参数

###  内部字段： ###

	{
    	status: "error", // 状态码
		result:
	    {
	        msgId: 'xxx' // 当前消息ID,
			errormsg: 'xxx' // 错误原因
	    }
	}


### 示例代码 ###
    
	uzmoduledemo.sendImageMessage({
        chatType: 'CHAT',
        toUser: 'xxxx',
        imagePath: 'xxxxx'
    	}, function (ret, err) {
        	if (ret.status == 'progress'){
			
			}else if (ret.status == 'success'){
				
			}
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**sendVoiceMessage**<div id="12"></div>
发送语音信息

sendVoiceMessage ({params}, callback(ret, err))

## params ##
### chatType： ###

- 类型：字符串
- 默认值：无
- 描述：类型,单聊类型值为"CHAT",群聊类型值为"GROUPCHAT",默认是单聊

### toUser： ###

- 类型：字符串
- 默认值：0
- 描述：接收对象,单聊类型值为"userid",群聊类型值为"groupid"

### voicePath： ###

- 类型：字符串
- 默认值：0
- 描述：语音文件的路径

### duration： ###

- 类型：数字
- 默认值：0
- 描述：语音消息的时长，单位为秒

## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: 'success', // 状态码：success / progress
	    result:
	    {
	        msgId: 'xxx' // 当前消息ID,
			progress: 'xxx' // 进度,当状态码为progress是才有
			status: 'xxx' // 消息的状态,当状态码为progress是才有
	    }
	}
### err: ###

- 类型：JSON 对象
- 描述：返回参数

###  内部字段： ###

	{
    	status: "error", // 状态码
		result:
	    {
	        msgId: 'xxx' // 当前消息ID,
			errormsg: 'xxx' // 错误原因
	    }
	}


### 示例代码 ###
    
	uzmoduledemo.sendVoiceMessage({
        chatType: 'CHAT',
        toUser: 'xxxx',
		duration: 5000,
        voicePath: 'xxxxx'
    	}, function (ret, err) {
        	if (ret.status == 'progress'){
			
			}else if (ret.status == 'success'){
				
			}
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**sendFileMessage**<div id="13"></div>
发送文件信息

sendFileMessage ({params}, callback(ret, err))

## params ##
### chatType： ###

- 类型：字符串
- 默认值：无
- 描述：类型,单聊类型值为"CHAT",群聊类型值为"GROUPCHAT",默认是单聊

### toUser： ###

- 类型：字符串
- 默认值：0
- 描述：接收对象,单聊类型值为"userid",群聊类型值为"groupid"

### filePath： ###

- 类型：字符串
- 默认值：0
- 描述：文件的路径

## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: 'success', // 状态码：success / progress
	    result:
	    {
	        msgId: 'xxx' // 当前消息ID,
			progress: 'xxx' // 进度,当状态码为progress是才有
			status: 'xxx' // 消息的状态,当状态码为progress是才有
	    }
	}
### err: ###

- 类型：JSON 对象
- 描述：返回参数

###  内部字段： ###

	{
    	status: "error", // 状态码
		result:
	    {
	        msgId: 'xxx' // 当前消息ID,
			errormsg: 'xxx' // 错误原因
	    }
	}


### 示例代码 ###
    
	uzmoduledemo.sendFileMessage({
        chatType: 'CHAT',
        toUser: 'xxxx',
        filePath: 'xxxxx'
    	}, function (ret, err) {
        	if (ret.status == 'progress'){
			
			}else if (ret.status == 'success'){
				
			}
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**sendLocationMessage**<div id="14"></div>
发送位置信息

sendLocationMessage ({params}, callback(ret, err))

## params ##
### chatType： ###

- 类型：字符串
- 默认值：无
- 描述：类型,单聊类型值为"CHAT",群聊类型值为"GROUPCHAT",默认是单聊

### toUser： ###

- 类型：字符串
- 默认值：0
- 描述：接收对象,单聊类型值为"userid",群聊类型值为"groupid"

### latitude: ###

- 类型：数字
- 默认值：无
- 描述：纬度

### longitude: ###

- 类型：数字
- 默认值：无
- 描述：经度

### locationAddress: ###

- 类型：字符串
- 默认值：无
- 描述：地址文字内容

## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: 'success', // 状态码：success / progress
	    result:
	    {
	        msgId: 'xxx' // 当前消息ID,
			progress: 'xxx' // 进度,当状态码为progress是才有
			status: 'xxx' // 消息的状态,当状态码为progress是才有
	    }
	}
### err: ###

- 类型：JSON 对象
- 描述：返回参数

###  内部字段： ###

	{
    	status: "error", // 状态码
		result:
	    {
	        msgId: 'xxx' // 当前消息ID,
			errormsg: 'xxx' // 错误原因
	    }
	}


### 示例代码 ###
    
	uzmoduledemo.sendLocationMessage({
        chatType: 'CHAT',
        toUser: 'xxxx',
		latitude: 'xxxx',
		longitude: 'xxxx',
        locationAddress: 'xxxxx'
    	}, function (ret, err) {
        	if (ret.status == 'progress'){
			
			}else if (ret.status == 'success'){
				
			}
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**sendVideoMessage**<div id="15"></div>
发送视频信息

sendVideoMessage ({params}, callback(ret, err))

## params ##
### chatType： ###

- 类型：字符串
- 默认值：无
- 描述：类型,单聊类型值为"CHAT",群聊类型值为"GROUPCHAT",默认是单聊

### toUser： ###

- 类型：字符串
- 默认值：0
- 描述：接收对象,单聊类型值为"userid",群聊类型值为"groupid"

### videoPath： ###

- 类型：字符串
- 默认值：0
- 描述：视频文件的路径

### duration： ###

- 类型：数字
- 默认值：0
- 描述：视频消息的时长，单位为秒

## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: 'success', // 状态码：success / progress
	    result:
	    {
	        msgId: 'xxx' // 当前消息ID,
			progress: 'xxx' // 进度,当状态码为progress是才有
			status: 'xxx' // 消息的状态,当状态码为progress是才有
	    }
	}
### err: ###

- 类型：JSON 对象
- 描述：返回参数

###  内部字段： ###

	{
    	status: "error", // 状态码
		result:
	    {
	        msgId: 'xxx' // 当前消息ID,
			errormsg: 'xxx' // 错误原因
	    }
	}


### 示例代码 ###
    
	uzmoduledemo.sendVideoMessage({
        chatType: 'CHAT',
        toUser: 'xxxx',
		duration: 5000,
        voicePath: 'xxxxx'
    	}, function (ret, err) {
        	if (ret.status == 'progress'){
			
			}else if (ret.status == 'success'){
				
			}
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**getUnreadMsgCount**<div id="16"></div>
获取未读消息数

getUnreadMsgCount ({params}, callback(ret, err))

## params ##
### conversation： ###

- 类型：字符串
- 默认值：无
- 描述：当前的会话,单聊类型值为"userid",群聊类型值为"groupid"


## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: true, // 状态码
	    result: 5 //返回的未读消息数
	}
### err: ###

- 类型：JSON 对象
- 描述：返回参数

###  内部字段： ###

	{
    	status: false // 状态码
	}


### 示例代码 ###
    
	uzmoduledemo.getUnreadMsgCount({
        conversation: 'xxxx'
    	}, function (ret, err) {
        	alert(JSON.stringify(ret));
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**resetUnreadMsgCount**<div id="17"></div>
未读消息数清零

resetUnreadMsgCount ({params}, callback(ret, err))

## params ##
### conversation： ###

- 类型：字符串
- 默认值：无
- 描述：当前的会话,单聊类型值为"userid",群聊类型值为"groupid"


## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: true, // 状态码
	}
### err: ###

- 类型：JSON 对象
- 描述：返回参数

###  内部字段： ###

	{
    	status: false // 状态码
	}


### 示例代码 ###
    
	uzmoduledemo.resetUnreadMsgCount({
        conversation: 'xxxx'
    	}, function (ret, err) {
        	alert(JSON.stringify(ret));
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**resetAllUnreadMsgCount**<div id="18"></div>
所有未读消息数清零

resetAllUnreadMsgCount (callback(ret, err))

## params ##
无


## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: true, // 状态码
	}
### err: ###

- 类型：JSON 对象
- 描述：返回参数

###  内部字段： ###

	{
    	status: false // 状态码
	}


### 示例代码 ###
    
	uzmoduledemo.resetAllUnreadMsgCount(function (ret, err) {
        	alert(JSON.stringify(ret));
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**getMsgCount**<div id="19"></div>
获取消息总数

getMsgCount ({params},callback(ret, err))

## params ##
### conversation： ###

- 类型：字符串
- 默认值：无
- 描述：当前的会话,单聊类型值为"userid",群聊类型值为"groupid"


## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: true, // 状态码
		result: 100 //返回的消息总数
	}
### err: ###

- 类型：JSON 对象
- 描述：返回参数

###  内部字段： ###

	{
    	status: false // 状态码
	}


### 示例代码 ###
    
	uzmoduledemo.getMsgCount({
        conversation: 'xxxx'
    	}, function (ret, err) {
        	alert(JSON.stringify(ret));
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**clearConversation**<div id="20"></div>
清空会话聊天记录,但不删除这个会话对象

clearConversation ({params},callback(ret, err))

## params ##
### conversation： ###

- 类型：字符串
- 默认值：无
- 描述：当前的会话,单聊类型值为"userid",群聊类型值为"groupid"


## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: true, // 状态码
	}
### err: ###

- 类型：JSON 对象
- 描述：返回参数

###  内部字段： ###

	{
    	status: false // 状态码
	}


### 示例代码 ###
    
	uzmoduledemo.clearConversation({
        conversation: 'xxxx'
    	}, function (ret, err) {
        	alert(JSON.stringify(ret));
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**deleteConversation**<div id="21"></div>
清空会话聊天记录并删除这个会话对象

deleteConversation ({params},callback(ret, err))

## params ##
### conversation： ###

- 类型：字符串
- 默认值：无
- 描述：当前的会话,单聊类型值为"userid",群聊类型值为"groupid"


## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: true, // 状态码
	}
### err: ###

- 类型：JSON 对象
- 描述：返回参数

###  内部字段： ###

	{
    	status: false // 状态码
	}


### 示例代码 ###
    
	uzmoduledemo.deleteConversation({
        conversation: 'xxxx'
    	}, function (ret, err) {
        	alert(JSON.stringify(ret));
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**removeMessage**<div id="22"></div>
删除某个会话的某条聊天记录

removeMessage ({params},callback(ret, err))

## params ##
### conversation： ###

- 类型：字符串
- 默认值：无
- 描述：当前的会话,单聊类型值为"userid",群聊类型值为"groupid"

### msgId： ###

- 类型：字符串
- 默认值：无
- 描述：某条聊天记录ID


## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: true, // 状态码
	}
### err: ###

- 类型：JSON 对象
- 描述：返回参数

###  内部字段： ###

	{
    	status: false // 状态码
	}


### 示例代码 ###
    
	uzmoduledemo.removeMessage({
        conversation: 'xxxx',
		msgId : '5555' 
    	}, function (ret, err) {
        	alert(JSON.stringify(ret));
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**deleteAllConversation**<div id="23"></div>
删除所有会话记录

deleteAllConversation (callback(ret, err))

## params ##
无


## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: true, // 状态码
	}
### err: ###

- 类型：JSON 对象
- 描述：返回参数

###  内部字段： ###

	{
    	status: false // 状态码
	}


### 示例代码 ###
    
	uzmoduledemo.deleteAllConversation(function (ret, err) {
        	alert(JSON.stringify(ret));
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**getContactUserNames**<div id="24"></div>
获取好友列表

getContactUserNames (callback(ret, err))

## params ##
无

## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: true, // 状态码
		result:      //好友的用户名列表
	}
### err: ###

- 类型：JSON 对象
- 描述：返回参数

###  内部字段： ###

	{
    	status: false, // 状态码
		result: '获取好友失败'//失败信息
	}


### 示例代码 ###
    
	uzmoduledemo.getContactUserNames(function (ret, err) {
        	alert(JSON.stringify(ret));
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**addContact**<div id="25"></div>
添加好友

addContact ({params},callback(ret, err))

## params ##
### username： ###

- 类型：字符串
- 默认值：无
- 描述：要添加的好友名


### reason： ###

- 类型：字符串
- 默认值：无
- 描述：理由

## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: true, // 状态码
	}
### err: ###

- 类型：JSON 对象
- 描述：返回参数

###  内部字段： ###

	{
    	status: false, // 状态码
		result : '添加好友失败'//失败信息
	}


### 示例代码 ###
    
	uzmoduledemo.addContact({
        username: 'xxxx',
		reason:'我是1010,请回复'
    	}, function (ret, err) {
        	alert(JSON.stringify(ret));
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**deleteContact**<div id="26"></div>
删除好友

deleteContact ({params},callback(ret, err))

## params ##
### username： ###

- 类型：字符串
- 默认值：无
- 描述：要添加的好友名

## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: true, // 状态码
	}
### err: ###

- 类型：JSON 对象
- 描述：返回参数

###  内部字段： ###

	{
    	status: false, // 状态码
		result : '删除好友失败'//失败信息
	}


### 示例代码 ###
    
	uzmoduledemo.deleteContact({
        conversation: 'xxxx'
    	}, function (ret, err) {
        	alert(JSON.stringify(ret));
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**acceptInvitation**<div id="27"></div>
同意好友请求

acceptInvitation ({params},callback(ret, err))

## params ##
### username： ###

- 类型：字符串
- 默认值：无
- 描述：要添加的好友名

## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: true, // 状态码
	}
### err: ###

- 类型：JSON 对象
- 描述：返回参数

###  内部字段： ###

	{
    	status: false, // 状态码
		result : '同意好友请求失败'//失败信息
	}


### 示例代码 ###
    
	uzmoduledemo.acceptInvitation({
        username: 'xxxx'
    	}, function (ret, err) {
        	alert(JSON.stringify(ret));
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**refuseInvitation**<div id="28"></div>
拒绝好友请求

refuseInvitation ({params},callback(ret, err))

## params ##
### username： ###

- 类型：字符串
- 默认值：无
- 描述：要添加的好友名

## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: true, // 状态码
	}
### err: ###

- 类型：JSON 对象
- 描述：返回参数

###  内部字段： ###

	{
    	status: false, // 状态码
		result : '拒绝好友请求失败'//失败信息
	}


### 示例代码 ###
    
	uzmoduledemo.refuseInvitation({
        username: 'xxxx'
    	}, function (ret, err) {
        	alert(JSON.stringify(ret));
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**getBlackListUsernames**<div id="29"></div>
获取黑名单列表

getBlackListUsernames (callback(ret, err))

## params ##
无

## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: true, // 状态码
		result://黑名单用户名列表
	}
### err: ###

- 类型：JSON 对象
- 描述：返回参数

###  内部字段： ###

	{
    	status: false, // 状态码
		result : '获取黑名单列表失败'//失败信息
	}


### 示例代码 ###
    
	uzmoduledemo.getBlackListUsernames(function (ret, err) {
        	alert(JSON.stringify(ret));
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**addUserToBlackList**<div id="30"></div>
把用户加入到黑名单

addUserToBlackList ({params},callback(ret, err))

## params ##
### username： ###

- 类型：字符串
- 默认值：无
- 描述：要添加的好友名

### both： ###

- 类型：boolean
- 默认值：false
- 描述：为true，则把用户加入到黑名单后双方发消息时对方都收不到；为false,我能给黑名单的中用户发消息，但是对方发给我时我是收不到的

## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: true, // 状态码
	}
### err: ###

- 类型：JSON 对象
- 描述：返回参数

###  内部字段： ###

	{
    	status: false, // 状态码
		result : '加入到黑名单列表失败'//失败信息
	}


### 示例代码 ###
    
	uzmoduledemo.addUserToBlackList({
        username: 'xxxx',
		both:true,
    	}, function (ret, err) {
        	alert(JSON.stringify(ret));
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**deleteUserFromBlackList**<div id="31"></div>
把用户从黑名单中移除

deleteUserFromBlackList ({params},callback(ret, err))

## params ##
### username： ###

- 类型：字符串
- 默认值：无
- 描述：要添加的好友名

## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: true, // 状态码
	}
### err: ###

- 类型：JSON 对象
- 描述：返回参数

###  内部字段： ###

	{
    	status: false, // 状态码
		result : '从黑名单中移除失败'//失败信息
	}


### 示例代码 ###
    
	uzmoduledemo.deleteUserFromBlackList({
        username: 'xxxx',
    	}, function (ret, err) {
        	alert(JSON.stringify(ret));
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**createPublicGroup**<div id="32"></div>
创建一个公开群

createPublicGroup ({params},callback(ret, err))

## params ##
### groupName： ###

- 类型：字符串
- 默认值：无
- 描述：创建的群聊的名称

### desc： ###

- 类型：字符串
- 默认值：空
- 描述： 群聊简介

### members： ###

- 类型：字符串
- 默认值：空
- 描述：群聊成员,为空时这个创建的群组只包含自己,用","分开

### needApprovalRequired： ###

- 类型：字符串
- 默认值：false
- 描述：如果创建的公开群需要户自由加入，就传false。否则需要申请，等群主批准后才能加入，传true


### maxUsers： ###

- 类型：数字
- 默认值：200
- 描述：最大人数

## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{	   
		result : {
           status: true, // 状态码
		   groupId : //返回的群主ID
		}
	}
### err: ###

- 类型：JSON 对象
- 描述：返回参数

###  内部字段： ###
 {	    
		result : {
			groupId : //返回的群主ID
            status: true // 状态码
		}
	}


### 示例代码 ###
    
	uzmoduledemo.createPublicGroup({
        groupName: 'xxxx',
		desc: 'xxxx',
		needApprovalRequired: true,
		maxUsers: 500
    	}, function (ret, err) {
        	alert(JSON.stringify(ret));
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**createPrivateGroup**<div id="33"></div>
创建一个私有群

createPrivateGroup ({params},callback(ret, err))

## params ##
### groupName： ###

- 类型：字符串
- 默认值：无
- 描述：创建的群聊的名称

### desc： ###

- 类型：字符串
- 默认值：空
- 描述： 群聊简介

### members： ###

- 类型：字符串
- 默认值：空
- 描述：群聊成员,为空时这个创建的群组只包含自己,用","分开

### allowInvite： ###

- 类型：字符串
- 默认值：false
- 描述：是否允许群成员邀请人进群


### maxUsers： ###

- 类型：数字
- 默认值：200,是大2000
- 描述：最大人数

## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    
		result : {
			groupId : //返回的群主ID
            status: true // 状态码
		}
	}
### err: ###

- 类型：JSON 对象
- 描述：返回参数

###  内部字段： ###

	{
    	status: false, // 状态码
		result : '创建群组失败'//失败信息
	}


### 示例代码 ###
    
	uzmoduledemo.createPrivateGroup({
        groupName: 'xxxx',
		desc: 'xxxx',
		allowInvite: true,
		maxUsers: 500
    	}, function (ret, err) {
        	alert(JSON.stringify(ret));
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**addUsersToGroup**<div id="34"></div>
添加群成员

addUsersToGroup ({params},callback(ret, err))

## params ##
### groupId： ###

- 类型：字符串
- 默认值：无
- 描述：群组ID

### members： ###

- 类型：字符串
- 默认值：空
- 描述：群聊成员,为空时这个创建的群组只包含自己,用","分开


## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: true, // 状态码
	}
### err: ###

- 类型：JSON 对象
- 描述：返回参数

###  内部字段： ###

	{
    	status: false, // 状态码
		result : '添加群成员失败'//失败信息
	}


### 示例代码 ###
    
	uzmoduledemo.addUsersToGroup({
		groupId : '',
        members: 'xxxx,xxxx,xxx,xxxx'
    	}, function (ret, err) {
        	alert(JSON.stringify(ret));
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**removeUserFromGroup**<div id="35"></div>
删除群成员

removeUserFromGroup ({params},callback(ret, err))

## params ##
### groupId： ###

- 类型：字符串
- 默认值：无
- 描述：群组ID

### username： ###

- 类型：字符串
- 默认值：空
- 描述：成员


## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: true, // 状态码
	}
### err: ###

- 类型：JSON 对象
- 描述：返回参数

###  内部字段： ###

	{
    	status: false, // 状态码
		result : '删除失败'//失败信息
	}


### 示例代码 ###
    
	uzmoduledemo.removeUserFromGroup({
		groupId: 'xxxx',
        username: 'xxxx'
    	}, function (ret, err) {
        	alert(JSON.stringify(ret));
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**joinGroup**<div id="36"></div>
成员加群请求

joinGroup ({params},callback(ret, err))

## params ##
### groupId： ###

- 类型：字符串
- 默认值：无
- 描述：群组ID

### reason： ###

- 类型：字符串
- 默认值：空
- 描述：理由


## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: true, // 状态码
	}
### err: ###

- 类型：JSON 对象
- 描述：返回参数

###  内部字段： ###

	{
    	status: false, // 状态码
		result : '请求加入群聊失败'//失败信息
	}


### 示例代码 ###
    
	uzmoduledemo.joinGroup({
		groupId: 'xxxx',
        reason: 'xxxx'//理由
    	}, function (ret, err) {
        	alert(JSON.stringify(ret));
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**exitFromGroup**<div id="37"></div>
退群请求

exitFromGroup ({params},callback(ret, err))

## params ##
### groupId： ###

- 类型：字符串
- 默认值：无
- 描述：群组ID


## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: true, // 状态码
	}
### err: ###

- 类型：JSON 对象
- 描述：返回参数

###  内部字段： ###

	{
    	status: false, // 状态码
		result : '退出群聊失败'//失败信息
	}


### 示例代码 ###
    
	uzmoduledemo.exitFromGroup({
		groupId: 'xxxx'
    	}, function (ret, err) {
        	alert(JSON.stringify(ret));
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**exitAndDeleteGroup**<div id="38"></div>
解散群聊

exitAndDeleteGroup ({params},callback(ret, err))

## params ##
### groupId： ###

- 类型：字符串
- 默认值：无
- 描述：群组ID


## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: true, // 状态码
	}
### err: ###

- 类型：JSON 对象
- 描述：返回参数

###  内部字段： ###

	{
    	status: false, // 状态码
		result : '解散群聊失败'//失败信息
	}


### 示例代码 ###
    
	uzmoduledemo.exitAndDeleteGroup({
		groupId: 'xxxx'
    	}, function (ret, err) {
        	alert(JSON.stringify(ret));
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**blockGroupMessage**<div id="39"></div>
是否屏蔽群消息

blockGroupMessage ({params},callback(ret, err))

## params ##
### groupId： ###

- 类型：字符串
- 默认值：无
- 描述：群组ID

### block： ###

- 类型：boolean
- 默认值：false
- 描述：true,设置屏蔽,false不屏蔽


## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: true, // 状态码
	}
### err: ###

- 类型：JSON 对象
- 描述：返回参数

###  内部字段： ###

	{
    	status: false, // 状态码
		result : '失败'//失败信息
	}


### 示例代码 ###
    
	uzmoduledemo.blockGroupMessage({
		groupId: 'xxxx',
		block : true
    	}, function (ret, err) {
        	alert(JSON.stringify(ret));
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**blockUser**<div id="40"></div>
是否将群成员拉入群组的黑名单（只有群主才能调用此函数）

blockUser ({params},callback(ret, err))

## params ##
### groupId： ###

- 类型：字符串
- 默认值：无
- 描述：群组ID

### username： ###

- 类型：字符串
- 默认值：无
- 描述：成员

### block： ###

- 类型：boolean
- 默认值：false
- 描述：true,设置屏蔽,false不屏蔽


## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: true, // 状态码
	}
### err: ###

- 类型：JSON 对象
- 描述：返回参数

###  内部字段： ###

	{
    	status: false, // 状态码
		result : '失败'//失败信息
	}


### 示例代码 ###
    
	uzmoduledemo.blockUser({
		groupId: 'xxxx',
		username:'xxxx',
		block : true
    	}, function (ret, err) {
        	alert(JSON.stringify(ret));
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**getBlockedUsers**<div id="41"></div>
获取群组的黑名单用户列表

getBlockedUsers ({params},callback(ret, err))

## params ##
### groupId： ###

- 类型：字符串
- 默认值：无
- 描述：群组ID


## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: true, // 状态码
		result://成员名列表
	}
### err: ###

- 类型：JSON 对象
- 描述：返回参数

###  内部字段： ###

	{
    	status: false, // 状态码
		result : '失败'//失败信息
	}


### 示例代码 ###
    
	uzmoduledemo.getBlockedUsers({
		groupId: 'xxxx'
    	}, function (ret, err) {
        	alert(JSON.stringify(ret));
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**changeGroupName**<div id="42"></div>
修改群组名称

changeGroupName ({params},callback(ret, err))

## params ##
### groupId： ###

- 类型：字符串
- 默认值：无
- 描述：群组ID

### changedGroupName： ###

- 类型：字符串
- 默认值：无
- 描述：新群组名称


## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: true, // 状态码
	}
### err: ###

- 类型：JSON 对象
- 描述：返回参数

###  内部字段： ###

	{
    	status: false, // 状态码
		result : '失败'//失败信息
	}


### 示例代码 ###
    
	uzmoduledemo.changeGroupName({
		groupId: 'xxxx',
		changedGroupName : 'ffff'
    	}, function (ret, err) {
        	alert(JSON.stringify(ret));
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**getAllGroups**<div id="43"></div>
获取群聊列表

getAllGroups (callback(ret, err))

## params ##
无


## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: true, // 状态码
		result : [{
			groupId : 
			groupName:
			count:
			maxUser:
			description:
			lastModifiedTime:
			isPublic:
			isAllowInvites:
			isMembersOnly:
			owner:
		}]
	}
### err: ###

- 类型：JSON 对象
- 描述：返回参数

###  内部字段： ###

	{
    	status: false, // 状态码
		result : '失败'//失败信息
	}


### 示例代码 ###
    
	uzmoduledemo.getAllGroups(function (ret, err) {
        	alert(JSON.stringify(ret));
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**getGroup**<div id="44"></div>
获取单个群聊信息

getGroup ({params},callback(ret, err))

## params ##
### groupId： ###

- 类型：字符串
- 默认值：无
- 描述：群组ID

## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: true, // 状态码
		result : [{
			groupId : 
			groupName:
			count:
			maxUser:
			description:
			lastModifiedTime:
			isPublic:
			isAllowInvites:
			isMembersOnly:
			owner:
			members:
		}]
	}
### err: ###

- 类型：JSON 对象
- 描述：返回参数

###  内部字段： ###

	{
    	status: false, // 状态码
		result : '失败'//失败信息
	}


### 示例代码 ###
    
	uzmoduledemo.getGroup({
		groupId: 'xxxx'
    	}, function (ret, err) {
        	alert(JSON.stringify(ret));
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**addGroupChangeListener**<div id="45"></div>
群聊事件监听

addGroupChangeListener (callback(ret, err))

## params ##
### groupId： ###

- 类型：字符串
- 默认值：无
- 描述：群组ID

## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

#### 当前用户被管理员移除出群聊 ####

	{
	    status: 'onUserRemoved', // 状态码
		groupId : 
		groupName:
	}

#### 收到加入群聊的邀请 ####

	{
	    status: 'onInvitationReceived', // 状态码
		groupId : 
		inviter:
		reason:
	}

#### 群聊邀请被拒绝 ####

	{
	    status: 'onInvitationDeclined', // 状态码
		groupId : 
		invitee:
		reason:
	}

#### 群聊邀请被接受 ####

	{
	    status: 'onInvitationAccpted', // 状态码
		groupId : 
		inviter:
		reason:
	}

#### 群聊被创建者解散 ####

	{
	    status: 'onGroupDestroy', // 状态码
		groupId : 
		groupName:
	}

#### 收到加群申请 ####

	{
	    status: 'onApplicationReceived', // 状态码
		groupId : 
		groupName:
		applyer:
		reason:
	}

#### 加群申请被同意 ####

	{
	    status: 'onApplicationAccept', // 状态码
		groupId : 
		groupName:
		accepter:
	}

#### 加群申请被拒绝 ####

	{
	    status: 'onApplicationDeclined', // 状态码
		groupId : 
		groupName:
		decliner:
		reason:
	}
### err: ###

- 类型：JSON 对象
- 描述：返回参数

###  内部字段： ###

	{
    	status: false, // 状态码
	}


### 示例代码 ###
    
	uzmoduledemo.addGroupChangeListener({
		groupId: 'xxxx'
    	}, function (ret, err) {
        	alert(JSON.stringify(ret));
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**addEMConnectionListener**<div id="46"></div>
注册一个连接状态的监听

addEMConnectionListener (callback(ret, err))

## params ##
无

## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

#### onConnected ####

	{
	    status: 'onConnected', // 状态码
	}

#### onDisconnected ####

	{
	    status: 'onInvitationReceived', // 状态码
		error : //错误码参考http://www.easemob.com/apidoc/android/chat/com/easemob/EMError.html
	}

### 示例代码 ###
    
	uzmoduledemo.addEMConnectionListener(
		function (ret) {
        	alert(JSON.stringify(ret));
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本


#**getMessage**<div id="47"></div>
获取某一条信息

getMessage (params,callback(ret, err))

## params ##
### msgId： ###

- 类型：字符串
- 默认值：无
- 描述：消息ID

## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: true, // 状态码
		result://消息字段具体信息参考http://www.easemob.com/apidoc/android/chat/com/easemob/chat/EMMessage.html
	}

### err: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: false, // 状态码
		result:
	}

### 示例代码 ###
    
	uzmoduledemo.getMessage(
		{msgId:"xxxx"},
		function (ret) {
        	alert(JSON.stringify(ret));
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**getMessages**<div id="48"></div>
获得指定会话的所有信息

getMessages (params,callback(ret, err))

## params ##
### conversation： ###

- 类型：字符串
- 默认值：无
- 描述：当前的会话,单聊类型值为"userid",群聊类型值为"groupid"

## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: true, // 状态码
		result://所有消息的数组,消息字段具体信息参考http://www.easemob.com/apidoc/android/chat/com/easemob/chat/EMMessage.html
	}

### err: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: false, // 状态码
		result:
	}

### 示例代码 ###
    
	uzmoduledemo.getMessages(
		{conversation:"xxxx"},
		function (ret) {
        	alert(JSON.stringify(ret));
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**loadMoreMsg**<div id="49"></div>
获取startMsgId之前的pagesize条消息

loadMoreMsg (params,callback(ret, err))

## params ##
### conversation： ###

- 类型：字符串
- 默认值：无
- 描述：当前的会话,单聊类型值为"userid",群聊类型值为"groupid"

### pagesize： ###

- 类型：int
- 默认值：20
- 描述：取出的条数

### startMsgId： ###

- 类型：字符串
- 默认值：无
- 描述：从哪条记录起


## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: true, // 状态码
		result://所有消息的数组,消息字段具体信息参考http://www.easemob.com/apidoc/android/chat/com/easemob/chat/EMMessage.html
	}

### err: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: false, // 状态码
		result:
	}

### 示例代码 ###
    
	uzmoduledemo.loadMoreMsg(
		{
			conversation:"xxxx",
			startMsgId:"xxxx",
			pagesize:20,
		},
		function (ret) {
        	alert(JSON.stringify(ret));
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**registerListener**<div id="50"></div>
注册主要的监听

registerListener ()

## params ##
无

## callback(ret, err) ##
无


### 示例代码 ###
	
	uzmoduledemo.registerListener();

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本


# unregisterReceiver() #
##
注销主要的广播

unregisterReceiver ()

## params ##
无

## callback(ret, err) ##
无


### 示例代码 ###
	
	uzmoduledemo.unregisterReceiver();

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**unregisterListener**<div id="51"></div>
注销主要的监听

unregisterListener ()

## params ##
无

## callback(ret, err) ##
无


### 示例代码 ###
	
	uzmoduledemo.unregisterListener();

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本


#**acceptInvitationGroup**<div id="52"></div>
 接受加入群组邀请

acceptInvitationGroup ({params},callback(ret, err))

## params ##
### groupId： ###

- 类型：字符串
- 默认值：无
- 描述：群组ID

## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: true, // 状态码
	}
### err: ###

- 类型：JSON 对象
- 描述：返回参数

###  内部字段： ###

	{
    	status: false, // 状态码
		result : '同意好友请求失败'//失败信息
	}


### 示例代码 ###
    
	uzmoduledemo.acceptInvitationGroup({
        groupId: 'xxxx'
    	}, function (ret, err) {
        	alert(JSON.stringify(ret));
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**declineApplicationGroup**<div id="53"></div>
拒绝加群申请

declineApplicationGroup ({params},callback(ret, err))

## params ##
### groupId： ###

- 类型：字符串
- 默认值：无
- 描述：群组ID

### username： ###

- 类型：字符串
- 默认值：无
- 描述：被拒绝的用户

### reason： ###

- 类型：字符串
- 默认值：无
- 描述：拒绝理由


## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: true, // 状态码
	}
### err: ###

- 类型：JSON 对象
- 描述：返回参数

###  内部字段： ###

	{
    	status: false, // 状态码
		result : '同意好友请求失败'//失败信息
	}


### 示例代码 ###
    
	uzmoduledemo.declineApplicationGroup({
        groupId: ret.groupId,
        username: ret.applyer,
        reason: "拒绝!"
    	}, function (ret, err) {
        	alert(JSON.stringify(ret));
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**acceptApplicationGroup**<div id="54"></div>
同意加群申请

acceptApplicationGroup ({params},callback(ret, err))

## params ##
### groupId： ###

- 类型：字符串
- 默认值：无
- 描述：群组ID

### username： ###

- 类型：字符串
- 默认值：无
- 描述：被同意的用户

## callback(ret, err) ##

### ret: ###

- 类型：JSON 对象
- 描述：返回参数

### 内部字段： ###

	{
	    status: true, // 状态码
	}
### err: ###

- 类型：JSON 对象
- 描述：返回参数

###  内部字段： ###

	{
    	status: false, // 状态码
		result : '同意好友请求失败'//失败信息
	}


### 示例代码 ###
    
	uzmoduledemo.acceptApplicationGroup({
        groupId: ret.groupId,
        username: ret.applyer
    	}, function (ret, err) {
        	alert(JSON.stringify(ret));
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**setNotifyBySoundAndVibrate**<div id="55"></div>
设置是否启用新消息提醒(打开或者关闭消息声音和震动提示)

setNotifyBySoundAndVibrate ({params})

## params ##
### flag： ###

- 类型：boolean
- 默认值：无
- 描述：true|false,默认为true


## callback(ret, err) ##

无

### 示例代码 ###
    
	uzmoduledemo.setNotifyBySoundAndVibrate({
		flag : true
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**setNoticeBySound**<div id="56"></div>
设置是否启用新消息声音提醒

setNoticeBySound ({params})

## params ##
### flag： ###

- 类型：boolean
- 默认值：无
- 描述：true|false,默认为true


## callback(ret, err) ##

无

### 示例代码 ###
    
	uzmoduledemo.setNoticeBySound({
		flag : true
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**setNoticedByVibrate**<div id="57"></div>
设置是否启用新消息震动提醒

setNoticedByVibrate ({params})

## params ##
### flag： ###

- 类型：boolean
- 默认值：无
- 描述：true|false,默认为true


## callback(ret, err) ##

无

### 示例代码 ###
    
	uzmoduledemo.setNoticedByVibrate({
		flag : true
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**setUseSpeaker**<div id="58"></div>
设置语音消息播放是否设置为扬声器播放

setUseSpeaker ({params})

## params ##
### flag： ###

- 类型：boolean
- 默认值：无
- 描述：true|false,默认为true


## callback(ret, err) ##

无

### 示例代码 ###
    
	uzmoduledemo.setUseSpeaker({
		flag : true
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本


#**setShowNotificationInBackgroud**<div id="59"></div>
设置语音消息播放是否设置为扬声器播放

setShowNotificationInBackgroud ({params})

## params ##
### flag： ###

- 类型：boolean
- 默认值：无
- 描述：true|false,默认为true


## callback(ret, err) ##

无

### 示例代码 ###
    
	uzmoduledemo.setShowNotificationInBackgroud({
		flag : true
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本

#**setAcceptInvitationAlways**<div id="60"></div>
默认添加好友时为true，是不需要验证的，改成需要验证为false

setAcceptInvitationAlways ({params})

## params ##
### flag： ###

- 类型：boolean
- 默认值：无
- 描述：true|false,默认为true


## callback(ret, err) ##

无

### 示例代码 ###
    
	uzmoduledemo.setAcceptInvitationAlways({
		flag : true
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本


#**updateCurrentUserNick**<div id="61"></div>
更新当前用户的nickname 此方法的作用是在ios离线推送时能够显示用户nick

updateCurrentUserNick ({params})

## params ##
### nickname： ###

- 类型：String
- 默认值：无
- 描述：nickname


## callback(ret, err) ##

无

### 示例代码 ###
    
	uzmoduledemo.updateCurrentUserNick({
		nickname : ''
    	}
	);

### 补充说明 ###
无

### 可用性 ###

 android系统

可提供的1.0.0及更高版本
