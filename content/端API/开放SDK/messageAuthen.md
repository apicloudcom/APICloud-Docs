/*
Title: messageAuthen
Description: messageAuthen
*/
<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">方法</a></li>
</ul>
<div id="method-content">

<div class="outline">

[register](#register)
[send](#send)
[enter](#enter)

</div>

# 概述 #

本模块是一款实现手机短信验证的模块。本模块封装了短信验证的相关接口。使用此模块之前需要先去[http://mob.com/sms](http://mob.com/sms)注册获取appkey和appsecret


## register(params)<div id="register"></div>
注册

register (params)

## params ##
appkey：

- 类型：字符串
- 默认值：“”
- 描述：从官方网站获取唯一标志

appsecret：

- 类型：字符串
- 默认值：“”
- 描述：从官方网站获取唯一标志

### 示例代码 ###

```js
var messageAuthen = api.require('messageAuthen');
var param = {appkey:" ",appsecret:" "}; 
    
messageAuthen.register(param);
```

### 可用性 ###

Android 系统

可提供的 1.0.0 及更高版本


## send<div id="send"></div>
发送验证码

send(params, callback)

## params ##
phone：

- 类型：字符串
- 默认值：无
- 描述：填写自己的手机号码

## callback(ret, err)
ret：

- 类型：JSON对象
- 内部字段：

```
	{
		result==“ok”:  //操作是否成功
    }
    
```

### 示例代码

```js
var messageAuthen = api.require('messageAuthen');
var param = {phone:" "};
messageAuthen.send(param,function(ret,err){
    	if(ret.result == "ok"){
       		alert("短信发送成功");
       	}
});
```	

### 可用性 ###

Android系统

可提供的1.0.0及更高版本


## enter<div id="enter"></div>
输入验证码

enter (params, callback)

## params ##
code：

- 类型：字符串
- 默认值：“”
- 描述：短信平台发送的验证码

## callback(ret, err) ##
ret：

- 类型：JSON对象
- 内部字段：

```
	{
		result==“ok”:  //操作是否成功
    }
    
```

### 示例代码 ###

```js
var messageAuthen = api.require('messageAuthen');
var param={code:"123456"};

messageAuthen.enter(param,function(ret,err){
if(ret.result == "ok"){
  		alert("验证成功");
  	}
});
```

### 可用性 ###

Android系统

可提供的 1.0.0 及更高版本