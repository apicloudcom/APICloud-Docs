/*
Title: ciaYi
Description: ciaYi
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>

<div id="method-content">
</div>

<div class="outline">
[initCIASDK](#a1)
[VerPhoneNum](#a2)
[VerCode](#a3)
[cancleCIASDK](#a4)
</div>

#**概述**

ciaYi封装了CIA身份验证的SDK，使用此模块可轻松替代短信验证码，永久免费，一键认证，99%送达，不被拦截。


使用此模块之前必须先配置 config 文件,配置方法如下:

名称:CIASDK
参数:appId   authKey
备注:用户可以在CIA官网 http://www.ciaapp.cn 中通过项目的两个平台的包名来获取APPID和授权码,并同时配置在 config 文件中

配置示例:
  <feature name="CIASDK"> 
    <param name="appId" value="a031e97d464846ca873a86cb55d5d3dc"/>  
    <param name="authKey" value="b15e5591ea1f42f99cd68b64ec0658d8"/> 
  </feature>
字段描述:

appId:官网申请的APPID

authKey:官网申请的授权码


#**initCIASDK**<div id="a1"></div>

初始化SDK

initCIASDK()

##示例代码

```js
{
	var ciasdk = api.require('ciaYi');
	ciasdk.initCIASDK();
}
```

##补充说明

初始化SDK，建议初始化在apiready中调用，避免调用完立刻使用验证。

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**VerPhoneNum**<div id="a2"></div>

向需要验证的手机号拨打电话。

VerPhoneNum({params}, callback(ret, err))

##params

phonenum:

- 类型：字符串
- 描述：需要验证的手机号 

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	state:101		//数字类型；操作成功状态值，取值范围如下：
	             //100（为手机号验证成功，不需要再次输入验证码，主要针对android手机）
	             //101 (电话已拨打等待验证）
	             //110（请求失败）
	             //111（请求异常）
	             //404（未知错误）
}
```

##示例代码

```js
{
	var param = {
		phonenum : "13642155555"
	};
	var ciasdk = api.require('ciaYi');
	ciasdk.VerPhoneNum(param, function(ret){
		alert(JSON.stringify(ret));
	});
}
```

##补充说明

android手机支持一键验证不需要输入验证码，ios手机不支持此功能。
未知错误包括网路不好等情况。
当开始验证手机号的时候，建议给用户一个提示-------"验证码已发送到您输入的手机号码上，隐藏在手机未接来电010-********的后四位，请查询并输入验证码。"


##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本



#**VerCode**<div id="a3"></div>

验证用户输入的验证码

VerCode({params}, callback(ret, err))

##params

phonecode:

- 类型：字符串
- 描述：获取到的用户输入的验证码 

##callback(ret)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	state:100		//数字类型；操作成功状态值，取值范围如下；
	             //100（验证码输入正确）
	             //102（验证码输入错误）
	             //103（验证码过期）
	             //104（验证码输入错误超过上限）
	             //404（未知错误）
}
```


##示例代码

```js
{
	var codea = "1234";
	var param = {
		phonecode : codea
	};
	var ciasdk = api.require('ciaYi');
	ciasdk.VerCode(param, function(ret){
		alert(JSON.stringify(ret));
	});
}
```

##补充说明

获取用户输入的验证码，并进行验证。验证码默认时效60秒，默认输入错误次数3次，超过3次则提示错误超过上限。
未知错误包括网路不好等情况。

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**cancleCIASDK**<div id="a4"></div>

结束验证

cancleCIASDK()

##示例代码

```js
{
	var ciasdk = api.require('ciaYi');
   ciasdk.cancleCIASDK();
}
```

##补充说明

当验证成功之后，请注意要注销sdk。

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本