/*
Title: moduleShareSMS
Description: moduleShareSMS
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>
<div id="method-content">

<div class="outline">
[getVerificationCode](#a1)

[submitVerificationCode](#a2)

[startWizard](#a3)

[submitUserInfo](#a4)

[findFriendInContacts](#a5)

[getNewFriendsCount](#a6)

</div>


#**概述**

moduleShareSMS封装了mob.com平台的免费短信验证码SDK，使用此模块可以实现短信验证功能。本模块最大的特点是每天1万免费额度，基本不用钱了，适合刚起步的应用。使用前需到mob.com注册账号获得api key和secret。计划5月加入IOS。

应一些朋友的要求，我加一些总的文档。首先，至少写这篇文档的时候，使用这个模块一定要！！云编译！！一键调试啥的是没用的，apicloud不会把远程的模块下给你让你本地编译。

如果你是初学者，就想体验一下，请直接调用startWizard方法。没错，我特地为你准备了这个，啥都不用做，就传入key和secret，你就能体验验证功能了，界面见封面截图。不过不建议正式产品用这个。

一般验证码开发流程：1、自己画注册界面；2、有个按钮叫获取验证码，点击调用getVerificationCode；3、当用户填完验证码、用户名、密码点击提交时，先调用submitVerificationCode查看是否验证成功，如果成功继续你的注册流程。以后的版本我会考虑集成更安全的服务器验证方法。

好友邀请开发流程：1、在用户注册成功以后，一定要调用submitUserInfo通知ShareSDK,不然他不会知道你通讯录那些人是注册了你的app的；startWizard方法结束前会自动调用submitUserInfo创建一个随机用户。2、平时你可以没事的时候调用getNewFriendsCount，如果大于0就说明有新朋友，可以通知用户去看看通讯录，当然这步可以跳过；3、核心逻辑，邀请用户或者加通讯录好友，如果你懒的写界面，那直接调用findFriendInContacts；如果你觉得这个界面和你风格不同要自己写，那就调用getFriendsInApp，这个api没有界面，直接返回你通讯录里面所有注册了app的好友。

2015-04-19更新内容：
1.增加好友邀请
2.查找联系人中的朋友

#**getVerificationCode**<div id="a1"></div>

获得验证码

getVerificationCode({params}, callback(ret, err))

##params

phone：

- 类型：字符串
- 默认值：无
- 描述：手机号码，11位数字

key：

- 类型：字符串
- 默认值：无
- 描述：mob.com免费获得的短信SDK的app_key

secret：

- 类型：字符串
- 默认值：无
- 描述：mob.com免费获得的短信SDK的app_secret


##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:  int          //状态值，成功发送验证码为1
	description: String  //当status不为1，此字段为失败原因
}

```

err：

- 类型：JSON对象

内部字段：

```js
{
    //这个，聪明的你一定猜到了，没错，我都发ret里了，err不会有东西的。
}
```

##示例代码

```js
var uzShareSMSModule = api.require('moduleShareSMS');
uzShareSMSModule.getVerificationCode({
	key:"your_app_key",
	secret:"your_app_secret",
	phone: "13912345678"
}, function(ret, err){
	if(ret.status == 1){
		alert("ok!");
	} else {
		alert(ret.description)
	}
});
```

##可用性

Android系统

可提供的1.0.0及更高版本




#**submitVerificationCode**<div id="a2"></div>

获得验证码

submitVerificationCode({params}, callback(ret, err))

##params

phone：

- 类型：字符串
- 默认值：无
- 描述：手机号码，11位数字

code：

- 类型：字符串
- 默认值：无
- 描述：用户输入的验证码


key：

- 类型：字符串
- 默认值：无
- 描述：mob.com免费获得的短信SDK的app_key

secret：

- 类型：字符串
- 默认值：无
- 描述：mob.com免费获得的短信SDK的app_secret


##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:  int          //状态值，成功发送验证码为1
	description: String  //当status不为1，此字段为失败原因
}

```

err：

- 类型：JSON对象

内部字段：

```js
{
    //这个，聪明的你一定猜到了，没错，我都发ret里了，err不会有东西的。
}
```

##示例代码

```js
var uzShareSMSModule = api.require('moduleShareSMS');
uzShareSMSModule.submitVerificationCode({
	key:"your_app_key",
	secret:"your_app_secret",
	phone: "13912345678",
	code: "1234"
}, function(ret, err){
	if(ret.status == 1){
		alert("注册成功");
	} else {
		alert(ret.description);
	}
});
```

##可用性

Android系统

可提供的1.0.0及更高版本





#**startWizard**<div id="a3"></div>

开启手机验证向导

startWizard({params}, callback(ret, err))

##params

key：

- 类型：字符串
- 默认值：无
- 描述：mob.com免费获得的短信SDK的app_key

secret：

- 类型：字符串
- 默认值：无
- 描述：mob.com免费获得的短信SDK的app_secret


##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:  int          //状态值，成功发送验证码为1
	description: String  //当status不为1，此字段为失败原因
}

```

err：

- 类型：JSON对象

内部字段：

```js
{
    //这个，聪明的你一定猜到了，没错，我都发ret里了，err不会有东西的。
}
```

##示例代码

```js
var uzShareSMSModule = api.require('moduleShareSMS');
uzShareSMSModule.startWizard({
   key:"your_app_key",
   secret:"your_app_secret",
}, function(ret, err){
	alert(JSON.stringify(ret));
	if(err)
		alert(JSON.stringify(err));
});
```

##可用性

Android系统

可提供的1.0.0及更高版本





#**submitUserInfo**<div id="a4"></div>

提交用户信息，用于之后匹配手机通讯录功能

submitUserInfo({params}, callback(ret, err))

##params

phone：

- 类型：字符串
- 默认值：无
- 描述：手机号码，11位数字

nickname：

- 类型：字符串
- 默认值：无
- 描述：用户昵称


key：

- 类型：字符串
- 默认值：无
- 描述：mob.com免费获得的短信SDK的app_key

secret：

- 类型：字符串
- 默认值：无
- 描述：mob.com免费获得的短信SDK的app_secret


##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:  int          //状态值，成功发送验证码为1
	description: String  //当status不为1，此字段为失败原因
}

```

err：

- 类型：JSON对象

内部字段：

```js
{
    //这个，聪明的你一定猜到了，没错，我都发ret里了，err不会有东西的。
}
```

##示例代码

```js
var uzShareSMSModule = api.require('moduleShareSMS');
uzShareSMSModule.submitUserInfo({
	key:"your_app_key",
	secret:"your_app_secret",
	phone: "13912345678",
	nickname: "nickname"
}, function(ret, err){
	alert(JSON.stringify(ret));
	if(err)
		alert(JSON.stringify(err));
});
```

##可用性

Android系统

可提供的1.0.0及更高版本




#**findFriendInContacts**<div id="a5"></div>

查找通讯录中的已注册朋友或者邀请未注册朋友（有界面），回调函数比较特殊，每次用户查看通讯录中的已注册朋友，点击该朋友右侧“添加”按钮的时候被调用，可能会被调用多次。

findFriendInContacts({params}, callback(ret, err))

##params

key：

- 类型：字符串
- 默认值：无
- 描述：mob.com免费获得的短信SDK的app_key

secret：

- 类型：字符串
- 默认值：无
- 描述：mob.com免费获得的短信SDK的app_secret

invite_message：

- 类型：字符串
- 默认值：无
- 描述：邀请用户时发送的短信内容

friends：

- 类型：JSONArray
- 默认值：无
- 描述：用户目前的好友列表（手机号），可以不传，传了的话如果对方已经是你好友了，那他旁边的按钮就会变成灰的“已添加”，不然是“添加”。


##callback(ret, err)

注意：开发者负责处理该回调函数传入的用户，向该用户发送当前用户的好友请求。可能会被调用多次。好友关系啥的需要开发者自己维护。

ret：

- 类型：JSON对象

内部字段：

```js
{
	phone:  String          //手机号
	nickname: String  //昵称
	displayname: String  //通讯录名字
}

```

err：

- 类型：JSON对象

内部字段：

```js
{
    //这个，聪明的你一定猜到了，没错，我都发ret里了，err不会有东西的。
}
```

##示例代码

```js
var uzShareSMSModule = api.require('moduleShareSMS');
uzShareSMSModule.findFriendInContacts({
	key:"your_app_key",
	secret:"your_app_secret",
	invite_message: "快来使用XXXX吧，网址是XXXXX！",
	friends: ["13912345678", "13912345679"],
}, function(ret, err){
	alert("" + (new Date()) + JSON.stringify(ret));
});
```

##可用性

Android系统

可提供的1.0.0及更高版本





#**getFriendsInApp**<div id="a1"></div>

返回通讯录中的朋友列表（无界面）

getFriendsInApp({params}, callback(ret, err))

##params

key：

- 类型：字符串
- 默认值：无
- 描述：mob.com免费获得的短信SDK的app_key

secret：

- 类型：字符串
- 默认值：无
- 描述：mob.com免费获得的短信SDK的app_secret


##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:  int          //状态值，成功发送验证码为1
	data: JsonArray  //通讯录中的注册用户列表
}

```

err：

- 类型：JSON对象

内部字段：

```js
{
    //这个，聪明的你一定猜到了，没错，我都发ret里了，err不会有东西的。
}
```

##示例代码

```js
var uzShareSMSModule = api.require('moduleShareSMS');
uzShareSMSModule.getFriendsInApp({
   key:"your_app_key",
	secret:"your_app_secret",
}, function(ret, err){
	alert(JSON.stringify(ret));
	if(err)
		alert(JSON.stringify(err));
});
```

##可用性

Android系统

可提供的1.0.0及更高版本





#**getNewFriendsCount**<div id="a6"></div>

返回通讯录中的新增的注册用户数

getNewFriendsCount({params}, callback(ret, err))

##params

key：

- 类型：字符串
- 默认值：无
- 描述：mob.com免费获得的短信SDK的app_key

secret：

- 类型：字符串
- 默认值：无
- 描述：mob.com免费获得的短信SDK的app_secret


##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:  int          //状态值，成功发送验证码为1
	number: int  //通讯录中的新增注册用户数
}

```

err：

- 类型：JSON对象

内部字段：

```js
{
    //这个，聪明的你一定猜到了，没错，我都发ret里了，err不会有东西的。
}
```

##示例代码

```js
var uzShareSMSModule = api.require('moduleShareSMS');
uzShareSMSModule.getNewFriendsCount({
	key:"your_app_key",
	secret:"your_app_secret",
}, function(ret, err){
	alert(JSON.stringify(ret));
	if(err)
		alert(JSON.stringify(err));
});
```

##可用性

Android系统

可提供的1.0.0及更高版本





