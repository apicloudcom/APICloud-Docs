/*
Title: appleUnionPay
Description: appleUnionPay
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[canMakePayments](#p1)
[pay](#p2)
</div>

#**概述**

Apple Pay 是苹果公司在2014苹果秋季新品发布会上发布的一种基于 NFC 的手机支付功能，于2014年10月20日在美国正式上线。2016年2月18日凌晨5：00， Apple Pay 业务在中国上线。

###**Apple Pay 支持的设备**

iPhone系列：iPhone 6、iPhone6 Plus、iPhone 6s、iPhone 6s Plus

iPad系列：iPad Air 2、iPad mini 3、iPad mini 4、iPad Pro

Apple Watch

注意：iPhone 5 和 iPhone 5s 本身并不支持，而是连接到它们的 Apple Watch 可以用，因为5系列的手机不带NFC。

###**Apple Pay 系统要求**

IOS 需升级到9.2及以上，WatchOS 需要2.1或更高版本。

###**Apple Pay 使用方法**

使用 Apple Pay 需要在苹果系统自带的 Wallet 程序里添加银行卡。iPhone 用户点击进入 Wallet 后，点击屏幕右上方的+号，再点击“下一步”就可进入申请页面，然后将银行卡正面放置在iPhone摄像头前，使卡面出现在屏幕的提示框内，系统会自动识别卡号，当然也可以手工输入卡号，接下来需要手工输入姓名、卡片有效期与安全码，还要阅读业务须知并选择接受。添加卡片成功后需激活才能使用，客户要确认手机号，并接收和输入验证码，才能成功激活。

如果需要在 Apple Watch 上添加，只要在相关联的 iPhone 上打开 Watch APP，轻点“Wallet 与 Apple Pay”，再轻点“添加信用卡或借记卡”，也可同样进行设置。需要注意的是，只有IOS9.2以上的版本才支持 Apple Pay。

同一台设备可以添加多张银行卡。工行表示，同一台苹果设备可添加5张信用卡，首张添加卡即为默认卡。客户可以在 “Wallet” APP 中通过长按卡片并将该卡排列为首位的方式将该卡设为默认付款卡，也可在“设置- Wallet 与 Apple Pay”功能中设置默认付款卡。

Apple Pay 分为线上支付和线下支付。线下支付不需要手机接入互联网，也不需要点击进入APP，甚至无须唤醒显示屏，只要将iPhone 靠近有银联闪付标志的读卡器，并将手指放在HOME键上验证指纹，即可进行支付。也可以在iPhone 处于黑屏锁定状态时，轻点两下主屏幕按钮进入 Wallet，快速进行购买。如果交易终端显示需要输入密码，还需要输入银行卡的交易密码。只需一两秒钟就可以完成Apple Pay 支付。

本模块封装了 Apple Pay 的线上支付功能，开发者只需几行代码，即可把苹果支付功能集成至自己的app内。用户使用自己的 app 购买商品时，可选择使用 Apple Pay 支付方式进行支付自己所购买的商品。

提醒：如果你在你的 APP 中销售的是电子产品或者虚拟货币，你应该使用内购方式（[iap](http://docs.apicloud.com/端API/功能扩展/iap)）而不是 App Pay 去销售你的东西。你可以使用 Apple Pay 销售你的实体商品和服务。

###**Apple Pay 国内合作银行**

- 中国农业银行
- 中国银行
- 上海银行
- 中信银行
- 中国建设银行
- 广发银行
- 招商银行
- 中民生银行
- 中国工商银行
- 兴业银行
- 中国邮政储蓄银行
- 浦发银行

###**Apple Pay 国内近期推出银行**

- 北京银行
- 交通银行
- 广州银行
- 宁波银行
- 中国光大银行
- 华夏银行
- 平安银行

###**Apple Pay 上线国家**

- 美国
- 英国
- 加拿大
- 澳大利亚
- 中国

###**Apple Pay 国内支付供应商**

苹果公司强烈建议开发者选择支持 Apple Pay 并提供 SDK 的支付供应商。当然您也可以提供自己的服务器端解决方案，以用于从您的 App 接收付款、解密付款令牌并与支付供应商进行互动。信用卡和借记卡付款的处理可能非常复杂。如果您不具备相应的专业知识和系统，又希望您的 App 支持 Apple Pay，使用支付供应商提供的 SDK 是最为便捷可靠的一种方式。Apple Pay 支付的付款流程如下图所示：

![付款流程](/img/docImage/appleUnionPay/applePay.png)

目前国内苹果支付的供应商如下：

- [中国银联](http://en.unionpay.com)
- [连连支付](https://apple.lianlianpay.com/OpenPlatform/)
- [首信易支付](https://www.beijing.com.cn/product/ApplePay_ch.jsp)
- [易宝支付](https://www.yeepay.com/applepay)
- [银联商务](http://www.chinaums.com)

本模块即是封装了中国银联的 Apple Pay 控件开发包

###**银联支付控件 SDK 模式 Apple Pay 支付的实现方式**

![付款流程](/img/docImage/appleUnionPay/applePayUnion.png)

- 1-2：商户生成订单，通过商户 SERVER 端将订单信息发送给银联支付网关；
- 3-4：银联支付网关记录订单信息，返回用来标识订单的 TN 号，经由商户 SERVER 返回至给
商户 APP；
- 5：商户 APP 调用银联SDK，将 TN 号传递给银联 SDK
- 6：银联 SDK 向苹果公司的 PASSKIT FRAMEWORK 发起支付请求；
- 7：接口返回加密的支付 Token 信息；
- 8-9：银联 SDK 将支付 Token 传递给银联支付网关，完成交易认证；
- 10-12：银联将支付结果返回给商户APP，商户SERVER，商户APP 负责提示用户交易结果

本模块封装了支付流程的5-12。

###**appleUnionPay 模块使用攻略**

**步骤一、成为银联手机支付入网商户**

参照《全渠道业务运营服务指引》，签署业务Apple Pay 线上支付合作协议，申请银联商
户代码，准备接入的相关参数。 详情参考[商户入网指南](https://merchant.unionpay.com/join/help/director)

**步骤二 、登录银联商户服务平台，通过商户服务平台申请 CSR**

***a、关于商户 CSR***

接入银联 Apple Pay 在线支付的商户，须生成 Apple Pay 专用的 CSR 文件并提及至评估开发者网站进行签名，以签署证书，取得 Apple Pay 的访问权限。在银联 SDK 模式（本模块逻辑流程）中，银联代为商户生成 CSR 文件，商户可直接登录银联商户服务平台获取

***a、商户 CSR 申请方式***

1、成为银联商户服务平台用户。在申请银联 Apple Pay 接入时，银联的系人会分配商户服务平台的登录权限及 CSR 的申请权限 。存量商户应确认是否开通了 Apple Apple 接入权限。

2、通过银联商户服务平台申请 CSR。银联在 商户服务平台 https://merchant.unionpay.com/中提供 Apple Pay 的 CSR 下载功能。登录商户服务平台，进入安全管理-CSR 文件下载，点击 “生成 CSR”按钮，并将获取的 CSR 保存。CSR文件与商户代码一对应，是交易安全保护的重要环节请勿将 CSR 透漏给无关人员。

3、商户服务平台 CSR 生成页面示意

![csr下载](/img/docImage/appleUnionPay/applePayCSR.png)

重置 CSR 后，原 CSR 即刻失效，应重新向苹果公司的网站提交新的 CSR 文件。

**步骤三、苹果证书及描述文件**

- 1.前往苹果开发者中心的Certificates, Identifiers, and Profiles部分并且[创建一个新的商家ID](https://developer.apple.com/account/ios/identifiers/merchant/merchantCreate.action)，注意此 id 需要在支付时作为 mID 传给模块，其一般格式为：merchant.com.app名。
- 2.接下来，前往[创建苹果证书](https://developer.apple.com/account/ios/certificate/certificateCreate.action)，并创建一个新的苹果支付证书。这需要向苹果公司上传从银联商户服务平台申请的证书签名请求（CSR），同时也需要勾选1过程创建的商家ID。
- 3.[创建App IDs](https://developer.apple.com/account/ios/identifiers/bundle/bundleCreate.action)，注意创建时勾选 Apple Pay 功能。App ID 即是我们平台上称之为包名的 id，其一般格式为：com.公司名.app名。App ID 创建完成后要编辑其 Apple Pay 功能，此过程需要勾选2过程创建的苹果支付证书。
- 4.[申请证书描述文件](https://developer.apple.com/account/ios/profile/profileCreate.action)，此描述文件（需安装mac电脑上后在钥匙串中导出为mobileprovision文件）需要上传 APICloud 平台编译服务器。此过程需要勾选3过程创建的App ID，以及之前已经创建好的苹果证书（需安装mac电脑上后在钥匙串中导出为p12文件，然后上传 APICloud 编译服务器）。

**步骤四、服务器端开发**

服务器端开发包可以去银联支付官网下载[银联ApplePay控件开发包](https://open.unionpay.com/ajweb/help/file/techFile?productId=80)，论坛亦有相关[帖子](http://community.apicloud.com/bbs/forum.php?mod=viewthread&tid=24249&extra=)可以下载到，


**注意：使用本模块必须云编译或自定义loader**

#**canMakePayments**<div id="p1"></div>

判断手机是否支持 Apple Pay 功能，以及是否已加载有可用的支付卡片

canMakePayments(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status:			//布尔类型；支付环境判断，true|false
}
```

##示例代码

```js
var appleUnionPay = api.require('appleUnionPay');
appleUnionPay.canMakePayments(function( ret, err ){		
    if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统

可提供的1.0.0及更高版本

#**pay**<div id="p2"></div>

支付

pay({params}, callback(ret, err))


##params

tn：

- 类型：字符串
- 描述：交易流水号，商户后台向银联后台提交订单信息后，由银联后台生成并下发给商户后台的交易凭证

mode：

- 类型：字符串
- 描述：接入模式，标识商户以何种方式调用支付控件，该参数提供以下两个可选值
- 取值范围：
	- 00：代表接入生产环境（正式版本需要）
	- 01：代表接入开发测试环境（测试版本需要）

mID：

- 类型：字符串
- 描述：在苹果公司申请的商户号，表示调用 Apple Pay 所需要的 MerchantID


##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	result: ,       //字符串类型；支付状态返回值，取值范围如下：
	                //success：支付成功
	                //failure：支付失败
	                //cancel：支付取消
	                //unknownCancel：支付取消，交易已发起，状态不确定，商户需查询商户后台确认支付状态
	description:,   //字符串类型；表示支付失败时候服务器返回的错误描述，包括文字信息与应答码两部分
	otherInfo:      //字符串类型；目前表示成功支付时包含的优惠信息
}
```
**字段举例描述：**

description：例如：“可用余额不足［1000051］“，此信息前半部分为文字错误信息，后7位为错误应答码。当支付成功或支付取消的时候 errorDescription 取值为nil。应答码列表可以在[论坛](http://community.apicloud.com/bbs/forum.php?mod=viewthread&tid=24249&extra=)下载，亦可到银联支付官网下载[银联ApplePay控件开发包](https://open.unionpay.com/ajweb/help/file/techFile?productId=80)。

otherInfo：例如：“currency=元&order_amt=20.00&pay_amt=15.00“，其中 currency 表示币种，order_amt 表示订单金额，pay_amt 表示实付金额。优惠形式包括但不限于立减折扣，随机折扣等。当无优惠信息时 otherInfo 取值为 nil，可不作处理。当出现优惠信息时，商户可以根据此优惠信息组织个性化的优惠页面进行展示，但应在页面中加入原金额、优惠金额及“云闪付”要素，UI 示例如下：

![csr下载](/img/docImage/appleUnionPay/applePayExamples.png)

**商户订单是否成功支付应以商户后台收到全渠道返回的支付结果为准，此处支付
控件返回结果仅作为商户App 向用户展示支付结果使用。**

##示例代码

```js
var appleUnionPay = api.require('appleUnionPay');
appleUnionPay.pay({
    tn: "201602231715123483638",
    mode: "01",
    mID: "merchent.com.apicloud"
}, function(ret, err){		
    if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

iOS系统

可提供的1.0.0及更高版本