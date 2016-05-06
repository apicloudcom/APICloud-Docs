/*
Title: aliPay
Description: 支付宝模块
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">
<div class="outline">
[payOrder](#a1)

[config](#a2)

[pay](#a3)
</div>

#**概述**

**支付宝简介**

支付宝（中国）网络技术有限公司是国内领先的第三方支付平台，致力于提供“简单、安全、快速”的支付解决方案。支付宝公司从2004年建立开始，始终以“信任”作为产品和服务的核心。旗下有“支付宝”与“支付宝钱包”两个独立品牌。自2014年第二季度开始成为当前全球最大的移动支付厂商。
支付宝主要提供支付及理财服务。包括网购担保交易、网络支付、转账、信用卡还款、手机充值、水电煤缴费、个人理财等多个领域。在进入移动支付领域后，为零售百货、电影院线、连锁商超和出租车等多个行业提供服务。还推出了余额宝等理财服务。

支付宝与国内外180多家银行以及VISA、MasterCard国际组织等机构建立战略合作关系，成为金融机构在电子支付领域最为信任的合作伙伴。

**支付宝特色功能**

钱包

支付宝也可以在智能手机上使用，该手机客户端为支付宝钱包。支付宝钱包具备了电脑版支付宝的功能，也因为手机的特性，内含更多创新服务。如“当面付”、“二维码支付”等。
还可以通过添加“服务”来让支付宝钱包成为自己的个性化手机应用。
支付宝钱包主要在iOS、Android上使用，iPad版与WP版正在开发中。

安全

支付涉及到用户的资金安全，因此遵循官方的安全规范至关重要。
如安全控件、短信校验服务、数字证书、第三方证书、支付盾、宝令、宝令手机版、安全保护问题、安全策略、手机安全设置等。
几乎所有的支付服务都可以使用支付宝。从购物到水电燃气缴费，且正有部分取代现金的趋势。

还款

2009年1月15日支付宝推出信用卡还款服务，国内39家银行发行的信用卡均支持。是最受欢迎的第三方还款平台。
主要优势：免费查信用卡账单、免费还款，还有自动还款/还款提醒等增值服务。推荐使用支付宝钱包。
2014年第一季度，76%的还信用卡是用支付宝钱包完成的。

转账

通过支付宝转账分为两种：1、转账到支付宝账号，资金瞬间到达对方支付宝账户；转账到支付宝账户的限额2、转账到银行卡，用户可以转账到自己或他人的银行卡，支持百余家银行，最快2小时到账。支持到账的银行和到账时间、转账到银行卡的限额
推荐使用支付宝钱包，免手续费。

缴费

2008年底开始，支付宝推进公共事业缴费服务，已经覆盖了全国300多个城市，支持1200多个合作机构。除了水电煤等基础生活缴费外，其还扩展到交通罚款、物业费、有线电视费等更多与老百姓生活息息相关的缴费领域。
常用的在线缴费服务有：
水电煤缴费、教育缴费、交通罚款、有线电视费

服务窗

在支付宝钱包的“服务”中添加相关服务账号，就能在钱包内获得更多服务。包括银行服务、缴费服务、保险理财、手机通讯服务、交通旅行、零售百货、医疗健康、休闲娱乐、美食吃喝等10余个类目。
区别于其他公众服务平台，服务窗具有天然的支付基因、超亿的支付用户群体、以及严格审核的商户服务，这使得服务窗产生更大的生态价值。

**模块概述**

aliPay封装了支付宝的SDK，开发者只需配置从支付宝申请的相应的参数即可将支付宝功能集成到自己的app。若当前设备（客户端）未安装支付宝 app，则调用内嵌网页版支付。支付宝支付处理流程，[请参考论坛](http://community.apicloud.com/bbs/forum.php?mod=viewthread&tid=18494&highlight=alipay)。使用此模块需先与支付宝签约，签约流程请参照[支付宝接入指南](http://doc.open.alipay.com/doc2/detail?spm=0.0.0.0.v406JH&treeId=58&articleId=103541&docType=1)。 支付宝服务器端代码参考[论坛帖子](http://community.apicloud.com/bbs/forum.php?mod=viewthread&tid=24822&extra=)。

![图片说明](/img/docImage/aliPay.jpg)


**本模块封装了两套支付方案：**

- **方案一**：开发者通过 payOrder 方法来进行支付，自己处理订单信息以及签名过程；

- **方案二**：通过 config 接口和 pay 接口把订单信息以及签名过程交予模块内部处理。config 接口的参数可通过 `key.xml` 文件配置（***此时需要云编译或自定义loader才能测试本功能***）。

**支付宝使用注意：**

1. 此模块必须在真机环境下使用
2. 使用前商户必须与支付宝公司签约获得商户Id、账户Id、商家私钥、支付宝公钥。详情可参看支付宝文档[PID和密钥管理](http://doc.open.alipay.com/doc2/detail?spm=0.0.0.0.pF0173&treeId=58&articleId=103543&docType=1)
3. 商家私钥的生成和支付宝公钥的获取见支付宝官方相关文档[RSA私钥及公钥生成](http://doc.open.alipay.com/doc2/detail?treeId=58&articleId=103242&docType=1)（[开发者技术分享](http://community.apicloud.com/bbs/forum.php?mod=viewthread&tid=14777&highlight=alipay)，[私钥生成方法](http://community.apicloud.com/bbs/forum.php?mod=viewthread&tid=30005&extra=)，[常见错误](http://community.apicloud.com/bbs/forum.php?mod=viewthread&tid=16292&highlight=alipay)）。
4. 商家公钥一定要上传，具体方法参考支付宝官方文档[上传RSA公钥](http://doc.open.alipay.com/doc2/detail.htm?spm=0.0.0.0.rKRiyk&treeId=58&articleId=103578&docType=1)。
5. 使用此模块前需先配置 [config.xml](/APICloud/技术专题/app-config-manual)文件，方法如下：

	- 名称：aliPay
	- 参数：urlScheme
	- 配置示例:
		
		```js
		<feature name="aliPay">
			<param name="urlScheme" value="AliPayA000000011" />
		</feature>
		```
		
	- 字段描述：
		
		**urlScheme**：（必须配置）用于实现应用间跳转及数据交换，本应用可以启动支付宝客户端，也可以从支付宝客户端跳回本应用（***此时需要云编译或自定义loader才能测试本功能***）。urlScheme 的 value 值由字符串 ‘AliPay’ 和本应用的 widgetId 拼接而成
	
**密钥配置（适用于支付方案二）**
	
下面说明下私钥和公钥的配置（支付方案一可忽略密钥的配置直接调用payOrder支付）：商家私钥和支付宝公钥可通过 `key.xml` 文件设置，也可通过 config 接口配置。若选择通过`key.xml` 文件配置，则在自己的支付页面内直接调用 pay 接口传入相应参数即可，无需调用 config 接口。建议将商家私钥和支付宝公钥配置在 `key.xml` 文件里，将该文件放在 widget 下的 res 文件下，服务器编译时会将此文件加密。 aliPay模块底层代码会自动读取该文件中的公钥和私钥等参数，提高安全性。`key.xml` 文件格式如下:

	```js
	<?xml version="1.0" encoding="UTF-8" ?>
	<security>
	<item name="aliPay_partner" value="*********"/>
	<item name="aliPay_seller" value="*********"/>
	<item name="aliPay_rsaPriKey" value="***"/>
	<item name="aliPay_rsaPubKey" value="***"/>
	<item name="aliPay_notifyURL" value="***"/>
	<item name="其它服务需加密的参数配置 " value="***"/>
	.
	.
	.
	</security> 
	```
	
	
- 字段描述：
	
	**aliPay_partner**：（必须配置）合作者身份ID（PID）是商户与支付宝签约后，商户获得的支付宝商户唯一识别码。当商户把支付宝功能接入商户网站时会用到PID，以便让支付宝认证商户。以2088开头的16位纯数字。请到支付宝官网[查看PID](http://doc.open.alipay.com/doc2/detail?treeId=58&articleId=103544&docType=1)。
	
	**aliPay_seller**：（必须配置）商户账户，商户登陆支付宝和支付宝签约的账户号。
	
	**aliPay_rsaPriKey**：（必须配置）商户私钥，用于支付过程中的签名，生成规范参考支付宝官方文档，[RSA私钥及公钥生成](http://doc.open.alipay.com/doc2/detail.htm?spm=0.0.0.0.QQZbTS&treeId=58&articleId=103242&docType=1)。
	
	**aliPay_rsaPubKey**：（必须配置）支付宝公钥。请到支付宝官网[查看支付宝公钥](http://doc.open.alipay.com/doc2/detail.htm?spm=0.0.0.0.uVDGrl&treeId=58&articleId=103546&docType=1)。
	
	**aliPay_notifyURL**：（必须配置）回调 url，支付结束，支付宝服务器会把支付结果通知给该 url。	如果 notifyURL 带参数需要url编码，否则 xml 加密之后无法找到对应的 key，参考[开发者分享](http://community.apicloud.com/bbs/forum.php?mod=viewthread&tid=17669&page=1#pid97424)	

##**模块接口**

#**payOrder**<div id="a1"></div>

调用支付宝客户端支付

payOrder({params}, callback(ret, err))

##params

orderInfo：

- 类型：字符串
- 描述：支付信息（由订单信息，签名，签名类型组成），支付信息生成（此过程可放在服务器端）可参照支付宝官方文档[请求参数说明](http://doc.open.alipay.com/doc2/detail?treeId=59&articleId=103663&docType=1)

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    code:        //字符串类型；错误码，取值范围如下：
                 //9000：支付成功
                 //4000：系统异常
                 //4001：数据格式不正确
                 //4003：该用户绑定的支付宝账户被冻结或不允许支付
                 //4004：该用户已解除绑定
                 //4005：绑定失败或没有绑定
                 //4006：订单支付失败
                 //4010：重新绑定账户
                 //6000：支付服务正在进行升级操作
                 //6001：用户中途取消支付操作
}
```

##示例代码

```js
var aliPay = api.require('aliPay');
aliPay.payOrder({
  orderInfo:'partner="2088101568358171"&seller_id="xxx@alipay.com"&out_trade_no="0819145412-6177"&subject="测试"&body="测试测试"&total_fee="0.01"&notify_url="http://notify.msp.hk/notify.htm"&service="mobile.securitypay.pay"&payment_type="1"&_input_charset="utf-8"&it_b_pay="30m"&sign="lBBK%2F0w5LOajrMrji7DUgEqNjIhQbidR13GovA5r3TgIbNqv231yC1NksLdw%2Ba3JnfHXoXuet6XNNHtn7VE%2BeCoRO1O%2BR1KugLrQEZMtG5jmJIe2pbjm%2F3kb%2FuGkpG%2BwYQYI51%2BhA3YBbvZHVQBYveBqK%2Bh8mUyb7GM1HxWs9k4%3D"&sign_type="RSA"'
},function(ret,err) {
  api.alert({
      title: '支付结果',
      msg: ret.code,
      buttons: ['确定']
  });
});
```

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

#**config**<div id="a2"></div>

配置支付宝信息，**适用于支付方案二**

config({params}, callback(ret, err))
##params

partner：

- 类型：字符串
- 描述：商户 Id

seller：

- 类型：字符串
- 描述：商户账户 Id

rsaPriKey：

- 类型：字符串
- 描述：商户私钥

rsaPubKey：

- 类型：字符串
- 描述：支付宝公钥

notifyURL：

- 类型：字符串
- 描述：支付完成后，支付宝会通知客户端，也会把支付结果通知给商家，此 URL 即是商家服务器地址

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
   status:       //布尔类型；是否配置成功，true|false
}
```
err：

- 类型：JSON 对象
- 内部字段：

```js
{
    code: ""       //数字类型；错误码，取值范围如下：
                   //0：未知错误
                   //1：缺少商户配置信息（商户id，支付公钥，支付密钥）
}
```
##示例代码

```js
var aliPay = api.require('aliPay');
aliPay.config({
  partner:'12345678901234',
  seller:'123456789024354',
  rsaPriKey:'testKEY',
  rsaPubKey:'testKEY',
  notifyURL:'http://www.apicloud.com'
},function(ret,err) {
  api.alert({
      title: '支付结果',
      msg: ret.msg,
      buttons: ['确定']
  });
});
```

##可用性

iOS系统，Android系统

可提供的1.0.1及更高版本

#**pay**<div id="a3"></div>

调用支付宝客户端支付，**适用于支付方案二**

pay({params}, callback(ret, err))

##params

subject：

- 类型：字符串
- 描述：交易商品名

body：

- 类型：字符串
- 描述：交易商品的简介

amount：

- 类型：字符串
- 描述：交易商品的价钱（单位为元，精确到分如：10.29元）

tradeNO：

- 类型：字符串
- 描述：交易订单编号（由商家按自己的规则生成），**不可包含字母，否则在 iOS 平台上报错**

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    code: 1          //字符串类型；支付结果状态码，取值范围如下：
                     //9000：支付成功
                     //4000：系统异常
                     //4001：数据格式不正确
                     //4003：该用户绑定的支付宝账户被冻结或不允许支付
                     //4004：该用户已解除绑定
                     //4005：绑定失败或没有绑定
                     //4006：订单支付失败
                     //4010：重新绑定账户
                     //6000：支付服务正在进行升级操作
                     //6001：用户中途取消支付操作
                     //0001：缺少商户配置信息（商户id，支付公钥，支付密钥）
                     //0002：缺少参数（subject、body、amount、tradeNO）
                     //0003：签名错误（公钥私钥错误）
}
```

##示例代码

```js
var aliPay = api.require('aliPay');
var notifyURL = 'http://www.apicloud.com';
aliPay.pay({
   subject: '订单名',
	body: '订单描述',
	amount: '0.01',
	tradeNO: '4563548735674'
},function(ret,err) {
	api.alert({
		title: '支付结果',
		msg: ret.code,
		buttons: ['确定']
	});
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本