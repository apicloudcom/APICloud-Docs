/*
Title: pingpp
Description: 封装了多个渠道的支付接口.
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：ping++</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">分享类接口</a></li>
	<li><a href="#const-content">常量</a></li>
</ul>
<div id="method-content">

<div class="outline">
[createPayment](#a1)

[getVersion](#a2)
</div>

#**概述**

pingpp 封装了支付宝（alipay），微信（wx），银联（upacp/upmp），百度钱包（bfb_wap/bfb）四个渠道的支付接口。使用此模块可轻松实现各个渠道的支付功能。<br>
使用之前需要先到 [Ping++](https://pingxx.com) 注册，并根据[技术文档](https://pingxx.com/document)部署 Server SDK。


#**createPayment**<div id="a1"></div>

支付.

createPayment({params}, callback(ret, err))

## params

charge

- 类型：字符串
- 描述：从 Server SDK 获取到的 charge 对象 JSON 序列化字符串

scheme

- 类型：字符串
- 描述：自定义的 iOS URL Schemes，如果不传，会自动获取 URL Types 下的第一个。Android 平台不需要。

## callback(ret, err)

ret

- 类型：JSON 对象.

内部字段：

```
{
    result:"success"    // 可能的取值："success", "fail", "cancel", "invalid"
}
```
iOS 中微信客户端未安装时会返回 `invalid`，Android 中微信客户端或者银联支付插件未安装时会返回 `invalid`

err

- 类型：JSON 对象

内部字段：

```
{
    code:0,    // 错误码
    msg:""     // 错误描述
}
```


错误码：详见[错误码](!Constant)常量

##示例代码

```js

var pingpp = api.require('pingpp');

var params = {
    charge: chargeJSONString,
    scheme: "yourappurlscheme"
};

pingpp.createPayment(params, function(ret, err){
    if (ret.result == "success") {
        api.alert({msg:"success"});
    }
});
```

##补充说明

- 百度钱包渠道字段，iOS 请用 `bfb_wap`，Android 请用 `bfb`
- 银联渠道分两种，2015 年之前申请的为 `upmp`，之后的为 `upacp`

##可用性

Android 系统, iOS 系统

可提供的1.0.0及更高版本


#**getVersion**<div id="a2"></div>

获取版本号

getVersion();

## callback(ret, err)

ret

- 类型：JSON 对象.

内部字段：


```
{
    version:"2.1.1"    // 版本号
}
```

##示例代码

```js
var pingpp = api.require('pingpp');

pingpp.getVersion(function(ret){
    api.alert({msg:ret.version});
});
```

##补充说明

无

##可用性

Android系统  iOS系统

可提供的1.0.0及更高版本



#**setDebugMode**<div id="a2"></div>

设置是否开启 Debug 模式

setDebugMode({enabled:true});

## params

enabled
- 类型：布尔型
- 描述：是否开启 Debug 模式

##示例代码
```
var pingpp = api.require('pingpp');
pingpp.setDebugMode({enabled:true});
```

##补充说明

无

##可用性

iOS系统，Android系统

</div>

<div id="const-content">

<div class="outline">
[错误码](#1)
</div>

#**错误码**<div id="1"></div>

错误码

##取值范围：

- 0 无效的 Charge;
- 1 无效的 Credential;
- 2 无效的渠道;
- 3 微信客户端未安装;
- 4 微信客户端版本不支持 OpenApi;
- 5 取消;
- 6 找不到 ViewController;(仅在 iOS 出现)
- 7 测试模式异步通知失败;
- 8 渠道返回失败;
- 9 网络错误;
- 10 未知错误。