/*
Title: moduleSMS
Description: moduleSMS
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[getSmsNumber](#a1)

[getSms](#a2)
</div>

#**概述**

封装了封装了短信监听内容，可截取手机刚接收到的短信内容和获取本机号码（部分手机和电信服务商的号码无法获取）。
使用此模块之前需先配置config文件的permission，方法如下：
	配置示例：
	
```js
<permission name="sms"/>	
```


#**getSmsNumber**<div id="a1"></div>

获取本机手机号码

getSmsNumber(callback(ret, err))


##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	number:185*********           //获取到的手机号码内容
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	code:0,	  //错误码
	msg:””    //错误描述
}
```
##示例代码

```js
var sms = api.require('moduleSMS');
			var resultCallback = function(ret, err) {
				document.getElementById("tel").value = ret.number;
			};
			sms.getSmsNumber(resultCallback);

```

##补充说明

获取本机号码，没有获取到则返回空值

##可用性

Android系统
可提供的1.0.0及更高版本



#**getSms**<div id="a2"></div>

监听短信

getSms(callback(ret, err))

##callback(ret, err)

ret：
- 类型：JSON对象
内部字段：

```js
{
	message:*******		//截取收集新接收到的短信全部内容
}
```

err：
- 类型：JSON对象
内部字段：

```js
{
    code:0,		//错误码（详见错误码常量）
	 msg:””		//错误描述
}
```

##示例代码

```js
var resultCallback = function(ret, err) {
								var msg = ret.message.match(/\d{6}/g);
								document.getElementById("yzcode").value = msg;
							};
							sms.getSms(resultCallback);

```

##补充说明

每触发一次监听，只获取一条短信内容，获取到短信内容后，监听自动关闭，如果需要继续监听，则需要再次调用该方法。

##可用性

Android系统

可提供的1.0.0及更高版本
