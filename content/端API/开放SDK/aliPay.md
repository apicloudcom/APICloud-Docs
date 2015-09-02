/*
Title: aliPay
Description: 支付宝模块
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">
<div class="outline">
[config](#a1)

[pay](#a2)
</div>

#**概述**

aliPay封装了支付宝的SDK，开发者只需配置从支付宝申请的相应的参数即可将支付宝功能集成到自己的app，安全，方便，快捷。让开发者摆脱冗长的支付宝集成流程

![图片说明](/img/docImage/aliPay.jpg)

**支付宝模块使用注意：**

1. 此模块必须在真机环境下使用
2. 使用前商户必须与支付宝公司签约获得商户id、账户id、商家私钥、支付宝公钥(可参考技术专题->开放SDK接入帮助->调用支付宝前期准备文档)
3. 商家私钥的生成和支付宝公钥的获取见支付宝官方相关文档，这里解释下私钥和公钥的配置。商家私钥和支付宝公钥可通过key.xml文件设置，也可通过config接口配置，亦可在pay时随参数一起传进来。官方建议将商家私钥和支付宝公钥配置在key.xml文件里，将该文件放在widget下的res文件里，服务器编译时会将此文件加密。 aliPay模块底层代码会自动读取该文件中的公钥和私钥等参数，提高安全性。key.xml文件格式如下:
```js
<?xml version="1.0" encoding="UTF-8" ?>
<security>
<item name="aliPay_partner" value=" 1234567890183798 "/>
<item name="aliPay_seller" value=" 1234567890783837 "/>
<item name="aliPay_rsaPriKey" value="***"/>
<item name="aliPay_rsaPubKey" value="***"/>
<item name="aliPay_notifyURL" value="***"/>
<item name="其它服务需加密的参数配置 " value="***"/>
.
.
.
</security> 
```
4. 使用此模块前需要先配置config.xml文件的Feature，方法如下：

	名称：aliPay

	参数：urlScheme

	描述：配置支付宝专用的URL Scheme，使得本应用可以启动支付宝客户端，并与之交换数据，同时可以从支付宝客户端返回到本应用
	配置示例：
	```js
	<feature name="aliPay">
		<param name="urlScheme" value="AliPay + widgetId" />
	</feature>
	```
	字段描述：
		1. 	param-urlScheme：声明此字段为URL Scheme类型
		2. 	param-value：固定值，由字符串‘AliPay’和本应用的widgetId拼接而成

#**config**<div id="a1"></div>

配置支付宝信息

config({params},callback(ret,err))
##params

partner：

- 类型：字符串
- 默认值：无
- 描述：商户id，不能为空

seller：

- 类型：字符串
- 默认值：无
- 描述：商户账户id，不能为空

rsaPriKey：

- 类型：字符串
- 默认值：无
- 描述：商户私钥，不能为空

rsaPubKey：

- 类型：字符串
- 默认值：无
- 描述：支付宝公钥，不能为空

notifyURL：

- 类型：字符串
- 默认值：无
- 描述：支付完成后，支付宝会通知客户端，也会把支付结果通知给商家，此url即是商家的地址，不能为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
 status:       //状态码，是否初始化成功
}
```
err：

- 类型：JSON对象

内部字段：

```js
{
    msg: ""       //错误描述，字符串
}
```
##示例代码

```js
var obj = api.require('aliPay');
var subject = '订单名';
var body = '订单描述';
var amount = '10.99';
var tradeNO = '467467655635';
var notifyURL = 'http://www.apicloud.com';
obj.config({
  partner:'12345678901234',
  seller:'123456789024354',
  rsaPriKey:'testKEY',
  rsaPubKey:'testKEY',
  notifyURL:notifyURL
},function(ret,err) {
  api.alert({
      title: '支付结果',
      msg: ret.msg,
      buttons: ['确定']
  });
});
```

##补充说明

要用真机调试，并且填写正确的商家信息

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

#**pay**<div id="a2"></div>

调用支付宝客户端支付

pay({params}, callback(ret, err))

##params

<del>partner：</del>

- <del>类型：字符串</del>
- <del>默认值：无</del>
- <del>描述：商户id，可为空</del>

<del>seller：</del>

- <del>类型：字符串</del>
- <del>默认值：无</del>
- <del>描述：商户账户id，可为空</del>

<del>rsaPriKey：</del>

- <del>类型：字符串</del>
- <del>默认值：无</del>
- <del>描述：商户私钥，可为空</del>

<del>rsaPubKey：</del>

- <del>类型：字符串</del>
- <del>默认值：无</del>
- <del>描述：支付宝公钥，可为空</del>

subject：

- 类型：字符串
- 默认值：无
- 描述：交易商品名，不能为空

body：

- 类型：字符串
- 默认值：无
- 描述：交易商品的简介，不能为空

amount：

- 类型：字符串
- 默认值：无
- 描述：交易商品的价钱（单位为元，精确到分如：10.29元），不能为空

tradeNO：

- 类型：字符串
- 默认值：无
- 描述：交易订单编号（由商家按自己的规则生成），不能为空
<del>
<del>notifyURL：</del>

-<del> 类型：字符串</del>
- <del>默认值：无</del>
- <del>描述：支付完成后，支付宝会通知客户端，也会把支付结果通知给商家，此url即是商家的地址，可为空</del>

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
    statusMessage:"" //支付情况返回的信息----Will be deprecated at some point, please replace with msg
    statusCode:"" //支付情况的代码  ----Will be deprecated at some point, please replace with code
    msg:""           //支付情况返回的信息，字符串类型
    code:""         //支付情况的代码，字符串类型参考附录错误代码列表
}
```

##示例代码

```js
var obj = api.require('aliPay');
var subject = '订单名';
var body = '订单描述';
var amount = '10.99';
var tradeNO = '4563548735674';
var notifyURL = 'http://www.apicloud.com';
obj.pay({
    subject:subject,
	body:body,
	amount:amount,
	tradeNO:tradeNO
},function(ret,err) {
	api.alert({
		title: '支付结果',
		msg: ret.msg,
		buttons: ['确定']
	});
});
```

##补充说明

要用真机调试，并且填写正确的商家信息

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

**附录**
<div id="a100"></div>
以下为安全支付服务所定义的错误代码：
<table>
    <tr>
        <th>错误代码</th>
        <th>含义</th>
    </tr>
    <tr>
        <td>9000</td>
        <td>操作成功</td>
    </tr>
    <tr>
        <td>4000</td>
        <td>系统异常</td>
    </tr>
    <tr>
        <td>4001</td>
        <td>数据格式不正确</td>
    </tr>
    <tr>
        <td>4003</td>
        <td>该用户绑定的支付宝账户被冻结或不允许支付</td>
    </tr>
	<tr>
        <td>4004</td>
        <td>该用户已解除绑定</td>
    </tr>
	<tr>
        <td>4005</td>
        <td>绑定失败或没有绑定</td>
    </tr>
	<tr>
        <td>4006</td>
        <td>订单支付失败</td>
    </tr>
    <tr>
        <td>4010</td>
        <td>重新绑定账户</td>
    </tr>
    <tr>
        <td>6000</td>
        <td>支付服务正在进行升级操作</td>
    </tr>
    <tr>
        <td>6001</td>
        <td>用户中途取消支付操作</td>
    </tr>
    <tr>
        <td>0001(APICloud定义)</td>
        <td>缺少商户配置信息（商户id，支付公钥，支付密钥）</td>
    </tr>
    <tr>
        <td>0002(APICloud定义)</td>
        <td>用户当前设备没有安装支付宝客户端（ios）或安全支付插件（Android）</td>
    </tr>
    <tr>
        <td>0003(APICloud定义)</td>
        <td>签名错误（公钥私钥错误）</td>
    </tr>
</table>

