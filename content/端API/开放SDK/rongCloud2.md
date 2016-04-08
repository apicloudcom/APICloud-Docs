/*
Title: rongCloud2
Description: rongCloud2
*/
<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>

<div id="method-content">

<div class="outline">

<!-- 初始化和连接 -->

[init](#init)

[connect](#connect)

~~[reconnect](#reconnect)~~

[disconnect](#disconnect)

**[logout](#logout)**

*[setConnectionStatusListener](#setConnectionStatusListener)*

**[getConnectionStatus](#getConnectionStatus)**

**[getCurrentUserId](#getCurrentUserId)**

<!-- 消息的接收和发送 -->

[sendTextMessage](#sendTextMessage)

[sendImageMessage](#sendImageMessage)

[sendVoiceMessage](#sendVoiceMessage)

[sendLocationMessage](#sendLocationMessage)

[sendRichContentMessage](#sendRichContentMessage)

[sendCommandNotificationMessage](#sendCommandNotificationMessage)

**[sendCommandMessage](#sendCommandMessage)**

[setOnReceiveMessageListener](#setOnReceiveMessageListener)

<!-- 会话 -->

*[getConversationList](#getConversationList)*

*[getConversation](#getConversation)*

[removeConversation](#removeConversation)

[clearConversations](#clearConversations)

[setConversationToTop](#setConversationToTop)

<!-- 会话通知状态 -->

[getConversationNotificationStatus](#getConversationNotificationStatus)

[setConversationNotificationStatus](#setConversationNotificationStatus)

**[disableLocalNotification](#disableLocalNotification)**

<!-- 消息的读取和删除 -->

[getLatestMessages](#getLatestMessages)

[getHistoryMessages](#getHistoryMessages)

[getHistoryMessagesByObjectName](#getHistoryMessagesByObjectName)

**[getRemoteHistoryMessages](#getRemoteHistoryMessages)**

[deleteMessages](#deleteMessages)

[clearMessages](#clearMessages)

<!-- 未读消息数 -->

[getTotalUnreadCount](#getTotalUnreadCount)

[getUnreadCount](#getUnreadCount)

[getUnreadCountByConversationTypes](#getUnreadCountByConversationTypes)

<!-- 消息的状态 -->

*[setMessageReceivedStatus](#setMessageReceivedStatus)*

[clearMessagesUnreadStatus](#clearMessagesUnreadStatus)

[setMessageExtra](#setMessageExtra)

**[setMessageSentStatus](#setMessageSentStatus)**

<!-- 文字消息草稿 -->

[getTextMessageDraft](#getTextMessageDraft)

[saveTextMessageDraft](#saveTextMessageDraft)

[clearTextMessageDraft](#clearTextMessageDraft)

<!-- 讨论组 -->

[createDiscussion](#createDiscussion)

[getDiscussion](#getDiscussion)

[setDiscussionName](#setDiscussionName)

[addMemberToDiscussion](#addMemberToDiscussion)

[removeMemberFromDiscussion](#removeMemberFromDiscussion)

[quitDiscussion](#quitDiscussion)

[setDiscussionInviteStatus](#setDiscussionInviteStatus)

<!-- 群组 -->

[syncGroup](#syncGroup)

[joinGroup](#joinGroup)

[quitGroup](#quitGroup)

<!-- 聊天室 -->

[joinChatRoom](#joinChatRoom)

[quitChatRoom](#quitChatRoom)

<!-- 黑名单 -->

**[addToBlacklist](#addToBlacklist)**

**[removeFromBlacklist](#removeFromBlacklist)**

**[getBlacklistStatus](#getBlacklistStatus)**

**[getBlacklist](#getBlacklist)**

<!-- 消息通知免打扰 -->

**[setNotificationQuietHours](#setNotificationQuietHours)**

**[removeNotificationQuietHours](#removeNotificationQuietHours)**

**[getNotificationQuietHours](#getNotificationQuietHours)**

</div>

## 概述

（rongCloud2是rongCloud的优化版）

融云 Rong Cloud 是国内首家专业的即时通讯云服务提供商，专注为互联网、移动互联网开发者提供即时通讯基础能力和云端服务。通过融云平台，开发者不必搭建服务端硬件环境，就可以将即时通讯、实时网络能力快速集成至应用中。

rongCloud2 封装了融云即时通讯能力库 IMLib SDK 的 API，对融云的相关接口做了一一对应的封装，功能详情可参考目录。

使用 rongCloud2 模块之前，请先 [注册](https://developer.rongcloud.cn/signup) 融云的开发者帐号并申请创建 App，创建 App 后，可以在 [开发者后台](https://developer.rongcloud.cn) 获取 App Key 和 App Secret 用于开发。

开发前请先认真阅读相关的 [融云开发文档和视频](http://docs.rongcloud.cn)。



## APICloud融云模块V2.0.0版更新说明

弃用的方法：

- reconnect

修改的方法：

- sendImageMessage的prepare返回值content中localPath统一为imageUrl，其值不变
- sendRichContentMessage返回值content中加入url字段
- getConversationList和getConversation 安卓返回值去掉字段notificationStatus,该字段取值可通过 getConversationNotificationStatus 获取
- setConnectionStatusListener返回状态值统一成枚举字符串；去掉了status字段
- setOnReceiveMessageListener 去掉了status字段
- setMessageReceivedStatus  状态值统一成枚举字符串
- getConversation/getConversationList  修改recievedStatus，统一为枚举字符串
- 所有的错误err将只返回code，不再有msg，错误码信息参照 [融云常见错误码](http://www.rongcloud.cn/docs/android.html#%E5%B8%B8%E8%A7%81%E9%94%99%E8%AF%AF%E7%A0%81)

新增的方法：

- getConnectionStatus  // 获取当前连接状态
- logout  // 注销登录
- getRemoteHistoryMessages  // 获取远端历史消息
- setMessageSentStatus  // 设置消息发送状态
- getCurrentUserId  // 获取当前用户 Id
- addToBlacklist  // 加入黑名单
- removeFromBlacklist  // 移出黑名单
- getBlacklistStatus // 获取用户黑名单状态
- getBlacklist // 获取用户黑名单
- setNotificationQuietHours // 设置关闭 Push 时间，在该段时间内您可以收到 Push 消息，但不会收到提示。
- removeNotificationQuietHours // 删除 Push 设置
- getNotificationQuietHours // 查询 Push 设置
- sendCommandMessage  // 不保存、不计数的消息（ObjectName 为 RC:CmdMsg），您需要这种类型的消息时可以直接使用，不需要再自定义。
- disableLocalNotification // 设置本地消息不在通知栏提示

## init <div id="init"></div>

初始化融云 SDK，调用 connect 连接前务必保证调用此方法

调用前请在 config.xml 中设置内容如下：

``` xml
<feature name="rongCloud2">
    <param name="appKey" value="此处填写 App Key 值" />
</feature>
```

其中 value 的值请替换为您在融云开发者平台上申请的 App Key 值

init(callback(ret, err))

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：初始化的状态，如果 config.xml 中没有设置 appKey 值，会导致失败，错误信息为参数错误

内部字段：

``` js
{
	status: 'success', // 状态码：success / error
}
```

err:

- 类型：JSON 对象

内部字段：

``` js
{
	code: -10002	// 错误码
}
```

错误说明：

| 错误码    | 说明     |
| :----- | :----- |
| -10002 | 输入参数错误 |

### 示例代码

``` js
var rong = api.require('rongCloud2');

rong.init(function(ret, err){
	if (ret.status == 'error')
		api.toast({ msg: err.code });
});
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## connect <div id="connect"></div>

连接融云 IM 服务器，进行后续各种方法操作前务必要先调用此方法

connect({params}, callback(ret, err))

### params

token:

- 类型：字符串
- 默认值：无
- 描述：从服务端获取的用户身份令牌（Token）

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：返回的登录成功或者失败的状态

内部字段：

``` js
{
	status: 'success', // 状态码：success / error
	result:
	{
		userId: '9527' // 当前登录的用户 Id
	}
}
```

err:

- 类型：JSON 对象

内部字段：

``` js
{
	code: 31004	// 错误码
}
```

错误说明：

| 错误码    | 说明                                       |
| :----- | :--------------------------------------- |
| 31003  | 服务器不可用                                   |
| 31004  | 错误的令牌（Token），Token 解析失败，请重新向身份认证服务器获取 Token |
| 31002  | 可能是错误的 App Key，或者 App Key 被服务器积极拒绝       |
| 33002  | 服务端数据库错误                                 |
| 31000  | 服务器超时                                    |
| -10000 | 未调用 init 方法进行初始化                         |
| -10002 | 输入参数错误                                   |

### 示例代码

``` js
var rong = api.require('rongCloud2');

rong.init(function(ret, err){
	if (ret.status == 'error')
		api.toast({ msg: err.code });
});

rong.connect({
	token: 'ThptTWyiPPPvZHvuSiuri82yq+hfEluLjZ78E1qo4hEVSFQNpqdoPu406urMWKN4Z3/olWR+v9JVLAwfOQoLrA=='},
	function(ret, err){
		if (ret.status == 'success')
			api.toast({ msg: ret.result.userId });
});
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## ~~reconnect~~ <div id="reconnect"></div>

主动重新连接服务器。融云的 SDK 会自动进行重连，一般情况下您不需要调用这个方法；2.0版本弃用该方法。

reconnect(callback(ret, err))

### 可用性

iOS 系统，Android 系统

此方法在apicloud融云模块1.1.0中支持，由于融云支持掉线后自动重连，所以在2.0.0版本中弃用该方法

## disconnect <div id="disconnect"></div>

断开连接

disconnect({params}, callback(ret, err))

### params

isReceivePush:

- 类型：布尔
- 默认值：true
- 描述：断开后是否接收 Push

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：返回的断开连接成功或者失败的状态

内部字段：

``` js
{
	status: 'success' // 状态码：success
}
```

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

 rong.disconnect({
         isReceivePush: true
     },function (ret, err) {
           if ('success' == ret.status) {
               api.toast({msg: '断开连接成功!'});
           }
       }
 );  // 断开，且不再接收 Push
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## setConnectionStatusListener <div id="setConnectionStatusListener"></div>

设置连接状态变化的监听器，请在调用 init 方法之后，调用 connect 方法之前设置

setConnectionStatusListener(callback(ret, err))

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：连接服务器的回调返回值，参见 [连接状态](#connectionStatus)

内部字段：

``` js
{
	result:
	{
		connectionStatus: 'CONNECTED' // 连接状态
	}
}
```

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 的代码省略

rong.setConnectionStatusListener(function(ret, err){
	api.toast({ msg: ret.result.connectionStatus });
});

// 之后调用 connect 的代码省略
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## sendTextMessage <div id="sendTextMessage"></div>

发送文字消息

sendTextMessage({params}, callback(ret, err))

### params

conversationType:

- 类型：字符串
- 默认值：无
- 描述：消息的会话类型，通过改变消息会话类型，可以发送单聊消息、讨论组消息、群聊消息、聊天室消息等，参见 [会话类型](#conversationType)

targetId:

- 类型：字符串
- 默认值：无
- 描述：消息的接收方 Id。根据不同的 conversationType，可能是用户 Id、讨论组 Id、群组 Id 或聊天室 Id 等

text:

- 类型：字符串
- 默认值：无
- 描述：消息的文字内容

extra:

- 类型：字符串
- 默认值：无
- 描述：消息的附加信息

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：返回的消息内容。发送准备时，提供所有消息信息；之后，result 中将只返回 message.messageId 等必要相关的内容

内部字段：

发送准备：

``` js
{
	status: 'prepare', // 状态码：prepare / success / error
	result:
	{
		message:
		{
			content: {
				text: 'Hello world!',
				extra: ''
			}, // 消息内容
            extra: '',
			conversationType: 'PRIVATE', // 参见 会话类型 枚举
			messageDirection: 'SEND', // 消息方向：SEND 或者 RECEIVE
			targetId: '16', // 接收者 Id
			objectName: 'RC:TxtMsg', // 消息类型，参见 http://docs.rongcloud.cn/android_message.html#_内置内容类消息
			sentStatus: 'SENDING', // 发送状态：SENDING, SENT 或 FAILED
			senderUserId: '55', // 发送者 userId
			messageId: 608, // 本地消息 Id
			sentTime: 1418971531533, // 发送消息的时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数
			receivedTime: 0 // 收到消息的时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数
		}
	}
}
```

成功：

``` js
{
	status: 'success', // 状态码：prepare / success / error
	result:
	{
		message:
		{
			messageId: 608 // 本地消息 Id
		}
	}
}
```

失败：

``` js
{
	status: 'error', // 状态码：prepare / success / error
	result:
	{
		message:
		{
			messageId: 608 // 本地消息 Id
		}
	}
}
```

err:

- 类型：JSON 对象

内部字段：

``` js
{
	code: 30003
}
```

状态码说明：

| 状态码    | 说明                 |
| :----- | :----------------- |
| 30014  | 发送处理失败             |
| 30003  | 服务器超时              |
| 31009  | 用户被屏蔽              |
| -10000 | 未调用 init 方法进行初始化   |
| -10001 | 未调用 connect 方法进行连接 |
| -10002 | 输入参数错误             |
| 405    | 用户在黑名单中            |

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.sendTextMessage({
		conversationType: 'PRIVATE',
		targetId: '9527',
		text: 'Hello world.',
		extra: ''
	}, function (ret, err) {
		if (ret.status == 'prepare')
			api.toast({ msg: JSON.stringify(ret.result.message) });
		else if (ret.status == 'success')
			api.toast({ msg: ret.result.message.messageId });
		else if (ret.status == 'error')
			api.toast({ msg: err.code });
	}
);
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## sendVoiceMessage <div id="sendVoiceMessage"></div>

发送语音消息

sendVoiceMessage({params}, callback(ret, err))

### params

conversationType:

- 类型：字符串
- 默认值：无
- 描述：消息的会话类型，通过改变消息会话类型，可以发送单聊消息、讨论组消息、群聊消息、聊天室消息等，参见 [会话类型](#conversationType)

targetId:

- 类型：字符串
- 默认值：无
- 描述：消息的接收方 Id。根据不同的 conversationType，可能是用户 Id、讨论组 Id、群组 Id 或聊天室 Id 等

voicePath:

- 类型：字符串
- 默认值：无
- 描述：语音文件的路径，支持 fs://，如：fs:///voice/123.amr。文件要求为 AMR 格式

duration:

- 类型：数字
- 默认值：无
- 描述：语音消息的时长，单位为秒

extra:

- 类型：字符串
- 默认值：无
- 描述：消息的附加信息

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：返回的消息内容。发送准备时，提供所有消息信息；之后，result 中将只返回 message.messageId 等必要相关的内容

内部字段：

发送准备：

``` js
{
	status: 'prepare', // 状态码：prepare / success / error
	result:
	{
		message:
		{
			content: {
				voicePath: '/xxx/xxx/voice.amr',
				duration: 5,
				extra: ''
			}, // 消息内容
			conversationType: 'PRIVATE', // 参见 会话类型 枚举
			messageDirection: 'SEND', // 消息方向：SEND 或者 RECEIVE
			targetId: '16', // 接收者 Id
			objectName: 'RC:VcMsg', // 消息类型，参见 http://docs.rongcloud.cn/android_message.html#_内置内容类消息
			sentStatus: 'SENDING', // 发送状态：SENDING, SENT 或 FAILED
			senderUserId: '55', // 发送者 userId
			messageId: 608, // 本地消息 Id
			sentTime: 1418971531533, // 发送消息的时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数
			receivedTime: 0 // 收到消息的时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数
		}
	}
}
```

成功：

``` js
{
	status: 'success', // 状态码：prepare / success / error
	result:
	{
		message:
		{
			messageId: 608 // 本地消息 Id
		}
	}
}
```

失败：

``` js
{
	status: 'error', // 状态码：prepare / success / error
	result:
	{
		message:
		{
			messageId: 608 // 本地消息 Id
		}
	}
}
```

err:

- 类型：JSON 对象

内部字段：

``` js
{
	code: 30003
}
```

状态码说明：

| 状态码    | 说明                 |
| :----- | :----------------- |
| 30014  | 发送处理失败             |
| 30003  | 服务器超时              |
| 31009  | 用户被屏蔽              |
| -10000 | 未调用 init 方法进行初始化   |
| -10001 | 未调用 connect 方法进行连接 |
| -10002 | 输入参数错误             |
| 405    | 用户在黑名单中            |

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.sendVoiceMessage({
		conversationType: 'PRIVATE',
		targetId: '9527',
		voicePath: 'fs:///xxx/xxx/voice.amr',
		duration: 5,
		extra: ''
	}, function (ret, err) {
		if (ret.status == 'prepare')
			api.toast({ msg: JSON.stringify(ret.result.message) });
		else if (ret.status == 'success')
			api.toast({ msg: ret.result.message.messageId });
		else if (ret.status == 'error')
			api.toast({ msg: err.code });
	}
);
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## sendImageMessage <div id="sendImageMessage"></div>

发送图片消息

sendImageMessage({params}, callback(ret, err))

### params

conversationType:

- 类型：字符串
- 默认值：无
- 描述：消息的会话类型，通过改变消息会话类型，可以发送单聊消息、讨论组消息、群聊消息、聊天室消息等，参见 [会话类型](#conversationType)

targetId:

- 类型：字符串
- 默认值：无
- 描述：消息的接收方 Id。根据不同的 conversationType，可能是用户 Id、讨论组 Id、群组 Id 或聊天室 Id 等

imagePath:

- 类型：字符串
- 默认值：无
- 描述：图片的路径，支持 fs://，如：fs:///image/123.jpg

extra:

- 类型：字符串
- 默认值：无
- 描述：消息的附加信息

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：返回的消息内容。发送准备时，提供所有消息信息；之后，result 中将只返回 message.messageId 等必要相关的内容

内部字段：

发送准备：

``` js
{
	status: 'prepare', // 状态码：prepare / progress / success / error
	result:
	{
		message:
		{
			content: {
				localPath: '/xxx/xxx/image.jpg',
				thumbPath: '/xxx/xxx/thumb.jpg',
				extra: ''
			}, // 消息内容
			conversationType: 'PRIVATE', // 参见 会话类型 枚举
			messageDirection: 'SEND', // 消息方向：SEND 或者 RECEIVE
			targetId: '16', // 接收者 Id
			objectName: 'RC:ImgMsg', // 消息类型，参见 http://docs.rongcloud.cn/android_message.html#_内置内容类消息
			sentStatus: 'SENDING', // 发送状态：SENDING, SENT 或 FAILED
			senderUserId: '55', // 发送者 userId
			messageId: 608, // 本地消息 Id
			sentTime: 1418971531533, // 发送消息的时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数
			receivedTime: 0 // 收到消息的时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数
		}
	}
}
```

发送中：

``` js
{
	status: 'progress', // 状态码：prepare / progress / success / error
	result:
	{
		message:
		{
			messageId: 608 // 本地消息 Id
		},
		progress: 66 // 发送进度
	}
}
```

成功：

``` js
{
	status: 'success', // 状态码：prepare / progress / success / error
	result:
	{
		message:
		{
			messageId: 608 // 本地消息 Id
		}
	}
}
```

失败：

``` js
{
	status: 'error', // 状态码：prepare / progress / success / error
	result:
	{
		message:
		{
			sentStatus: 'FAILED', // 发送状态：SENDING, SENT 或 FAILED
			messageId: 608 // 本地消息 Id
		}
	}
}
```

err:

- 类型：JSON 对象

内部字段：

``` js
{
	code: 30003
}
```

状态码说明：

| 状态码    | 说明                 |
| :----- | :----------------- |
| 30014  | 发送处理失败             |
| 30003  | 服务器超时              |
| 31009  | 用户被屏蔽              |
| -10000 | 未调用 init 方法进行初始化   |
| -10001 | 未调用 connect 方法进行连接 |
| -10002 | 输入参数错误             |
| 405    | 用户在黑名单中            |

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.sendImageMessage({
		conversationType: 'PRIVATE',
		targetId: '9527',
		imagePath: 'fs:///xxx/xxx/picture.jpg',
		extra: ''
	}, function (ret, err) {
		if (ret.status == 'prepare')
			api.toast({ msg: JSON.stringify(ret.result.message) });
		else if (ret.status == 'progress')
			api.toast({ msg: ret.result.progress });
		else if (ret.status == 'success')
			api.toast({ msg: ret.result.message.messageId });
		else if (ret.status == 'error')
			api.toast({ msg: err.code });
	}
);
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## sendRichContentMessage <div id="sendRichContentMessage"></div>

发送图文消息

sendRichContentMessage({params}, callback(ret, err))

### params

conversationType:

- 类型：字符串
- 默认值：无
- 描述：消息的会话类型，通过改变消息会话类型，可以发送单聊消息、讨论组消息、群聊消息、聊天室消息等，参见 [会话类型](#conversationType)

targetId:

- 类型：字符串
- 默认值：无
- 描述：消息的接收方 Id。根据不同的 conversationType，可能是用户 Id、讨论组 Id、群组 Id 或聊天室 Id 等

title:

- 类型：字符串
- 默认值：无
- 描述：消息的标题

description:

- 类型：字符串
- 默认值：无
- 描述：消息的内容描述

imageUrl:

- 类型：字符串
- 默认值：无
- 描述：消息图片的网络地址

extra:

- 类型：字符串
- 默认值：无
- 描述：消息的附加信息

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：返回的消息内容。发送准备时，提供所有消息信息；之后，result 中将只返回 message.messageId 等必要相关的内容

内部字段：

发送准备：

``` js
{
	status: 'prepare', // 状态码：prepare / success / error
	result:
	{
		message:
		{
			content: {
				title: 'Big News',
				description: 'I am Ironman.',
				imageUrl: 'http://p1.cdn.com/fds78ruhi.jpg',
				extra: ''，
                url: ''
			}, // 消息内容
			conversationType: 'PRIVATE', // 参见 会话类型 枚举
			messageDirection: 'SEND', // 消息方向：SEND 或者 RECEIVE
			targetId: '16', // 接收者 Id
			objectName: 'RC:ImgTextMsg', // 消息类型，参见 http://docs.rongcloud.cn/android_message.html#_内置内容类消息
			sentStatus: 'SENDING', // 发送状态：SENDING, SENT 或 FAILED
			senderUserId: '55', // 发送者 userId
			messageId: 608, // 本地消息 Id
			sentTime: 1418971531533, // 发送消息的时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数
			receivedTime: 0 // 收到消息的时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数
		}
	}
}
```

成功：

``` js
{
	status: 'success', // 状态码：prepare / success / error
	result:
	{
		message:
		{
			messageId: 608 // 本地消息 Id
		}
	}
}
```

失败：

``` js
{
	status: 'error', // 状态码：prepare / success / error
	result:
	{
		message:
		{
			sentStatus: 'FAILED', // 发送状态：SENDING, SENT 或 FAILED
			messageId: 608 // 本地消息 Id
		}
	}
}
```

err:

- 类型：JSON 对象

内部字段：

``` js
{
	code: 30003
}
```

状态码说明：

| 状态码    | 说明                 |
| :----- | :----------------- |
| 30014  | 发送处理失败             |
| 30003  | 服务器超时              |
| 31009  | 用户被屏蔽              |
| -10000 | 未调用 init 方法进行初始化   |
| -10001 | 未调用 connect 方法进行连接 |
| -10002 | 输入参数错误             |
| 405    | 用户在黑名单中            |

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.sendRichContentMessage({
		conversationType: 'PRIVATE',
		targetId: '9527',
		title: 'Big News',
		description: 'I am Ironman.'
		imageUrl: 'http://ironman.com/xxx/xxx/picture.jpg',
		extra: ''
	}, function (ret, err) {
		if (ret.status == 'prepare')
			api.toast({ msg: JSON.stringify(ret.result.message) });
		else if (ret.status == 'success')
			api.toast({ msg: ret.result.message.messageId });
		else if (ret.status == 'error')
			api.toast({ msg: err.code });
	}
);
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## sendLocationMessage <div id="sendLocationMessage"></div>

发送位置消息

sendLocationMessage({params}, callback(ret, err))

### params

conversationType:

- 类型：字符串
- 默认值：无
- 描述：消息的会话类型，通过改变消息会话类型，可以发送单聊消息、讨论组消息、群聊消息、聊天室消息等，参见 [会话类型](#conversationType)

targetId:

- 类型：字符串
- 默认值：无
- 描述：消息的接收方 Id。根据不同的 conversationType，可能是用户 Id、讨论组 Id、群组 Id 或聊天室 Id 等

latitude:

- 类型：数字
- 默认值：无
- 描述：消息的文字内容

longitude:

- 类型：数字
- 默认值：无
- 描述：消息的文字内容

poi:

- 类型：字符串
- 默认值：无
- 描述：消息的文字内容

imagePath:

- 类型：字符串
- 默认值：无
- 描述：地图缩率图的路径，支持 fs://，如：fs:///location_thumb/123.jpg

extra:

- 类型：字符串
- 默认值：无
- 描述：消息的附加信息

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：返回的消息内容。发送准备时，提供所有消息信息；之后，result 中将只返回 message.messageId 等必要相关的内容

内部字段：

发送准备：

``` js
{
	status: 'prepare', // 状态码：prepare / progress / success / error
	result:
	{
		message:
		{
			content: {
				latitude: 39.9139
				longitude: 116.3917
				poi: '北京市朝阳区北苑路北辰泰岳大厦',
				imagePath: '/xxx/xxx/location.jpg'
				extra: ''
			}, // 消息内容
			conversationType: 'PRIVATE', // 参见 会话类型 枚举
			messageDirection: 'SEND', // 消息方向：SEND 或者 RECEIVE
			targetId: '16', // 接收者 Id
			objectName: 'RC:LBSMsg', // 消息类型，参见 http://docs.rongcloud.cn/android_message.html#_内置内容类消息
			sentStatus: 'SENDING', // 发送状态：SENDING, SENT 或 FAILED
			senderUserId: '55', // 发送者 userId
			messageId: 608, // 本地消息 Id
			sentTime: 1418971531533, // 发送消息的时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数
			receivedTime: 0 // 收到消息的时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数
		}
	}
}
```

发送中：

``` js
{
	status: 'progress', // 状态码：prepare / progress / success / error
	result:
	{
		message:
		{
			messageId: 608 // 本地消息 Id
		},
		progress: 66 // 发送进度
	}
}
```

成功：

``` js
{
	status: 'success', // 状态码：prepare / progress / success / error
	result:
	{
		message:
		{
			messageId: 608 // 本地消息 Id
		}
	}
}
```

失败：

``` js
{
	status: 'error', // 状态码：prepare / progress / success / error
	result:
	{
		message:
		{
			messageId: 608 // 本地消息 Id
		}
	}
}
```

err:

- 类型：JSON 对象

内部字段：

``` js
{
	code: 30003
}
```

状态码说明：

| 状态码    | 说明                 |
| :----- | :----------------- |
| 30014  | 发送处理失败             |
| 30003  | 服务器超时              |
| 31009  | 用户被屏蔽              |
| -10000 | 未调用 init 方法进行初始化   |
| -10001 | 未调用 connect 方法进行连接 |
| -10002 | 输入参数错误             |
| 405    | 用户在黑名单中            |

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.sendLocationMessage({
		conversationType: 'PRIVATE',
		targetId: '9527',
		latitude: 39.9139,
		longitude: 116.3917,
		poi: '北京市朝阳区北苑路北辰泰岳大厦',
		imagePath: 'fs:///xxx/xxx/location.jpg',
		extra: ''
	}, function (ret, err) {
		if (ret.status == 'prepare')
			api.toast({ msg: JSON.stringify(ret.result.message) });
		else if (ret.status == 'progress')
			api.toast({ msg: ret.result.progress });
		else if (ret.status == 'success')
			api.toast({ msg: ret.result.message.messageId });
		else if (ret.status == 'error')
			api.toast({ msg: err.code });
	}
);
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## sendCommandNotificationMessage <div id="sendCommandNotificationMessage"></div>

发送命令消息，可以用来实现任何自定义消息的发送

sendCommandNotificationMessage({params}, callback(ret, err))

### params

conversationType:

- 类型：字符串
- 默认值：无
- 描述：消息的会话类型，通过改变消息会话类型，可以发送单聊消息、讨论组消息、群聊消息、聊天室消息等，参见 [会话类型](#conversationType)

targetId:

- 类型：字符串
- 默认值：无
- 描述：消息的接收方 Id。根据不同的 conversationType，可能是用户 Id、讨论组 Id、群组 Id 或聊天室 Id 等

name:

- 类型：字符串
- 默认值：无
- 描述：命令的名称

data:

- 类型：字符串
- 默认值：无
- 描述：命令的数据

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：返回的消息内容。发送准备时，提供所有消息信息；之后，result 中将只返回 message.messageId 等必要相关的内容

内部字段：

发送准备：

``` js
{
	status: 'prepare', // 状态码：prepare / success / error
	result:
	{
		message:
		{
			content: {
				name: 'AddFriend',
				data: '{\"inviteUserId\":123}'
			}, // 消息内容
			conversationType: 'PRIVATE', // 参见 会话类型 枚举
			messageDirection: 'SEND', // 消息方向：SEND 或者 RECEIVE
			targetId: '16', // 接收者 Id
			objectName: 'RC:TxtMsg', // 消息类型，参见 http://docs.rongcloud.cn/android_message.html#_内置内容类消息
			sentStatus: 'SENDING', // 发送状态：SENDING, SENT 或 FAILED
			senderUserId: '55', // 发送者 userId
			messageId: 608, // 本地消息 Id
			sentTime: 1418971531533, // 发送消息的时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数
			receivedTime: 0 // 收到消息的时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数
		}
	}
}
```

成功：

``` js
{
	status: 'success', // 状态码：prepare / success / error
	result:
	{
		message:
		{
			messageId: 608 // 本地消息 Id
		}
	}
}
```

失败：

``` js
{
	status: 'error', // 状态码：prepare / success / error
	result:
	{
		message:
		{
			messageId: 608 // 本地消息 Id
		}
	}
}
```

err:

- 类型：JSON 对象

内部字段：

``` js
{
	code: 30003
}
```

状态码说明：

| 状态码    | 说明                 |
| :----- | :----------------- |
| 30014  | 发送处理失败             |
| 30003  | 服务器超时              |
| 31009  | 用户被屏蔽             |
| -10000 | 未调用 init 方法进行初始化   |
| -10001 | 未调用 connect 方法进行连接 |
| -10002 | 输入参数错误             |
| 405    | 用户在黑名单中            |

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.sendCommandNotificationMessage({
		conversationType: 'PRIVATE',
		targetId: '9527',
		name: 'AddFriend',
		data: '{\"inviteUserId\":123}'
	}, function (ret, err) {
		if (ret.status == 'prepare')
			api.toast({ msg: JSON.stringify(ret.result.message) });
		else if (ret.status == 'success')
			api.toast({ msg: ret.result.message.messageId });
		else if (ret.status == 'error')
			api.toast({ msg: err.code });
	}
);
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## sendCommandMessage <div id="sendCommandMessage"></div>

发送命令消息，您需要这种类型的消息时可以直接使用，不需要再自定义。此消息不保存、不计数。

sendCommandMessage({params}, callback(ret, err))

### params

conversationType:

- 类型：字符串
- 默认值：无
- 描述：消息的会话类型，通过改变消息会话类型，可以发送单聊消息、讨论组消息、群聊消息、聊天室消息等，参见 [会话类型](#conversationType)

targetId:

- 类型：字符串
- 默认值：无
- 描述：消息的接收方 Id。根据不同的 conversationType，可能是用户 Id、讨论组 Id、群组 Id 或聊天室 Id 等

name:

- 类型：字符串
- 默认值：无
- 描述：命令的名称

data:

- 类型：字符串
- 默认值：无
- 描述：命令的数据

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：返回的消息内容。发送准备时，提供所有消息信息；之后，result 中将只返回 message.messageId 等必要相关的内容

内部字段：

发送准备：

``` js
{
	status: 'prepare', // 状态码：prepare / success / error
	result:
	{
		message:
		{
			content: {
				name: 'AddFriend',
				data: '{\"inviteUserId\":123}'
			}, // 消息内容
			conversationType: 'PRIVATE', // 参见 会话类型 枚举
			messageDirection: 'SEND', // 消息方向：SEND 或者 RECEIVE
			targetId: '16', // 接收者 Id
			objectName: 'RC:TxtMsg', // 消息类型，参见 http://docs.rongcloud.cn/android_message.html#_内置内容类消息
			sentStatus: 'SENDING', // 发送状态：SENDING, SENT 或 FAILED
			senderUserId: '55', // 发送者 userId
			messageId: 608, // 本地消息 Id
			sentTime: 1418971531533, // 发送消息的时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数
			receivedTime: 0 // 收到消息的时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数
		}
	}
}
```

成功：

``` js
{
	status: 'success', // 状态码：prepare / success / error
	result:
	{
		message:
		{
			messageId: 608 // 本地消息 Id
		}
	}
}
```

失败：

``` js
{
	status: 'error', // 状态码：prepare / success / error
	result:
	{
		message:
		{
			messageId: 608 // 本地消息 Id
		}
	}
}
```

err:

- 类型：JSON 对象

内部字段：

``` js
{
	code: 30003
}
```

状态码说明：

| 状态码    | 说明                 |
| :----- | :----------------- |
| 30014  | 发送处理失败             |
| 30003  | 服务器超时              |
| 31009  | 用户被屏蔽              |
| -10000 | 未调用 init 方法进行初始化   |
| -10001 | 未调用 connect 方法进行连接 |
| -10002 | 输入参数错误             |
| 405    | 用户在黑名单中            |

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.sendCommandMessage({
		conversationType: 'PRIVATE',
		targetId: '9527',
		name: 'AddFriend',
		data: '{\"inviteUserId\":123}'
	}, function (ret, err) {
		if (ret.status == 'prepare')
			api.toast({ msg: JSON.stringify(ret.result.message) });
		else if (ret.status == 'success')
			api.toast({ msg: ret.result.message.messageId });
		else if (ret.status == 'error')
			api.toast({ msg: err.code });
	}
);
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## setOnReceiveMessageListener <div id="setOnReceiveMessageListener"></div>

设置接收消息的监听器，请在调用 init 方法之后，调用 connect 方法之前设置

所有接收到的消息、通知、状态都经由此处设置的监听器处理。包括私聊消息、讨论组消息、群组消息、聊天室消息以及各种其他消息、通知、状态等

setOnReceiveMessageListener(callback(ret, err))

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：接收到的消息内容和剩余消息条数

内部字段：

``` js
{
	result:
	{
		message:
		{
			content: {
				text: 'Hello world!',
				extra: ''
			}, // 消息内容
			conversationType: 'PRIVATE', // 参见 会话类型 枚举
			messageDirection: 'SEND', // 消息方向：SEND 或者 RECEIVE
			targetId: '55', // 这里对应消息发送者的 userId
			objectName: 'RC:TxtMsg', // 消息类型，参见 http://docs.rongcloud.cn/android_message.html#_内置内容类消息
			sentStatus: 'SENDING', // 发送状态：SENDING, SENT 或 FAILED
			senderUserId: '55', // 发送者 userId
			messageId: 608, // 本地消息 Id
			sentTime: 1418971531533, // 发送消息的时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数
			receivedTime: 0 // 收到消息的时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数
		},
		left: 0 // 剩余未拉取的消息数目
	}
}
```

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 的代码省略

rong.setOnReceiveMessageListener(function (ret, err) {
	api.toast({ msg: JSON.stringify(ret.result.message) });
	api.toast({ msg: ret.result.message.left });
})

// 之后调用 connect 的代码省略
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## getConversationList <div id="getConversationList"></div>

获取会话列表

会话列表按照时间从前往后排列，如果有置顶会话，则置顶会话在前

getConversationList(callback(ret, err))

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：会话列表

内部字段：

``` js
{
	status: 'success',
	result: [
		{
			conversationTitle: 'Ironman', // 会话标题
			conversationType: 'PRIVATE', // 参见 会话类型 枚举
			draft: '', // 文字消息草稿的内容
			targetId: 'group001', // 消息目标 Id
			latestMessage: {
				text: 'Hello world!',
				extra: ''
			}, // 最后一条消息的内容
			sentStatus: 'SENT', // 参见 发送出的消息状态
			*notificationStatus: 'NOTIFY', // 会话通知状态，2.0.0将不再提供此字段，可通过 getConversationNotificationStatus 获取
			objectName: 'RC:TxtMsg', // 消息类型，参见 http://docs.rongcloud.cn/android_message.html#_内置内容类消息
			receivedStatus: 'READ', // 参见 接收到的消息状态
			senderUserId: '55', // 发送消息的用户 Id
			unreadMessageCount: 10, // 本会话的未读消息数
			receivedTime: 1418968547905, // 发送消息的时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数
			sentTime: 1418968488063, // 收到消息的时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数
			isTop: false, // 置顶状态
			latestMessageId: 608 // 本会话最后一条消息 Id
		}
	]
}
```

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.getConversationList(function (ret, err) {
	api.toast({ msg: JSON.stringify(ret.result) });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## getConversation <div id="getConversation"></div>

获取某一会话信息

getConversation({params}, callback(ret, err))

### params

conversationType:

- 类型：字符串
- 默认值：无
- 描述：消息的会话类型，参见 [会话类型](#conversationType)

targetId:

- 类型：字符串
- 默认值：无
- 描述：目标 Id。根据不同的 conversationType，可能是用户 Id、讨论组 Id、群组 Id 或聊天室 Id 等

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：会话信息

内部字段：

``` js
{
	status: 'success',
	result: {
		conversationTitle: 'Ironman', // 会话标题
		conversationType: 'PRIVATE', // 参见 会话类型 枚举
		draft: '', // 文字消息草稿的内容
		targetId: 'group001', // 消息目标 Id
		latestMessage: {
				text: 'Hello world!',
				extra: ''
			}, // 最后一条消息的内容
			sentStatus: 'SENT', // 参见 发送出的消息状态
			*notificationStatus: 'NOTIFY', // 会话通知状态，2.0将不再提供此字段，可通过 getConversationNotificationStatus 获取
			objectName: 'RC:TxtMsg', // 消息类型，参见 http://docs.rongcloud.cn/android_message.html#_内置内容类消息
			recievedStatus: 0, // 参见 接收到的消息状态
			senderUserId: '55', // 发送消息的用户 Id
			unreadMessageCount: 10, // 本会话的未读消息数
			receivedTime: 1418968547905, // 发送消息的时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数
			sentTime: 1418968488063, // 收到消息的时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数
			isTop: false, // 置顶状态
			latestMessageId: 608 // 本会话最后一条消息 Id
		}
}
```

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.getConversation({
		conversationType: 'PRIVATE',
		targetId: '9527'
	}, function (ret, err) {
		api.toast({ msg: JSON.stringify(ret.result) });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## removeConversation <div id="removeConversation"></div>

从会话列表中移除某一会话，但是不删除会话内的消息

如果此会话中有新的消息，该会话将重新在会话列表中显示，并显示最近的历史消息

removeConversation({params}, callback(ret, err))

### params

conversationType:

- 类型：字符串
- 默认值：无
- 描述：消息的会话类型，参见 [会话类型](#conversationType)

targetId:

- 类型：字符串
- 默认值：无
- 描述：目标 Id。根据不同的 conversationType，可能是用户 Id、讨论组 Id、群组 Id 或聊天室 Id 等

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：操作结果

内部字段：

``` js
{
	status: 'success' // 状态码：success / error
}
```

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.removeConversation({
		conversationType: 'PRIVATE',
		targetId: '9527'
	}, function (ret, err) {
		api.toast({ msg: ret.status });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## clearConversations <div id="clearConversations"></div>

清空所有会话及会话消息

clearConversations({params}, callback(ret, err))

### params

conversationTypes:

- 类型：字符串数组
- 默认值：无
- 描述：消息的会话类型，参见 [会话类型](#conversationType)

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：操作结果

内部字段：

``` js
{
	status: 'success' // 状态码：success / error
}
```

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.clearConversations({
		conversationTypes: ['PRIVATE', 'GROUP']
	}, function (ret, err) {
		api.toast({ msg: ret.status });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## setConversationToTop <div id="setConversationToTop"></div>

设置某一会话为置顶或者取消置顶

setConversationToTop({params}, callback(ret, err))

### params

conversationType:

- 类型：字符串
- 默认值：无
- 描述：消息的会话类型，参见 [会话类型](#conversationType)

targetId:

- 类型：字符串
- 默认值：无
- 描述：目标 Id。根据不同的 conversationType，可能是用户 Id、讨论组 Id、群组 Id 或聊天室 Id 等

isTop:

- 类型：布尔
- 默认值：无
- 描述：是否置顶

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：操作结果

内部字段：

``` js
{
	status: 'success' // 状态码：success / error
}
```

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.setConversationToTop({
		conversationType: 'PRIVATE',
		targetId: '9527',
		isTop: true
	}, function (ret, err) {
		api.toast({ msg: ret.status });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## getConversationNotificationStatus <div id="getConversationNotificationStatus"></div>

获取某一会话的通知状态

getConversationNotificationStatus({params}, callback(ret, err))

### params

conversationType:

- 类型：字符串
- 默认值：无
- 描述：消息的会话类型，参见 [会话类型](#conversationType)

targetId:

- 类型：字符串
- 默认值：无
- 描述：目标 Id。根据不同的 conversationType，可能是用户 Id、讨论组 Id、群组 Id 或聊天室 Id 等

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：操作结果

内部字段：

``` js
{
	status: 'success', // 状态码：success / error
	result: {
		code: 0 // 状态码，0：免打扰 / 1：提醒
		notificationStatus: 'DO_NOT_DISTURB' // 参见 会话通知提醒状态 枚举
	}
}
```

err:

- 类型：JSON 对象

内部字段：

``` js
{
	code: 30003
}
```

状态码说明：

| 状态码    | 说明                 |
| :----- | :----------------- |
| 30003  | 服务器超时              |
| -10000 | 未调用 init 方法进行初始化   |
| -10001 | 未调用 connect 方法进行连接 |
| -10002 | 输入参数错误             |

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.getConversationNotificationStatus({
		conversationType: 'PRIVATE',
		targetId: '9527'
	}, function (ret, err) {
		if (ret.status == 'success')
			api.toast({ msg: ret.result.code });
		else
			api.toast({ msg: err.code });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## setConversationNotificationStatus <div id="setConversationNotificationStatus"></div>

设置某一会话的通知状态

setConversationNotificationStatus({params}, callback(ret, err))

### params

conversationType:

- 类型：字符串
- 默认值：无
- 描述：消息的会话类型，参见 [会话类型](#conversationType)

targetId:

- 类型：字符串
- 默认值：无
- 描述：目标 Id。根据不同的 conversationType，可能是用户 Id、讨论组 Id、群组 Id 或聊天室 Id 等

notificationStatus:

- 类型：字符串
- 默认值：无
- 描述：会话通知提醒状态，参见 [会话通知提醒状态](#conversationNotificationStatus)

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：操作结果

内部字段：

``` js
{
	status: 'success', // 状态码：success / error
	result: {
		code: 0 // 状态码，0：免打扰 / 1：提醒
		notificationStatus: "DO_NOT_DISTURB" // 参见 会话通知提醒状态 枚举
	}
}
```

err:

- 类型：JSON 对象

内部字段：

``` js
{
	code: 30003
}
```

状态码说明：

| 状态码    | 说明                 |
| :----- | :----------------- |
| 300003 | 服务器超时              |
| -10000 | 未调用 init 方法进行初始化   |
| -10001 | 未调用 connect 方法进行连接 |
| -10002 | 输入参数错误             |

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.setConversationNotificationStatus({
		conversationType: 'PRIVATE',
		targetId: '9527',
		notificationStatus: 'DO_NOT_DISTURB'
	}, function (ret, err) {
		if (ret.status == 'success')
			api.toast({ msg: ret.result.code });
		else
			api.toast({ msg: err.code });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## getLatestMessages <div id="getLatestMessages"></div>

获取某一会话的最新消息记录

getLatestMessages({params}, callback(ret, err))

### params

conversationType:

- 类型：字符串
- 默认值：无
- 描述：消息的会话类型，参见 [会话类型](#conversationType)

targetId:

- 类型：字符串
- 默认值：无
- 描述：目标 Id。根据不同的 conversationType，可能是用户 Id、讨论组 Id、群组 Id 或聊天室 Id 等

count:

- 类型：数字
- 默认值：无
- 描述：要获取的消息数量

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：最新消息记录，按照时间顺序从新到旧排列。

内部字段：

``` js
{
	status: 'success',
	result: [
		{
			content: {
				text: 'Hello world!',
				extra: ''
			}, // 消息内容
            extra: '', // 消息的附加信息，此信息只保存在本地
			conversationType: 'PRIVATE', // 参见 会话类型 枚举
			messageDirection: 'SEND', // 消息方向：SEND 或者 RECEIVE
			targetId: '55', // 这里对应消息发送者的 userId
			objectName: 'RC:TxtMsg', // 消息类型，参见 http://docs.rongcloud.cn/android_message.html#_内置内容类消息
			sentStatus: 'SENDING', // 参见 发送出的消息状态
			senderUserId: '55', // 发送者 userId
			messageId: 608, // 本地消息 Id
			sentTime: 1418971531533, // 发送消息的时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数
			receivedTime: 0 // 收到消息的时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数
		}
	]
}
```

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.getLatestMessages({
		conversationType: 'PRIVATE',
		targetId: '9527',
		count: 20
	}, function (ret, err) {
		api.toast({ msg: JSON.stringify(ret.result) });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## getHistoryMessages <div id="getHistoryMessages"></div>

获取某一会话的历史消息记录

getHistoryMessages({params}, callback(ret, err))

### params

conversationType:

- 类型：字符串
- 默认值：无
- 描述：消息的会话类型，参见 [会话类型](#conversationType)

targetId:

- 类型：字符串
- 默认值：无
- 描述：目标 Id。根据不同的 conversationType，可能是用户 Id、讨论组 Id、群组 Id 或聊天室 Id 等

oldestMessageId:

- 类型：数字
- 默认值：无
- 描述：最后一条消息的 Id，获取此消息之前的 count 条消息，没有消息第一次调用应设置为: -1

count:

- 类型：数字
- 默认值：无
- 描述：要获取的消息数量

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：最新消息记录，按照时间顺序从新到旧排列。

内部字段：

``` js
{
	status: 'success',
	result: [
		{
			content: {
				text: 'Hello world!',
				extra: ''
			}, // 消息内容
            extra: '', // 消息的附加信息，此信息只保存在本地
			conversationType: 'PRIVATE', // 参见 会话类型 枚举
			messageDirection: 'SEND', // 消息方向：SEND 或者 RECEIVE
			targetId: '55', // 这里对应消息发送者的 userId
			objectName: 'RC:TxtMsg', // 消息类型，参见 http://docs.rongcloud.cn/android_message.html#_内置内容类消息
			sentStatus: 'SENDING', // 参见 发送出的消息状态
			senderUserId: '55', // 发送者 userId
			messageId: 608, // 本地消息 Id
			sentTime: 1418971531533, // 发送消息的时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数
			receivedTime: 0 // 收到消息的时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数
		}
	]
}
```

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.getHistoryMessages({
		conversationType: 'PRIVATE',
		targetId: '9527',
		oldestMessageId: 688,
		count: 20
	}, function (ret, err) {
		api.toast({ msg: JSON.stringify(ret.result) });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## getHistoryMessagesByObjectName <div id="getHistoryMessagesByObjectName"></div>

按照消息类型获取历史消息记录

getHistoryMessagesByObjectName({params}, callback(ret, err))

### params

conversationType:

- 类型：字符串
- 默认值：无
- 描述：消息的会话类型，参见 [会话类型](#conversationType)

targetId:

- 类型：字符串
- 默认值：无
- 描述：目标 Id。根据不同的 conversationType，可能是用户 Id、讨论组 Id、群组 Id 或聊天室 Id 等

objectName:

- 类型：字符串
- 默认值：无
- 描述：消息类型标识

oldestMessageId:

- 类型：数字
- 默认值：无
- 描述：最后一条消息的 Id，获取此消息之前的 count 条消息，没有消息第一次调用应设置为: -1

count:

- 类型：数字
- 默认值：无
- 描述：要获取的消息数量

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：最新消息记录，按照时间顺序从新到旧排列。

内部字段：

``` js
{
	status: 'success',
	result: [
		{
			content: {
				text: 'Hello world!',
				extra: ''
			}, // 消息内容
            extra: '', // 消息的附加信息，此信息只保存在本地
			conversationType: 'PRIVATE', // 参见 会话类型 枚举
			messageDirection: 'SEND', // 消息方向：SEND 或者 RECEIVE
			targetId: '55', // 这里对应消息发送者的 userId
			objectName: 'RC:TxtMsg', // 消息类型，参见 http://docs.rongcloud.cn/android_message.html#_内置内容类消息
			sentStatus: 'SENDING', // 参见 发送出的消息状态
			senderUserId: '55', // 发送者 userId
			messageId: 608, // 本地消息 Id
			sentTime: 1418971531533, // 发送消息的时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数
			receivedTime: 0 // 收到消息的时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数
		}
	]
}
```

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.getHistoryMessagesByObjectName({
		conversationType: 'PRIVATE',
		targetId: '9527',
		objectName: 'RC:TxtMsg',
		oldestMessageId: 688,
		count: 20
	}, function (ret, err) {
		api.toast({ msg: JSON.stringify(ret.result) });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## deleteMessages <div id="deleteMessages"></div>

删除指定的一条或者一组消息

deleteMessages({params}, callback(ret, err))

### params

messageIds:

- 类型：数字数组
- 默认值：无
- 描述：要删除的消息 Id 数组

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：操作结果

内部字段：

``` js
{
	status: 'success' // 状态码：success / error
}
```

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.deleteMessages({
		messageIds: [688, 689]
	}, function (ret, err) {
		api.toast({ msg: ret.status });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## clearMessages <div id="clearMessages"></div>

清空某一会话的所有聊天消息记录

clearMessages({params}, callback(ret, err))

### params

conversationType:

- 类型：字符串
- 默认值：无
- 描述：消息的会话类型，参见 [会话类型](#conversationType)

targetId:

- 类型：字符串
- 默认值：无
- 描述：目标 Id。根据不同的 conversationType，可能是用户 Id、讨论组 Id、群组 Id 或聊天室 Id 等

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：操作结果

内部字段：

``` js
{
	status: 'success' // 状态码：success / error
}
```

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.clearMessages({
		conversationType: 'PRIVATE',
		targetId: '9527'
	}, function (ret, err) {
		api.toast({ msg: ret.status });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## getTotalUnreadCount <div id="getTotalUnreadCount"></div>

获取所有未读消息数

getTotalUnreadCount(callback(ret, err))

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：操作结果

内部字段：

``` js
{
	status: 'success',
	result: 12 // 未读消息数
}
```

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.getTotalUnreadCount(function (ret, err) {
	api.toast({ msg: ret.result });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## getUnreadCount <div id="getUnreadCount"></div>

获取来自某用户（某会话）的未读消息数

getUnreadCount({params}, callback(ret, err))

### params

conversationType:

- 类型：字符串
- 默认值：无
- 描述：消息的会话类型，参见 [会话类型](#conversationType)

targetId:

- 类型：字符串
- 默认值：无
- 描述：目标 Id。根据不同的 conversationType，可能是用户 Id、讨论组 Id、群组 Id 或聊天室 Id 等

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：操作结果

内部字段：

``` js
{
	status: 'success',
	result: 12 // 未读消息数
}
```

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.getUnreadCount({
		conversationType: 'PRIVATE',
		targetId: '9527'
	}, function (ret, err) {
		api.toast({ msg: ret.result });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## getUnreadCountByConversationTypes <div id="getUnreadCountByConversationTypes"></div>

获取某（些）会话类型的未读消息数

getUnreadCountByConversationTypes({params}, callback(ret, err))

### params

conversationTypes:

- 类型：字符串数组
- 默认值：无
- 描述：消息的会话类型，参见 [会话类型](#conversationType)

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：操作结果

内部字段：

``` js
{
	status: 'success',
	result: 12 // 未读消息数
}
```

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.getUnreadCountByConversationTypes({
		conversationTypes: ['PRIVATE', 'GROUP']
	}, function (ret, err) {
		api.toast({ msg: ret.result });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## setMessageReceivedStatus <div id="setMessageReceivedStatus"></div>

设置接收到的消息状态

setMessageReceivedStatus({params}, callback(ret, err))

### params

messageId:

- 类型：数字
- 默认值：无
- 描述：消息 Id

*receivedStatus:*

- 类型：字符串
- 默认值：无
- 描述：设置接收到的消息状态，参见 [接收到的消息状态](#receivedStatus)
- 特别说明：此参数在1.0版本中为数字类型，在2.0版本中统一了消息状态，变更为字符串类型

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：操作结果

内部字段：

``` js
{
	status: 'success' // 状态码：success / error
}
```

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.setMessageReceivedStatus({
		messageId: '688',
		receivedStatus: 'READ'
	}, function (ret, err) {
		api.toast({ msg: ret.status });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## clearMessagesUnreadStatus <div id="clearMessagesUnreadStatus"></div>

清除某一会话的消息未读状态

clearMessagesUnreadStatus({params}, callback(ret, err))

### params

conversationType:

- 类型：字符串
- 默认值：无
- 描述：消息的会话类型，参见 [会话类型](#conversationType)

targetId:

- 类型：字符串
- 默认值：无
- 描述：目标 Id。根据不同的 conversationType，可能是用户 Id、讨论组 Id、群组 Id 或聊天室 Id 等

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：操作结果

内部字段：

``` js
{
	status: 'success' // 状态码：success / error
}
```

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.clearMessagesUnreadStatus({
		conversationType: 'PRIVATE',
		targetId: '9527'
	}, function (ret, err) {
		api.toast({ msg: ret.status });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## setMessageExtra <div id="setMessageExtra"></div>

设置消息的附加信息，此信息只保存在本地

setMessageExtra({params}, callback(ret, err))

### params

messageId:

- 类型：数字
- 默认值：无
- 描述：消息 Id

value:

- 类型：字符串
- 默认值：无
- 描述：消息附加信息，最大 1024 字节

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：操作结果

内部字段：

``` js
{
	status: 'success' // 状态码：success / error
}
```

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.setMessageExtra({
		messageId: '688',
		value: 'extra info'
	}, function (ret, err) {
		api.toast({ msg: ret.status });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## getTextMessageDraft <div id="getTextMessageDraft"></div>

获取某一会话的文字消息草稿

getTextMessageDraft({params}, callback(ret, err))

### params

conversationType:

- 类型：字符串
- 默认值：无
- 描述：消息的会话类型，参见 [会话类型](#conversationType)

targetId:

- 类型：字符串
- 默认值：无
- 描述：目标 Id。根据不同的 conversationType，可能是用户 Id、讨论组 Id、群组 Id 或聊天室 Id 等

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：操作结果

内部字段：

``` js
{
	status: 'success',
	result: 'Hello w' // 草稿的文字内容
}
```

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.getTextMessageDraft({
		conversationType: 'PRIVATE',
		targetId: '9527'
	}, function (ret, err) {
		api.toast({ msg: ret.result });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## saveTextMessageDraft <div id="saveTextMessageDraft"></div>

保存某一会话的文字消息草稿

saveTextMessageDraft({params}, callback(ret, err))

### params

conversationType:

- 类型：字符串
- 默认值：无
- 描述：消息的会话类型，参见 [会话类型](#conversationType)

targetId:

- 类型：字符串
- 默认值：无
- 描述：目标 Id。根据不同的 conversationType，可能是用户 Id、讨论组 Id、群组 Id 或聊天室 Id 等

content:

- 类型：字符串
- 默认值：无
- 描述：草稿的文字内容

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：操作结果

内部字段：

``` js
{
	status: 'success' // 状态码：success / error
}
```

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.saveTextMessageDraft({
		conversationType: 'PRIVATE',
		targetId: '9527',
		content: 'Hello w'
	}, function (ret, err) {
		api.toast({ msg: ret.status });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## clearTextMessageDraft <div id="clearTextMessageDraft"></div>

清除某一会话的文字消息草稿

clearTextMessageDraft({params}, callback(ret, err))

### params

conversationType:

- 类型：字符串
- 默认值：无
- 描述：消息的会话类型，参见 [会话类型](#conversationType)

targetId:

- 类型：字符串
- 默认值：无
- 描述：目标 Id。根据不同的 conversationType，可能是用户 Id、讨论组 Id、群组 Id 或聊天室 Id 等

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：操作结果

内部字段：

``` js
{
	status: 'success' // 状态码：success / error
}
```

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.clearTextMessageDraft({
		conversationType: 'PRIVATE',
		targetId: '9527'
	}, function (ret, err) {
		api.toast({ msg: ret.status });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## createDiscussion <div id="createDiscussion"></div>

创建讨论组

createDiscussion({params}, callback(ret, err))

### params

name:

- 类型：字符串
- 默认值：无
- 描述：讨论组名称，如：当前所有成员的名字的组合。

userIdList:

- 类型：字符串数组
- 默认值：无
- 描述：讨论组成员 Id 列表

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：操作结果

内部字段：

``` js
{
	status: 'success', // 状态码：success / error
	result: {
		discussionId: "1b9f7abe-a5ae-463d-8ff8-d96deaf40b59" // 创建成功的讨论组 Id
	}
}
```

err:

- 类型：JSON 对象

内部字段：

``` js
{
	code: 30003
}
```

状态码说明：

| 状态码    | 说明                 |
| :----- | :----------------- |
| 30003  | 服务器超时              |
| -10000 | 未调用 init 方法进行初始化   |
| -10001 | 未调用 connect 方法进行连接 |
| -10002 | 输入参数错误             |

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.createDiscussion({
		name: 'Ironman, Batman',
		userIdList: ['1234', '4321']
	}, function (ret, err) {
		if (ret.status == 'success')
			api.toast({ msg: ret.result.discussionId });
		else
			api.toast({ msg: err.code });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## getDiscussion <div id="getDiscussion"></div>

获取讨论组信息和设置

getDiscussion({params}, callback(ret, err))

### params

discussionId:

- 类型：字符串
- 默认值：无
- 描述：讨论组 Id

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：操作结果

内部字段：

``` js
{
	status: 'success', // 状态码：success / error
	result: {
        creatorId: '55', // 讨论组创建者 Id
        id: '1b9f7abe-a5ae-463d-8ff8-d96deaf40b59', //讨论组 Id
        name: 'Ironman, Batman', // 讨论组名称
        memberIdList: [ '1234', '4321' ], // 成员 Id 列表
        inviteStatus: 'OPENED' // 是否公开好友邀请：OPENED / CLOSED，参见 讨论组邀请状态
	}
}
```

err:

- 类型：JSON 对象

内部字段：

``` js
{
	code: 30003
}
```

状态码说明：

| 状态码    | 说明                 |
| :----- | :----------------- |
| 30003  | 服务器超时              |
| -10000 | 未调用 init 方法进行初始化   |
| -10001 | 未调用 connect 方法进行连接 |
| -10002 | 输入参数错误             |

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.getDiscussion({
		discussionId: '1b9f7abe-a5ae-463d-8ff8-d96deaf40b59'
	}, function (ret, err) {
		if (ret.status == 'success')
			api.toast({ msg: JSON.stringify(ret.result.discussion) });
		else
			api.toast({ msg: err.code });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## setDiscussionName <div id="setDiscussionName"></div>

设置讨论组名称

setDiscussionName({params}, callback(ret, err))

### params

discussionId:

- 类型：字符串
- 默认值：无
- 描述：讨论组 Id

name:

- 类型：字符串
- 默认值：无
- 描述：讨论组名称

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：操作结果

内部字段：

``` js
{
	status: 'success' // 状态码：success / error
}
```

err:

- 类型：JSON 对象

内部字段：

``` js
{
	code: 30003
}
```

状态码说明：

| 状态码    | 说明                 |
| :----- | :----------------- |
| 30003  | 服务器超时              |
| -10000 | 未调用 init 方法进行初始化   |
| -10001 | 未调用 connect 方法进行连接 |
| -10002 | 输入参数错误             |

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.setDiscussionName({
		discussionId: '1b9f7abe-a5ae-463d-8ff8-d96deaf40b59',
		name: 'Ironman, Hulk'
	}, function (ret, err) {
		if (ret.status == 'success')
			api.toast({ msg: JSON.stringify(ret.status) });
		else
			api.toast({ msg: err.code });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## addMemberToDiscussion <div id="addMemberToDiscussion"></div>

添加一名或者一组用户加入讨论组

addMemberToDiscussion({params}, callback(ret, err))

### params

discussionId:

- 类型：字符串
- 默认值：无
- 描述：讨论组 Id

userIdList:

- 类型：字符串数组
- 默认值：无
- 描述：邀请的用户 Id 列表

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：操作结果

内部字段：

``` js
{
	status: 'success' // 状态码：success / error
}
```

err:

- 类型：JSON 对象

内部字段：

``` js
{
	code: 30003
}
```

状态码说明：

| 状态码    | 说明                 |
| :----- | :----------------- |
| 30003  | 服务器超时              |
| -10000 | 未调用 init 方法进行初始化   |
| -10001 | 未调用 connect 方法进行连接 |
| -10002 | 输入参数错误             |

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.addMemberToDiscussion({
		discussionId: '1b9f7abe-a5ae-463d-8ff8-d96deaf40b59',
		userIdList: ['4567', '7654']
	}, function (ret, err) {
		if (ret.status == 'success')
			api.toast({ msg: JSON.stringify(ret.status) });
		else
			api.toast({ msg: err.code });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## removeMemberFromDiscussion <div id="removeMemberFromDiscussion"></div>

供创建者将某用户移出讨论组

移出自己或者调用者非讨论组创建者将产生 -1 未知错误

removeMemberFromDiscussion({params}, callback(ret, err))

### params

discussionId:

- 类型：字符串
- 默认值：无
- 描述：讨论组 Id

userId:

- 类型：字符串
- 默认值：无
- 描述：用户 Id

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：操作结果

内部字段：

``` js
{
	status: 'success' // 状态码：success / error
}
```

err:

- 类型：JSON 对象

内部字段：

``` js
{
	code: 30003
}
```

状态码说明：

| 状态码    | 说明                 |
| :----- | :----------------- |
| 30003  | 服务器超时              |
| -10000 | 未调用 init 方法进行初始化   |
| -10001 | 未调用 connect 方法进行连接 |
| -10002 | 输入参数错误             |

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.removeMemberFromDiscussion({
		discussionId: '1b9f7abe-a5ae-463d-8ff8-d96deaf40b59',
		userId: '4567'
	}, function (ret, err) {
		if (ret.status == 'success')
			api.toast({ msg: JSON.stringify(ret.status) });
		else
			api.toast({ msg: err.code });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## quitDiscussion <div id="quitDiscussion"></div>

退出当前用户所在的某讨论组

quitDiscussion({params}, callback(ret, err))

### params

discussionId:

- 类型：字符串
- 默认值：无
- 描述：讨论组 Id

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：操作结果

内部字段：

``` js
{
	status: 'success' // 状态码：success / error
}
```

err:

- 类型：JSON 对象

内部字段：

``` js
{
	code: 30003
}
```

状态码说明：

| 状态码    | 说明                 |
| :----- | :----------------- |
| 30003  | 服务器超时              |
| -10000 | 未调用 init 方法进行初始化   |
| -10001 | 未调用 connect 方法进行连接 |
| -10002 | 输入参数错误             |

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.quitDiscussion({
		discussionId: '1b9f7abe-a5ae-463d-8ff8-d96deaf40b59'
	}, function (ret, err) {
		if (ret.status == 'success')
			api.toast({ msg: JSON.stringify(ret.status) });
		else
			api.toast({ msg: err.code });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## setDiscussionInviteStatus <div id="setDiscussionInviteStatus"></div>

设置讨论组成员邀请权限

setDiscussionInviteStatus({params}, callback(ret, err))

### params

discussionId:

- 类型：字符串
- 默认值：无
- 描述：讨论组 Id

inviteStatus:

- 类型：字符串
- 默认值：无
- 描述：邀请状态，默认为开放，参见 [讨论组邀请状态](#discussionInviteStatus)

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：操作结果

内部字段：

``` js
{
	status: 'success' // 状态码：success / error
}
```

err:

- 类型：JSON 对象

内部字段：

``` js
{
	code: 30003
}
```

状态码说明：

| 状态码    | 说明                 |
| :----- | :----------------- |
| 30003  | 服务器超时              |
| -10000 | 未调用 init 方法进行初始化   |
| -10001 | 未调用 connect 方法进行连接 |
| -10002 | 输入参数错误             |

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.setDiscussionInviteStatus({
		discussionId: '1b9f7abe-a5ae-463d-8ff8-d96deaf40b59',
		inviteStatus: 'OPENED'
	}, function (ret, err) {
		if (ret.status == 'success')
			api.toast({ msg: JSON.stringify(ret.status) });
		else
			api.toast({ msg: err.code });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## syncGroup <div id="syncGroup"></div>

同步当前用户所属的群组信息到融云服务器

syncGroup({params}, callback(ret, err))

### params

groups:

- 类型：JSON 对象数组
- 默认值：无
- 描述：讨论组 Id

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：操作结果

内部字段：

``` js
{
	status: 'success' // 状态码：success / error
}
```

err:

- 类型：JSON 对象

内部字段：

``` js
{
	code: 30003
}
```

状态码说明：

| 状态码    | 说明                 |
| :----- | :----------------- |
| 30003  | 服务器超时              |
| -10000 | 未调用 init 方法进行初始化   |
| -10001 | 未调用 connect 方法进行连接 |
| -10002 | 输入参数错误             |

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.syncGroup({
		groups: [
			{
				groupId: '123',
				groupName: 'Ski Club',
				portraitUrl: 'http://club.com/ski.jpg'
			}, {
				groupId: '456',
				groupName: 'Diving Club',
				portraitUrl: 'http://club.com/diving.jpg'
			}
		]
	}, function (ret, err) {
		if (ret.status == 'success')
			api.toast({ msg: JSON.stringify(ret.status) });
		else
			api.toast({ msg: err.code });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## joinGroup <div id="joinGroup"></div>

当前用户加入某群组

joinGroup({params}, callback(ret, err))

### params

groupId:

- 类型：字符串
- 默认值：无
- 描述：群组 Id

groupName:

- 类型：字符串
- 默认值：无
- 描述：群组名称

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：操作结果

内部字段：

``` js
{
	status: 'success' // 状态码：success / error
}
```

err:

- 类型：JSON 对象

内部字段：

``` js
{
	code: 30003
}
```

状态码说明：

| 状态码    | 说明                 |
| :----- | :----------------- |
| 30003  | 服务器超时              |
| -10000 | 未调用 init 方法进行初始化   |
| -10001 | 未调用 connect 方法进行连接 |
| -10002 | 输入参数错误             |

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.joinGroup({
		groupId: '123',
		groupName: 'Ski Club'
	}, function (ret, err) {
		if (ret.status == 'success')
			api.toast({ msg: JSON.stringify(ret.status) });
		else
			api.toast({ msg: err.code });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## quitGroup <div id="quitGroup"></div>

当前用户退出某群组

quitGroup({params}, callback(ret, err))

### params

groupId:

- 类型：字符串
- 默认值：无
- 描述：群组 Id

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：操作结果

内部字段：

``` js
{
	status: 'success' // 状态码：success / error
}
```

err:

- 类型：JSON 对象

内部字段：

``` js
{
	code: 30003
}
```

状态码说明：

| 状态码    | 说明                 |
| :----- | :----------------- |
| 30003  | 服务器超时              |
| -10000 | 未调用 init 方法进行初始化   |
| -10001 | 未调用 connect 方法进行连接 |
| -10002 | 输入参数错误             |

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.quitGroup({
		groupId: '123'
	}, function (ret, err) {
		if (ret.status == 'success')
			api.toast({ msg: JSON.stringify(ret.status) });
		else
			api.toast({ msg: err.code });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## joinChatRoom <div id="joinChatRoom"></div>

当前用户加入某聊天室

joinChatRoom({params}, callback(ret, err))

### params

chatRoomId:

- 类型：字符串
- 默认值：无
- 描述：聊天室 Id

defMessageCount:

- 类型：数字
- 默认值：无
- 描述：进入聊天室拉取消息数目

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：操作结果

内部字段：

``` js
{
	status: 'success' // 状态码：success / error
}
```

err:

- 类型：JSON 对象

内部字段：

``` js
{
	code: 30003
}
```

状态码说明：

| 状态码    | 说明                 |
| :----- | :----------------- |
| 30003  | 服务器超时              |
| -10000 | 未调用 init 方法进行初始化   |
| -10001 | 未调用 connect 方法进行连接 |
| -10002 | 输入参数错误             |

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.joinChatRoom({
		chatRoomId: '123',
		defMessageCount: 20
	}, function (ret, err) {
		if (ret.status == 'success')
			api.toast({ msg: JSON.stringify(ret.status) });
		else
			api.toast({ msg: err.code });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## quitChatRoom <div id="quitChatRoom"></div>

当前用户退出某聊天室

quitChatRoom({params}, callback(ret, err))

### params

chatRoomId:

- 类型：字符串
- 默认值：无
- 描述：聊天室 Id

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：操作结果

内部字段：

``` js
{
	status: 'success' // 状态码：success / error
}
```

err:

- 类型：JSON 对象

内部字段：

``` js
{
	code: 30003
}
```

状态码说明：

| 状态码    | 说明                 |
| :----- | :----------------- |
| 30003  | 服务器超时              |
| -10000 | 未调用 init 方法进行初始化   |
| -10001 | 未调用 connect 方法进行连接 |
| -10002 | 输入参数错误             |

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.quitChatRoom({
		chatRoomId: '123'
	}, function (ret, err) {
		if (ret.status == 'success')
			api.toast({ msg: JSON.stringify(ret.status) });
		else
			api.toast({ msg: err.code });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## getConnectionStatus <div id="getConnectionStatus"></div>

获取连接状态

getConnectionStatus(callback(ret, err))

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：连接状态枚举，参见 [连接状态](#connectionStatus)；

内部字段：

``` js
{
	status: 'success',
	result:
	{
		connectionStatus: 'CONNECTED' // 连接状态
	}
}
```

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.getConnectionStatus(function (ret, err) {
		api.toast({ msg: ret.result.connectionStatus });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 2.0.0 及更高版本

## logout <div id="logout"></div>

注销登录(不再接收 Push 消息)

logout(callback(ret, err))

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：返回的注销登录成功或者失败的状态

内部字段：

``` js
{
	status: 'success' // 状态码：success
}
```

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.logout(function (ret, err) {
		if (ret.status == 'error')
            api.toast({ msg: err.code });
}); // 断开，且不再接收 Push
```

### 可用性

iOS 系统，Android 系统

可提供的 2.0.0 及更高版本

## getRemoteHistoryMessages <div id="getRemoteHistoryMessages"></div>

获取历史消息记录（特别说明：调用此方法需要开启历史消息漫游；当用户因换设备或重装app导致本地本地存储丢失的情况，可用此方法获取记录；此方法返回值中messageId均为0，融云服务器不会保存此值）

getRemoteHistoryMessages({params}, callback(ret, err))

### params

conversationType:

- 类型：字符串
- 默认值：无
- 描述：消息的会话类型，参见 [会话类型](#conversationType)；不支持传入 RCConversationType.CHATROOM。

targetId:

- 类型：字符串
- 默认值：无
- 描述：目标 Id。根据不同的 conversationType，可能是用户 Id、讨论组 Id、群组 Id 或聊天室 Id 等

dateTime :

- 类型：日期
- 默认值：无
- 描述：从该时间点开始获取消息。即：消息中的 sentTime；第一次可传 0，再次取值此参数可传入上一次获取的最后一条记录的sentTime值。

count:

- 类型：数字
- 默认值：无
- 描述：要获取的消息数量（1-20条）

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：最新消息记录，按照时间顺序从新到旧排列。

内部字段：

``` js
{
	status: 'success',
	result: [
		{
			content: {
				text: 'Hello world!',
				extra: ''
			}, // 消息内容
            extra: '', // 消息的附加信息，此信息只保存在本地
			conversationType: 'PRIVATE', // 参见 会话类型 枚举
			messageDirection: 'SEND', // 消息方向：SEND 或者 RECEIVE
			targetId: '55', // 这里对应消息发送者的 userId
			objectName: 'RC:TxtMsg', // 消息类型，参见 http://docs.rongcloud.cn/android_message.html#_内置内容类消息
			sentStatus: 'SENDING', // 发送状态：SENDING, SENT 或 FAILED
			senderUserId: '55', // 发送者 userId
			messageId: 0, // 融云服务器不保存此值，返回值均为0
			sentTime: 1444446587902, // 发送消息的时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数
			receivedTime: 1444446598989 // 收到消息的时间戳，从 1970 年 1 月 1 日 0 点 0 分 0 秒开始到现在的毫秒数
		}
	]
}
```

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.getRemoteHistoryMessages({
		conversationType: 'PRIVATE',
		targetId: '9527',
		dateTime: 1418971531533,
		count: 20
	}, function (ret, err) {
		api.toast({ msg: JSON.stringify(ret.result) });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 2.0.0 及更高版本

## addToBlacklist <div id="addToBlacklist"></div>

将某个用户加到黑名单中

addToBlacklist({params}, callback(ret, err))

### params

userId:

- 类型：字符串
- 默认值：无
- 描述：要加入黑名单的用户 Id

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：操作结果

内部字段：

``` js
{
	status: 'success' // 状态码：success / error
}
```

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.addToBlacklist({
		userId: '688'
	}, function (ret, err) {
		api.toast({ msg: ret.status });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 2.0.0 及更高版本

## removeFromBlacklist <div id="removeFromBlacklist"></div>

将个某用户从黑名单中移出

removeFromBlacklist({params}, callback(ret, err))

### params

userId:

- 类型：字符串
- 默认值：无
- 描述：要移出黑名单的用户 Id

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：操作结果

内部字段：

``` js
{
	status: 'success' // 状态码：success / error
}
```

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.removeFromBlacklist({
		userId: '688'
	}, function (ret, err) {
		api.toast({ msg: ret.status });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 2.0.0 及更高版本

## getBlacklistStatus <div id="getBlacklistStatus"></div>

获取某用户是否在黑名单中

getBlacklistStatus({params}, callback(ret, err))

### params

userId:

- 类型：字符串
- 默认值：无
- 描述：要查询的用户 Id

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：操作结果

内部字段：

``` js
{
	status: 'success', // 状态码：success / error
    result: 1 // 1-不在黑名单；0-在黑名单
}
```

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.getBlacklistStatus({
		userId: '688'
	}, function (ret, err) {
		api.toast({ msg: ret.status });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 2.0.0 及更高版本

## getBlacklist <div id="getBlacklist"></div>

获取当前用户的黑名单列表

getBlacklist(callback(ret, err))

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：操作结果

内部字段：

``` js
{
	status: 'success' ，// 状态码：success / error
    result: ['aaa','bbb']
}
```

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.getBlacklist(function (ret, err) {
		api.toast({ msg: JSON.stringify(ret.result) });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 2.0.0 及更高版本

## setNotificationQuietHours <div id="setNotificationQuietHours"></div>

设置消息通知免打扰时间

setNotificationQuietHours({params}, callback(ret, err))

### params

startTime:

- 类型：字符串
- 默认值：无
- 描述：起始时间 格式 HH:MM:SS

spanMinutes :

- 类型：数字
- 默认值：无
- 描述：间隔分钟数 0 < spanMinutes < 1440。

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：操作结果

内部字段：

``` js
{
	status: 'success' // 状态码：success / error
}
```

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.setNotificationQuietHours({
		startTime: '22:00:00',
		spanMinutes: 6

	}, function (ret, err) {
		api.toast({ msg: ret.status });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 2.0.0 及更高版本

## removeNotificationQuietHours <div id="removeNotificationQuietHours"></div>

移除消息通知免打扰时间

removeNotificationQuietHours(callback(ret, err))

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：操作结果

内部字段：

``` js
{
	status: 'success' // 状态码：success / error
}
```

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.removeNotificationQuietHours( function (ret, err) {
		api.toast({ msg: ret.status });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 2.0.0 及更高版本

## getNotificationQuietHours <div id="getNotificationQuietHours"></div>

获取消息通知免打扰时间

getNotificationQuietHours(callback(ret, err))

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：操作结果

内部字段：

``` js
{
	status: 'success' , // 状态码：success / error
    result: {
        startTime: "22:00:00", // 起始时间
        spanMinutes: 6 // 间隔分钟数
    }
}
```

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.getNotificationQuietHours( function (ret, err) {
		api.toast({ msg:  JSON.stringify(ret.result) });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 2.0.0 及更高版本

## setMessageSentStatus <div id="setMessageSentStatus"></div>

设置消息发送状态

setMessageSentStatus({params}, callback(ret, err))

### params

messageId:

- 类型：数字
- 默认值：无
- 描述：消息 Id

sentStatus :

- 类型：字符串
- 默认值：无
- 描述：发送出的消息的状态枚举，参见 [发送状态](#sentStatus)；

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：操作结果

内部字段：

``` js
{
	status: 'success' // 状态码：success / error
}
```

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.setMessageSentStatus({
		messageId: 8,
		sentStatus: 'READ'
	}, function (ret, err) {
		api.toast({ msg: ret.status });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 2.0.0 及更高版本

## getCurrentUserId <div id="getCurrentUserId"></div>

获取当前连接用户的信息

getCurrentUserId(callback(ret, err))

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：操作结果

内部字段：

``` js
{
	status: 'success', // 状态码：success / error
    result: 'apple' // 当前连接用户
}
```

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.getCurrentUserId( function (ret, err) {
		api.toast({ msg: ret.result });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 2.0.0 及更高版本

## disableLocalNotification <div id="disableLocalNotification"></div>

设置本地消息不提示

disableLocalNotification(callback(ret, err))

### callback(ret, err)

ret:

- 类型：JSON 对象
- 描述：操作结果

内部字段：

``` js
{
	status: 'success' // 状态码：success / error
}
```

### 示例代码

``` js
var rong = api.require('rongCloud2');

// 之前调用 init 和 connect 的代码省略

rong.disableLocalNotification( function (ret, err) {
		api.toast({ msg: ret.status });
})
```

### 可用性

iOS 系统，Android 系统

可提供的 2.0.0 及更高版本

</div>

<div id="const-content">

<div class="outline">

[会话类型](#conversationType)

[会话通知提醒状态](#conversationNotificationStatus)

[讨论组邀请状态](#discussionInviteStatus)

[连接状态](#connectionStatus)

</div>

## 会话类型<div id="conversationType"></div>

区分不同的会话形式，字符串类型

### 取值范围

- PRIVATE			// 单聊
- DISCUSSION		// 讨论组
- GROUP				// 群组
- CHATROOM			// 聊天室
- CUSTOMER_SERVICE	// 客服
- SYSTEM			// 系统

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## 会话通知提醒状态<div id="conversationNotificationStatus"></div>

会话通知提醒的状态，开启或者关闭，字符串类型

### 取值范围

- DO_NOT_DISTURB	// 免打扰
- NOTIFY			// 提醒

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## 讨论组邀请状态<div id="discussionInviteStatus"></div>

讨论组邀请状态，开放或者关闭，字符串类型

### 取值范围

- OPENED	// 开放邀请
- CLOSED	// 关闭邀请

### 可用性

iOS 系统，Android 系统

可提供的 1.1.0 及更高版本

## 连接状态<div id="connectionStatus"></div>

连接状态，字符串类型

### 取值范围

- CONNECTED	// 连接成功
- CONNECTING	// 连接中
- DISCONNECTED	// 断开连接
- KICKED	// 用户账户在其他设备登录，本机会被踢掉线
- NETWORK_UNAVAILABLE	// 网络不可用
- SERVER_INVALID	// 服务器异常或无法连接
- TOKEN_INCORRECT	// Token 不正确

### 可用性

iOS 系统，Android 系统

可提供的 2.0.0 及更高版本

## 发送出的消息状态<div id="sentStatus"></div>

连接状态，字符串类型

### 取值范围

- DESTROYED	// 对方已销毁
- FAILED	// 发送失败
- READ	// 对方已读
- RECEIVED	// 对方已接收
- SENDING	// 发送中
- SENT	// 已发送

### 可用性

iOS 系统，Android 系统

可提供的 2.0.0 及更高版本

## 接收到的消息状态<div id="receivedStatus"></div>

接收到的消息状态，字符串类型

### 取值范围

- UNREAD // 未读
- READ // 已读
- LISTENED // 已收听
- DOWNLOADED // 已下载

### 可用性

iOS 系统，Android 系统

可提供的 2.0.0 及更高版本



</div>
