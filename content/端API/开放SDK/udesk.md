/*
Title: udesk
Description: udesk
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：udesk</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">方法</a></li>
</ul>
<div id="method-content">

<div class="outline">
[initUdesk](#a1)

[showFAQs](#a2)

[showConversation](#a3)

[showFAQSection](#a4)

[addUserInfo](#a5)

[component](#a6)
</div>

#**概述**

udesk是一款实现手机用户与企业客服保持实时沟通的在线工具。本模块封装了udesk的相关接口，使用此模块需先注册udesk来获取key和domain。

注册udesk:
登入udesk官网注册udesk账号，进入管理员页面，在管理中心－单点登录中获取共享的秘钥，domain为你注册的域名，例如：udesk.udesk.cn。


#**initUdesk**<div id="a1"></div>
初始化udesk

initUdesk({param})

##params

key：

- 类型：字符串
- 默认值：无
- 描述：注册udesk后，从udesk后台获得的key，不可为空

domain：

- 类型：字符串
- 默认值：无
- 描述：udesk域名，注册后获取，不能为空


##示例代码

```js
var param = {
    key:'************',
    domain:'***.udesk.cn'
};

var udesk = api.require('udesk');
udesk.initUdesk(param);
```

## 补充说明

使用此模块，必须先用initUdesk初始化

## 可用性

iOS系统  Android系统(4.0及以上)

可提供的1.0.0及更高版本



#**showFAQs**<div id="a2"></div>

弹出udesk功能集合页面(帮助中心，联系我们)

showFAQs()

##示例代码

```js
var udesk = api.require('udesk');
udesk.showFAQs();
```

##补充说明

使用此模块，必须先用initUdesk初始化，否则会发生意想不到的事。如果你想调用addUserInfo()、component()接口，则该接口因在这些接口之后执行。

##可用性

iOS系统  Android系统(4.0及以上)

可提供的1.0.0及更高版本



#**showConversation**<div id="a3"></div>

弹出udesk联系我们页面

showConversation()

##示例代码

```js
var udesk = api.require('udesk');
udesk.showConversation();
```

##补充说明

使用此模块，必须先用initUdesk初始化，否则会发生意想不到的事。如果你想调用addUserInfo()、component()接口，则该接口因在这些接口之后执行。

##可用性

iOS系统  Android系统(4.0及以上)

可提供的1.0.0及更高版本


 
#**showFAQSection**<div id="a4"></div>

弹出udesk帮助中心页面

showFAQSection()

##示例代码

```js
var udesk = api.require('udesk');
udesk.showFAQSection();
```

##补充说明

使用此模块，必须先用initUdesk初始化，否则会发生意想不到的事。如果你想调用addUserInfo()、component()接口，则该接口因在这些接口之后执行。

##可用性

iOS系统 Android系统(4.0及以上)

可提供的1.0.0及更高版本



#**addUserInfo**<div id="a5"></div>

添加用户相关信息

addUserInfo({param})

##params

user_id：

- 类型：字符串
- 默认值：udesk－sdk自动生成user_id
- 描述：用户唯一标示，不可重复，如果没有填写则udesk-sdk自动生成

user_info：

- 类型：字典
- 默认值：无
- 描述：用户信息字典

nick_name：

- 类型：字符串
- 默认值：无
- 描述：用户昵称

cellphone：

- 类型：字符串
- 默认值：无
- 描述：用户手机

weixin_id：

- 类型：字符串
- 默认值：无
- 描述：用户手机

weibo_name：

- 类型：字符串
- 默认值：无
- 描述：用户微博

qq：

- 类型：字符串
- 默认值：无
- 描述：用户qq

email：

- 类型：字符串
- 默认值：无
- 描述：用户email，不可重复。

description：

- 类型：字符串
- 默认值：无
- 描述：用户描述。


##示例代码

```js
var param = {

    uesr_id : 'TestID',

    user_info : {
        nick_name: 'sixer',
        cellphone: '00113233',
        weixin_id: 'six123',
        weibo_name: 'xuch5577',
        qq: '5739798666',
        email: 'xu23@163.com',
        description: '测试描述'

    }
};

var udesk = api.require('udesk');
udesk.addUserInfo(param);
```


##补充说明

Android系统暂不支持

使用此模块会讲用户信息传入udesk web端，用于客服查看工单时供客服参考，此接口必须在showFAQs(),showConversation(),showFAQSection()之前之前执行。

##可用性

iOS系统 

可提供的1.0.0及更高版本



#**component**<div id="a6"></div>

拼接udesk组件

setShowPictureFunction({param})

##params

Picture：

- 类型：布尔类型
- 默认值：false
- 描述：请输入true或false,用户组织udesk 发送图片组建和表情组建。

emoji：

- 类型：字符串
- 默认值：false
- 描述：请输入true或false,用户组织udesk 发送图片组建和表情组建。



##示例代码

```js
var param = {
	Picture: 'true',
	emoji: 'true'
};

var udesk = api.require('udesk');
udesk.setShowPictureFunction(param);
```

##补充说明
Android系统暂不支持

使用此模块，接口必须在showFAQs(),showConversation(),showFAQSection()之前之前执行,如果不使用此功能则Udesk IM不支持发送图片和表情。

##可用性

iOS系统

可提供的1.0.0及更高版本