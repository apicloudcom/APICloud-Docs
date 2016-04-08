/*
Title: smsVerify
Description: Mob免费短信验证模块，同时支持短信验证与语音验证。
*/
<div class="outline">
[register](#a1)

[sms](#a2)

[voice](#a3)

[verify](#a4)
</div>

#**概述**

smsVerify 模块封装了 [Mob](http://sms.mob.com/#/sms)2.0 版本的短信验证与语音验证功能。所有短信费用由Mob为您承担，支持212个国家、1000多个运营商。详细使用方法 [请看此帖](http://community.apicloud.com/bbs/forum.php?mod=viewthread&tid=22318)

**使用此模块之前必须先配置 config.xml 文件，配置方法如下：**
- 名称：smsVerify
- 参数：android_app_key、android_app_secret、ios_app_key、ios_app_secret
- 备注：同一个 App 需要同时支持 iOS 和 Android 平台，必须在Mob短信验证码平台分别创建 iOS 和 Android 的两个应用，并同时配置在 config.xml 文件中；若要移除本模块，需要先删除 config.xml 中的配置项，提交代码到云端后方可在控制台的模块栏目移除。
- 配置示例:
```
  <feature name="smsVerify">
    <param name="android_app_key" value="e2ffa3hse299"/>
    <param name="android_app_secret" value="7a0ejgd7df95607464eaaec5c0f9b2b9"/>
    <param name="ios_app_key" value="e2fhsc7fbw00"/>
    <param name="ios_app_secret" value="db5abtd9931e3211932dde17c94c30ae"/>
  </feature>
```
    
**其他问题和说明**
 1. [短信验证码自定义签名注意事项](http://bbs.mob.com/thread-16106-1-1.html)；
 2. iOS版模块SDK含有IDFA，所以关于使用本模块后iOS应用上架审核问题请看 [此链接第二点](http://wiki.mob.com/idfa%E7%9A%84%E6%A3%80%E6%B5%8B%E5%92%8C%E9%80%9A%E8%BF%87%E5%AE%A1%E6%A0%B8/) 的说明；
 3. [如何在mob创建应用](http://bbs.mob.com/forum.php?mod=viewthread&tid=8212)；
 4. 模块大部分错误码由SDK自动返回，但不知道 Mob 出于什么原因，部分错误对应的错误码和描述信息在 iOS 和 Android 上会有所不同。比如发短信验证码时，如果手机号为空，iOS 上返回的是```服务器错误码456```，而 Android 上返回的是```本地错误码603```，虽然俩者都代表手机号错误，但在项目开发时如果某些地方用到了错误码还请自行注意；
 5. 模块使用的是 Mob2.0 以上的SDK开发，1.0 时代申请的 AppKey 是无法在本模块上使用的，若要使用请到 Mob 官网重新申请；
 6. 验证码有效时间为 ```5分钟```；
 7. 费用：测试期间同一 AppKey 短信条数限制为 ```20条/天```，APP开发完成后务必提交开发包到 Mob 后台审核，```审核通过后完全免费```。（国内外短信、语音短信、自定义签名短信全部免费，不收取任何短信费用）；
 8. 运营商限制：```同一个手机号12小时内只能收到5条文本验证码，语音验证码24小时内只能收到10个```。开发中或已审核通过的应用皆受此限制；
 9. Android 智能验证是默认开启的，手机号如果通过智能验证，则不会下发短信验证码，可以在 Mob 后台关闭；


<div id="a1"></div>
#**register**

注册应用

register(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true      //布尔型；true||false，注册是否成功
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
    code: 1,     //数字类型；
                //错误码：
                //1（注册失败）
    msg: "注册失败，请配置 config.xml 文件"        //字符串类型；错误信息
}
```

##示例代码

```js
var smsVerify = api.require('smsVerify');
smsVerify.register(function(ret, err){
	if(ret.status){
		//api.alert({msg: '注册成功'});
	}else{
		api.alert({msg: err.code+' 注册失败'});
	}
});
```
##补充说明

进行后续各种方法操作前务必要先调用此方法！（在当前页面初始化时调用一次就够了）

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="a2"></div>
#**sms**

发送短信验证码

sms({params}, callback(ret, err))

##params

phone：

- 类型：字符串
- 描述：需要验证的手机号码
- 默认值：无

country：

- 类型：字符串
- 描述：（可选项）国际区号。前面不要有 + 号
- 默认值：86

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true,      //布尔型；true||false，操作是否成功
	smart: false      //布尔型；true||false，是否通过智能验证 (iOS系统不支持，所以iOS上永远返回false)
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
    code: 456,   //错误码；
	msg: "手机号码为空"       //字符串类型；错误信息
}
```

##示例代码

```js
var smsVerify = api.require('smsVerify');
smsVerify.sms({
	phone:"18111801118",
	country:"86"
},function(ret, err){
	if(ret.status){
		if( ret.smart == true ){	// 安卓版特有功能 智能验证
			api.alert({msg: '智能验证成功：开发者可以在这里直接执行手机号验证成功之后的相关操作'});
		}else{
			api.alert({msg: '短信发送成功'});
		}
	}else{
		api.alert({msg: err.code+' '+err.msg});
	}
});
```
##补充说明
- Mob短信后台开启智能验证后，若该设备待验证手机号码、手机设备唯一ID和SIM卡序列号，与上一次该设备短信验证通过的手机号码、手机设备唯一ID和SIM卡序列号完全一致。则无需进行短信验证，直接智能验证通过。（仅针对Android设备）
- [错误码参考](http://wiki.mob.com/android-api-%E9%94%99%E8%AF%AF%E7%A0%81%E5%8F%82%E8%80%83/)

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="a3"></div>
#**voice**

发送语音验证码

voice({params}, callback(ret, err))

##params

phone：

- 类型：字符串
- 描述：需要验证的手机号码
- 默认值：无

country：

- 类型：字符串
- 描述：（可选项）国际区号。前面不要有 + 号
- 默认值：86

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true      //布尔型；true||false，操作是否成功
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
    code: 456,   //错误码；
	msg: "手机号码为空"       //字符串类型；错误信息
}
```

##示例代码

```js
var smsVerify = api.require('smsVerify');
smsVerify.voice({
	phone:"18111801118",
	country:"86"
},function(ret, err){
	if(ret.status){
		api.alert({msg: '语音发送成功'});
	}else{
		api.alert({msg: err.code+' '+err.msg});
	}
});
```
##补充说明
[错误码参考](http://wiki.mob.com/android-api-%E9%94%99%E8%AF%AF%E7%A0%81%E5%8F%82%E8%80%83/)

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="a4"></div>
#**verify**

校验验证码

verify({params}, callback(ret, err))

##params

phone：

- 类型：字符串
- 描述：需要验证的手机号码
- 默认值：无

code：

- 类型：字符串
- 描述：收到的验证码
- 默认值：无

country：

- 类型：字符串
- 描述：（可选项）国际区号。前面不要有 + 号
- 默认值：86

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true      //布尔型；true||false，操作是否成功
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
    code: 456,   //错误码；
	msg: "手机号码为空"       //字符串类型；错误信息
}
```

##示例代码

```js
var smsVerify = api.require('smsVerify');
smsVerify.verify({
	phone:"18111801118",
	country:"86",
	code:"1234"
},function(ret, err){
	if(ret.status){
		api.alert({msg: '验证成功'});
	}else{
		api.alert({msg: err.code+' '+err.msg});
	}
});
```
##补充说明
[错误码参考](http://wiki.mob.com/android-api-%E9%94%99%E8%AF%AF%E7%A0%81%E5%8F%82%E8%80%83/)

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本