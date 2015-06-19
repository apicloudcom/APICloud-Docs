/*
Title: meChat
Description: meChat
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[initMeChat](#1)

[show](#2)

[specifyAlloc](#3)

[addUserInfo](#4)

[addOtherInfo](#5)
</div>

#**概述**

meChat是一款实现手机用户与企业保持随时随刻沟通的客服工具。本模块封装了美洽的相关接口。使用此模块之前需要先注册美洽获取appkey

![图片说明](/img/docImage/meChat.jpg)

**注册方法如下:**

使用管理员账号登陆[美洽管理后台](https://meiqia.com/login)，在 **账户和设置 --> 入口设置 --> inAPP SDK** 页面中，选择 **添加一个APP** ，在平台项中勾选任意平台，然后添加 APP 即可得到 `appkey` 用于配置。

注意：本模块在ios上支持最低版本为6.0


#**initMeChat**<div id="1"></div>
	
初始化美洽

initMeChat(params)

##params

appkey：

- 类型：字符串
- 默认值：无
- 描述：注册美洽后，从美洽后台获得的appkey，不可为空


##示例代码

```js
var obj = api.require('meChat');
obj.initMeChat({
	appkey:'**************'
});
```

##补充说明

使用此模块，必须先用initMeChat初始化

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**show**<div id="2"></div>

弹出美洽聊天界面

show()

##示例代码

	var obj = api.require('meChat');
	obj.show();

##补充说明

调用该接口之前，一定要先调用initMeChat初始化，否则无法正确启动。show()应该在执行specifyAlloc(),addUserInfo(),addOtherInfo()，之后再执行

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**specifyAlloc**<div id="3"></div>

指定分配客服与客服组

specifyAlloc({params})

##params

agentId：

- 类型：字符串
- 默认值：无
- 描述：在美洽系统中客服对应的ID，与groupId配合为空

groupId：

- 类型：字符串
- 默认值：无
- 描述：在美洽系统中客服组对应的ID，与agentId配合为空

##示例代码

```js
var obj = api.require('meChat');
obj.specifyAlloc({
	groupId: '******',
	agentId:'*******'
});
```

##补充说明

agentId和groupId可只传其中一个，也可同时都传。美洽系统将优先分配指定客服，如果客服不在线，则分配到指定的客服组，如果客服组也无人在线，则分配到全部客服。本接口必须在show之前调用

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**addUserInfo**<div id="4"></div>

添加规范化用户信息

addUserInfo({params})

##params

realName：

- 类型：字符串
- 默认值：无
- 描述：真实姓名，可为空

sex：

- 类型：字符串
- 默认值：无
- 描述：性别，可为空

birthday：

- 类型：字符串
- 默认值：无
- 描述：生日，可为空

age：

- 类型：字符串
- 默认值：无
- 描述：年龄，可为空

job：

- 类型：字符串
- 默认值：无
- 描述：职业，可为空

avatar：

- 类型：字符串
- 默认值：无
- 描述：头像url，可为空

comment：

- 类型：字符串
- 默认值：无
- 描述：备注，可为空

appUserId：

- 类型：字符串
- 默认值：无
- 描述：用户识别符，可为空

appUserName：

- 类型：字符串
- 默认值：无
- 描述：登陆名，可为空

appNickName：

- 类型：字符串
- 默认值：无
- 描述：昵称，可为空

tel：

- 类型：字符串
- 默认值：无
- 描述：电话，可为空

email：

- 类型：字符串
- 默认值：无
- 描述：邮箱，可为空

address：

- 类型：字符串
- 默认值：无
- 描述：地址，可为空

QQ：

- 类型：字符串
- 默认值：无
- 描述：qq号，可为空

weibo：

- 类型：字符串
- 默认值：无
- 描述：新浪微博ID，可为空

weixin：

- 类型：字符串
- 默认值：无
- 描述：微信号，可为空

##示例代码

```JS
var obj = api.require('meChat');
obj.addUserInfo({
	realName:'美洽',
    job:'客服服务',
	tel:'400-0031-322'
	});
```

##补充说明

规范化用户信息将会呗传送到美洽服务端，用于对话时显示给客服人员一作参考。这些参数都是可选的，可以选择其中的一个或者多个传递。此接口必须在show之前执行

可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**addOtherInfo**<div id="5"></div>

添加自定义信息

addOtherInfo({params})

##params

所有参数均为字符串类型，均无默认值，key可自定义

##示例代码

```JS
var obj = api.require('meChat');
obj.addOtherInfo({
	foo:'bar',
	hello:'world',
	你好:'世界'
});
```

##补充说明

自定义信息会被传送到美洽服务器，用于对话时显示给客服人员以作参考。本接口在show之前调用

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
