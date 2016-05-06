/*
Title: paypal
Description: paypal
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

<div class="outline">
[pay](#a1)
</div>

#**概述**

paypal封装了 PayPal 支付的 SDK，使用此模块可在应用内接入 PayPal 支付。接入 PayPal 支付前需要先到 PayPal [开发者中心](https://developer.paypal.com)注册开发者账号，然后在[创建App页面](https://developer.paypal.com/developer/applications)创建 App 获取 Client ID。Client ID 包括测试id（Sandbox）和正式上线id（Live）。**使用此模块需云编译或自定义loader**

PayPal 支持的 [国家地区](https://www.paypal.com/webapps/mpp/country-worldwide)

PayPal 支持的货币种类参考 [PayPal REST API Country and Currency Support](https://developer.paypal.com/docs/integration/direct/rest-api-payment-country-currency-support/)

PayPal 的常见问题 [FAQ](https://developer.paypal.com/docs/faq/#non-US-dev)

PayPal 验证支付结果方法 [Verify a mobile payment](https://developer.paypal.com/webapps/developer/docs/integration/mobile/verify-mobile-payment/)

**PayPal支付流程如下：**

（1）用户在客户端中点击购买商品，携带商品信息向 PayPal 服务器发起支付请求；<br>
（2）PayPal 服务器收到支付请求，处理后将结果返回客户端；<br>
（3）客户端收到 PayPal 服务器返回的支付结果，将其发送给商家客户端；<br>
（4）商家客户端收到客户端发来的支付结果，然后向 PayPal 服务器请求验证；<br>
（5）PayPal 服务器端验证结果返回商家服务器；<br>
（6）支付结束；<br>

**注: 本模块实现了上述流程的（1）、（2）步骤**

**使用本模块需先配置key.xml文件**
	
需将申请到的 CLIENT_ID_FOR_PRODUCTION 和 CLIENT_ID_FOR_SANDBOX 配置到 `key.xml` （本文件放在 widget 包里的 res 文件夹下）文件内，其格式如下:

	```js
	<?xml version="1.0" encoding="UTF-8" ?>
	<security>
	<item name="paypal_productionID" value="*********"/>
	<item name="paypal_sandboxID" value="*********"/>
	<item name="其它服务需加密的参数配置 " value="***"/>
	.
	.
	.
	</security> 
	```
	
	
- 字段描述：
	
	**paypal_productionID**：在 PayPal 开发者中心创建 App 后得到的 Client ID For Live。
	
	**paypal_sandboxID**：在 PayPal 开发者中心创建 App 后得到的 Client ID For Sandbox。


<div id="a1"></div>
#**pay**

支付

pay({params}, callback(ret, err))

##params

currency：

- 类型：字符串
- 描述：交易货币类型，取值范围见：[PayPal REST API Country and Currency Support](https://developer.paypal.com/docs/integration/direct/rest-api-payment-country-currency-support/)。**注意本模块不支持 JPY（日元） HUF（匈牙利福林） TWD（台币）**

description：

- 类型：字符串
- 描述：交易商品描述

price：

- 类型：字符串
- 描述：交易商品的价钱，单位：元（$）

mode：

- 类型：字符串
- 描述：支付环境，取值范围如下：
	- production：线上环境，真实扣款
	- sandbox：开发测试环境
	- noNetwork：不跟 PayPal 服务器交互，可伪装支付成功状态。用于单元测试


##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
   state: "success" ,                   //字符串类型；支付结果信息
	                                    //取值范围：
	                                    //success（支付成功）
	                                    //fail（支付失败）
	                                    //cancel（用户取消支付）
  client: {                             //JSON对象；支付客户端信息
    environment: "sandbox",             //字符串类型；类型：sandbox/live
    paypal_sdk_version: "2.0.0",        //字符串类型；sdk 版本号
    platform: "iOS",                    //字符串类型；平台：iOS/android
    product_name: "PayPal iOS SDK;"     //字符串类型；产品名称
  },                                    
  response: {                           //JSON对象；支付结果信息
    create_time: "2014-02-12T22:29:49Z",//字符串类型；时间
    id: "PAY-564191241M8701234KL57LXI", //字符串类型；id
    intent: "sale",                     //字符串类型；支付行为目的
    state: "approved"                   //字符串类型；状态
  },                                    
  response_type: "payment"              //字符串类型；回应类型
}
```

##示例代码

```js
	var paypal = api.require('paypal');
	paypal.pay({
	    currency: 'USD',
	    price: '36.06',
	    description: 'APICloud 短袖T恤',
	    mode: 'noNetwork'
	},function(ret){
	    if (ret) {
		   api.alert({msg:JSON.stringify(ret)});
	    }
	});
```

##可用性

iOS系统  Android系统

可提供的1.0.0及更高版本