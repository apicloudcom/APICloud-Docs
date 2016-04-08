/*
Title: cellPhone
Description: cellPhone
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">
<div class="outline">
[getPhoneNumber](#a1)
[getSMS](#a2)
</div>

#**概述**

cellPhone用来获取用户当前手机的手机号，以及解析短信验证码，主要是用来进行注册用的，并获取当前手机的智能设备唯一编号、获得SIM卡的序号 、国际移动用户识别码


#**getPhoneNumber**<div id="a1"></div>

获取手机信息

getPhoneNumber(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	telephone_DEVICEID:“***********”，      //获取智能设备唯一编号
	telephone_NUM:“***********”，           //获取本机号码
	telephone_IMEI:“***********”，          //获得SIM卡的序号 
	telephone_IMSI:“***********”，          //国际移动用户识别码
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    telephone_DEVICEID:“***********”，          
	telephone_NUM:“+0000000000000”，        //如果获取失败则手机号为0
	telephone_IMEI:“***********”，           
	telephone_IMSI:“***********”，           
}
```

##示例代码

```js
var uzmoduledemo = api.require('cellPhone');
var resultCallback = function(ret, err) {
	alert(JSON.stringify(ret));
}
uzmoduledemo.getPhoneNumber(resultCallback);
```

##补充说明

注意如果用户没有给予权限的情况下获取到的手机号都是0

##可用性

Android系统

可提供的1.0.0及更高版本


#**getSMS**<div id="a2"></div>

获取短信验证码
用户在使用此功能的时候在云编译的时候需要对软件添加读取短信的权限

getSMS({params}, callback(ret, err))

##params

regular

- 类型：字符串
- 默认值：无
- 描述：用来控制获取的短信验证码是多少位数，不能为空

ToObtainNum：

- 类型：字符串
- 默认值：无
- 描述：如果用户知道发送的手机号码，可以选择性获取短信内容，可为空


##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	SMS_CODE:"123456"		//获取成功之后返回的验证码字符串
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    SMS_CODE:'none'     //获取短信失败后返回none
}
```

##示例代码

```js
var uzmoduledemo = api.require('cellPhone');
var param = {
	regular : "\\d{6}",
	ToObtainNum : "+8612345678900"
};
var resultCallback = function(ret, err) {
	alert(JSON.stringify(ret));
}
uzmoduledemo.getSMS(param, resultCallback);

```

##补充说明

获取短信验证码的时候，当验证码为6位则regular : "\\d{6}"依次类推

##可用性

Android系统

可提供的1.0.0及更高版本
