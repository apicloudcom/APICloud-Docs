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

[setScheduledAgentOrAgentGroup](#3)

[addUserInfo](#4)

[addOtherInfo](#5)
</div>

#**概述**

美洽是一款实现手机用户与企业保持随时随刻沟通的客服工具。本模块封装了美洽的相关接口。使用此模块之前需要先注册美洽获取appkey

![图片说明](https://s3.cn-north-1.amazonaws.com.cn/pics.meiqia.bucket/4f2e9f86df2fd5f8)

**注册方法如下:**

使用**管理员权限**账号登陆[美洽](https://app.meiqia.com/login)，在 **设置 --> SDK** 页面中，选择 **添加 App 配置** ，根据提示配置App信息，然后添加 APP 即可得到 `appkey` 用于配置。

注意：本模块在ios上支持最低版本为6.0


#**initMeiQia**<div id="1"></div>
	
初始化美洽

initMeiQia(params, callback)

##params

appkey：
- 类型：字符串
- 默认值：无
- 描述：注册美洽后，从美洽后台获得的appkey，不可为空

callback:
- 类型：方法
- 默认值：无
- 描述：初始化成功将返回顾客ID（ClientId），初始化失败将返回错误描述

##示例代码

```js
//创建美洽
var mq = api.require('meiQia');

//配置初始化美洽需要的appkey
var param = {
    appkey:"33c19c19bd858746b878fcc93166f2e5"
};
        
//初始化美洽
mq.initMeiQia(param, function (ret, err){
    if (ret) {
	    //初始化成功
        alert(JSON.stringify(ret));
    }else{
	    //初始化失败
        alert(JSON.stringify(err));
    }
})
```

##补充说明

必须在初始化后才能正常使用此模块的其他方法，所以建议将初始化放在App启动时执行。美洽模块只需要初始化一次。

##可用性

iOS系统，Android系统

可提供的3.0.0及更高版本


#**show**<div id="2"></div>

弹出美洽聊天界面

show()

##示例代码
```js
	var mq = api.require('meiQia');
	mq.show();
```

##补充说明


##可用性

iOS系统，Android系统

可提供的3.0.0及更高版本


#**setScheduledAgentOrAgentGroup**<div id="3"></div>

指定分配客服与客服组

setScheduledAgentOrAgentGroup(params)

##params

agentId：

- 类型：字符串
- 默认值：无
- 描述：在美洽系统中客服对应的ID

agentGroup：

- 类型：字符串
- 默认值：无
- 描述：在美洽系统中客服组对应的ID

scheduleRule:

 - 类型：字符串 
 - 默认值：enterprise 
 - 描述：
	 - none：不转接给任何人
	 - group: 转接给组内的人
	 - enterprise: 转接给企业其他随机一个人

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
