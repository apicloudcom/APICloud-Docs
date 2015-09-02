/*
Title: ipaynow
Description: ipaynow
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">方法</a></li>
</ul>
<div id="method-content">-

<div class="outline">

[generatePresignMessage](#a1)

[doSignature](#a2)

[pay](#a3)

</div>

#**概述**

ipaynow(现在支付)封装了支付宝、微信、银联、点卡充值卡、百度支付等多个渠道的支付接口。使用此模块可轻松实现各个渠道的支付功能。

使用之前需要先到[ipaynow](https://payment.ipaynow.cn/online_merchant/index.jsp)注册，并根据技术文档部署 Server SDK。
需要参考聚合支付SDK中后台接口文档，开发后台接口使用聚合支付秘钥对交易数据进行签名。

**使用此模块之前需先配置config文件的Feature，方法如下**

	名称：ipaynow
	参数：urlScheme
	描述：配置微信专用的URL Scheme，使得本应用可以启动微信客户端，并与之交换数据，同时可以从支付宝客户端(微信暂时不能自动返回)返回到本应用。
配置示例:

```js
<feature name="ipaynow">
<param name="urlScheme" value="wxd0d84bbf23b4a0e4"/>
</feature>
```
字段描述:

		1.param-urlScheme：声明此字段为URL Scheme类型

#**generatePresignMessage**<div id="a1"></div>

获取待签名字符串

generatePresignMessage(params, callback)

##params

appId：

- 类型：字符串
- 默认值：无
- 描述：商家从ipaynow申请的商户应用唯一标识，不能为空

mhtCharset：

- 类型：字符串
- 默认值：无
- 描述：商户字符编码，定值UTF-8，不能为空

mhtCurrencyType：

- 类型：字符串
- 默认值：无
- 描述：商户订单币种类型，156为人民币，不能为空

mhtOrderAmt：

- 类型：字符串
- 默认值：无
- 描述：商户订单交易金额，单位为分，不能为空

mhtOrderDetail：

- 类型：字符串
- 默认值：无
- 描述：商户订单详情，不能为空

mhtOrderName：

- 类型：字符串
- 默认值：无
- 描述：商户商品名称，不能为空

mhtOrderNo：

- 类型：字符串
- 默认值：无
- 描述：商户订单号，不能为空

mhtorderStartTime：

- 类型：字符串
- 默认值：无
- 描述：商户订单开始时间，yyyyMMddHHmmss，不能为空

mhtOrderType：

- 类型：字符串
- 默认值：无
- 描述：商户交易类型，01为普通消费，不能为空

notifyUrl：

- 类型：字符串
- 默认值：无
- 描述：商户后台通知URL，不能为空


consumerId：

- 类型：字符串
- 默认值：无
- 描述：客户ID，可以为空


consumerName：

- 类型：字符串
- 默认值：无
- 描述：客户名称，可以为空


mhtOrderTimeOut：

- 类型：字符串
- 默认值：无
- 描述：商户订单超时时间60~3600（秒），默认3600，可以为空


mhtReserved：

- 类型：字符串
- 默认值：无
- 描述：商户保留域 ，不能为空

payChannelType：

- 类型：字符串
- 默认值：无
- 描述：渠道类型，下列中的一个值，银联支付:11，支付宝支付:12，微信支付:13，点卡支付:16，充值卡支付:19，百度支付：50，不能为空



##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	result:		// success或fail
	preSignStr: 		//待签名字符串（url编码）
	msg:				//当result为fail时出现该字段，说明错误原因
}

```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:””		//错误描述
}
```

##示例代码

```js
var da = (new Date()).format("yyyyMMddHHmmss");

var demo = api.require("ipaynow");

var param ={
    appId:"1408709961320306",
    mhtCharset:"UTF-8",
    mhtCurrencyType:"156",
    mhtOrderAmt:"10",
    mhtOrderDetail:"关于订单验证接口的测试",
    mhtOrderName:"IOS插件测试用例",
    mhtOrderNo:da,
    mhtorderStartTime:da,
    mhtOrderType:"01",
    notifyUrl:"http://localhost:10802/"
    };
demo.generatePresignMessage(param, function(ret, err){
    alert(ret.originStr);
});
```

##补充说明

方法输出样例：

```
{"result":"success","preSignStr":"appId%3D1408709961320306%26mhtCharset%3DUTF-8%26mhtCurrencyType%3D156%26mhtOrderAmt%3D10%26mhtOrderDetail%3D%E5%85%B3%E4%BA%8E%E8%AE%A2%E5%8D%95%E9%AA%8C%E8%AF%81%E6%8E%A5%E5%8F%A3%E7%9A%84%E6%B5%8B%E8%AF%95%26mhtOrderName%3DIOS%E6%8F%92%E4%BB%B6%E6%B5%8B%E8%AF%95%E7%94%A8%E4%BE%8B%26mhtOrderNo%3D20150304114640%26mhtOrderStartTime%3D20150304114640%26mhtOrderType%3D01%26notifyUrl%3Dhttp%3A%2F%2Flocalhost%3A10802%2F"}
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**doSignature**<div id="a2"></div>

对订单信息进行签名，商户也可选择自行处理签名不调用此方法，只须pay方法中的data参数满足条件即可。
该方法需要与商户后台签名接口配合使用，商户服务器应获取paydata字段中的内容，对内容做url解码，并对解码后的内容进行签名处理。
签名公式为MD5(服务器接收的解码内容+MD5(聚合支付平台发放的APP秘钥));

doSignature(params, callback)

##params

preSignStr：

- 类型：字符串
- 默认值：无
- 描述：待签名字符串，不能为空

post_content：

- 类型：字符串
- 默认值：无
- 描述：后台签名请求报文，不能为空


post_url：

- 类型：字符串
- 默认值：无
- 描述：后台签名url，不能为空


##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	result：         //签名结果状态，值为success或fail
	preSignStr: 		//待签名字符串
	resultStr: 		//后台签名结果字符串
	msg:				//当为fail时出现该字段，说明错误原因
}

```

err：

- 类型：JSON对象

内部字段：

```js
{
    msg: ""      //错误描述
}
```

##示例代码

```js
var originStr=ret.originStr; //ret为上一步执行结果

var url="http://yuyangnews.ipaynow.cn/ZyPluginPaymentTest_PAY/api/pay2.php";
var demo = api.require('ipaynow');

var param = {
    originStr:originStr,
    presignStr:"paydata="+originStr,
    url:url
};

demo.doSignature(param, function(ret, err){
    alert(ret.resultStr);
});
```

##补充说明

方法输出样例：

```
{"result":"success","resultStr":"mhtSignature=9e5ca89f18b872278fd18e9838d91da2&mhtSignType=MD5","preSignStr":"appId%3D1408709961320306%26mhtCharset%3DUTF-8%26mhtCurrencyType%3D156%26mhtOrderAmt%3D10%26mhtOrderDetail%3D%E5%85%B3%E4%BA%8E%E8%AE%A2%E5%8D%95%E9%AA%8C%E8%AF%81%E6%8E%A5%E5%8F%A3%E7%9A%84%E6%B5%8B%E8%AF%95%26mhtOrderName%3DIOS%E6%8F%92%E4%BB%B6%E6%B5%8B%E8%AF%95%E7%94%A8%E4%BE%8B%26mhtOrderNo%3D20150304114640%26mhtOrderStartTime%3D20150304114640%26mhtOrderType%3D01%26notifyUrl%3Dhttp%3A%2F%2Flocalhost%3A10802%2F"}
```


##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

#**pay**<div id="a3"></div>

支付订单

pay(params, callback)

##params

data：

- 类型：字符串
- 默认值：无
- 描述：商户的订单信息，key=“value”形式，以&连接，(待签名串&mhtSignType=MD5&mhtSignature=签名串)，不能为空

urlSchema：

- 类型：字符串
- 默认值：无
- 描述：商户app的urlSchema，和config文件中的urlScheme相同，不能为空


##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	result: 		//返回的支付结果, [success]支付成功、[fail]支付失败、[cancel]支付取消；
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    msg:""      //错误描述
}
```

##示例代码

```js
var paydata=ret.originStr+"&"+ret.resultStr;//ret为上一步执行结果

var demo = api.require('ipaynow');
var param = {
    data:paydata,
    urlSchema:"UZApp"
};
demo.pay(param, function(ret, err){
    alert(ret.result);
});
```

##补充说明

方法输出样例：

```
{"result":"[success]支付成功"}
```

##可用性

iOS系统，Android系统
可提供的1.0.0及更高版本