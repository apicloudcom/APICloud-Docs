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

</div>

#**概述**

moduleShareSMS封装了mob.com平台的免费短信验证码SDK，使用此模块可以实现短信验证功能。本模块最大的特点是每天1万免费额度，基本不用钱了，适合刚起步的应用。使用前需到mob.com注册账号获得api key和secret。我象征性收点小费，毕竟安装android studio、在APICloud下调试，还是很麻烦的……一顿早饭钱，我想应该不过分吧！以后有空我会再加入IOS的。

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
        alert(ret.description);
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