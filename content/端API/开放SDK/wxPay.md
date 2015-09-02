/*
Title: wxPay
Description: wxPay
*/
<div class="outline">
[getOrderId](#b1)

[payOrder](#b2)

[config](#b3)

[pay](#b4)
</div>

#**概述**

**wxPay 模块优化了 weiXin 模块的支付功能。**

wxPay 封装了微信支付的 SDK，可实现微信支付功能；使用之前须从微信开放平台申请获得 appid、secret（用于获取 access_token）、partnerkey（微信公众平台商户模块生成的商户密钥）。

**本模块封装了两套支付方案：**

- **方案一**：开发者通过 getOrderId、payOrder 自己处理签名过程（微信开放平台建议把 getOrderId 放在服务器端执行）；

- **方案二**：通过 config 接口和 pay 接口把签名过程交予模块内部处理。config 接口的参数可通过 `key.xml` 文件配置。

**使用此模块之前建议先配置  config.xml 文件，方法如下**

- 名称：wxPay
- 参数：urlScheme、apiKey、apiSecret
- 配置示例:

```js
  <feature name="wxPay">
    <param name="urlScheme" value="wxd0d84bbf23b4a0e4"/>
    <param name="apiKey" value="wxd0d84bbf23b4a0e4"/>
    <param name="apiSecret" value="a354f72aa1b4c2b8eaad137ac81434cd"/>
  </feature>
```
- 字段描述:

    **urlScheme**：（必须配置）用于实现应用间跳转及数据交换，本应用可以启动微信客户端，也可以从微信客户端跳回本应用。urlScheme 的 value 值是从微信开放平台获取的 appid。
    
    **apiKey**：（必须配置）从微信开放平台获取的 appid，值与 urlScheme 相同。

    **apiSecret**：从微信开放平台获取的 secret。**获取支付 token 需要配置此项**。

**key.xml 配置详解：**

`key.xml` 文件（适用于支付方案二）需要放在 `widget/res` 文件目录下，格式如下：

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<security>
  <item name="wxPay_appId" value="wxd0d84bbf23b4a0e4"/>
  <item name="wxPay_mchId" value="1234567890"/>
  <item name="wxPay_partnerKey" value="***"/>
  <item name="wxPay_notifyUrl" value="***"/>
  <item name="其它服务需加密的参数配置 " value="***"/>
  .
  .
  .
</security> 
```
- 字段描述:

    **wxPay_appId**：在微信开发者平台创建应用生成的 appId 

    **wxPay_mchId**：商户号，填写商户对应参数

    **wxPay_partnerKey**：商户API密钥，务必同在商户平台->账户设置->API安全里填写的密钥保持一致，此密钥是根据微信对商户密钥的规范自己生成的

    **wxPay_notifyUrl**：支付结果回调页面，微信支付服务器会将支付结果数据发送到该地址

<div id="b1"></div>

#**getOrderId**

获取预支付订单号（适用于支付方案一）

getOrderId({params}, callback(ret, err))

##params

info：

- 类型：字符串
- 描述：订单信息（详见[统一下单-请求参数](https://pay.weixin.qq.com/wiki/doc/api/app.php?chapter=9_1)）签名后的字符串。具体方法见微信支付[安全规范-签名算法](https://pay.weixin.qq.com/wiki/doc/api/app.php?chapter=4_3) 。**注意：微信官方建议本过程在服务器端执行**

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    return_code:'SUCCESS',                            //字符串类型；返回的状态码，SUCCESS/FAIL，此字段是通信标识，非交易标识，交易是否成功需要查看result_code来判断
    return_msg:'签名失败',                             //（可选项）字符串类型；返回信息，如非空，为错误原因，如：签名失败、参数格式校验错误...
    //以下字段在return_code为SUCCESS的时候有返回
    appid:'wx8888888888888888',                       //字符串类型；公众账号ID，调用接口提交的公众账号ID
    mch_id:'1900000109',                              //字符串类型；商户号，调用接口提交的商户号
    device_info:'013467007045764',                    //（可选项）字符串类型；设备号，调用接口提交的终端设备号
    nonce_str:'5K8264ILTKCH16CQ2502SI8ZNMTM67VS',     //字符串类型；随机字符串，微信返回的随机字符串
    sign:'C380BEC2BFD727A4B6845133519F3AD6',          //字符串类型；签名，微信返回的签名，详见上文链接（安全规范-签名算法）。用于验签（将本 ret JSON 对象按照签名算法签名后得到字符串跟本字符串比较，若相同则读取预支付订单，若不同则有可能是仿冒订单号）
    result_code:'SUCCESS',                            //字符串类型；业务结果，SUCCESS/FAIL
    err_code:'SYSTEMERROR',                           //（可选项）字符串类型；错误代码，详细参见统一支付订单-错误码（https://pay.weixin.qq.com/wiki/doc/api/app.php?chapter=9_1）
    err_code_des:'系统错误',                           //（可选项）字符串类型；错误代码描述，错误返回的信息描述
    //以下字段在return_code 和result_code都为SUCCESS的时候有返回
    trad_type:'JSAPI',                                //字符串类型；交易类型，调用接口提交的交易类型，取值如下：JSAPI，NATIVE，APP，详细说明见参数规定（https://pay.weixin.qq.com/wiki/doc/api/app.php?chapter=4_2）
    prepay_id:'wx201410272009395522657a690389285100', //字符串类型；预支付交易会话标识，微信生成的预支付回话标识，用于后续接口调用中使用，该值有效期为2小时
    code_url:'URl：weixin：//wxpay/s/An4baqw'         //（可选项）字符串类型；二维码链接，trade_type为NATIVE是有返回，可将该参数值生成二维码展示出来进行扫码支付
}
```

##示例代码

```js
var wxPay = api.require('wxPay');
wxPay.getOrderId({
	info: ''
}, function(ret,err){
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="b2"></div>

#**payOrder**

支付订单（适用于支付方案一）

payOrder({params}, callback(ret, err))

##params

apiKey：

- 类型：字符串
- 描述：（可选项）从微信开放平台获取的 appid，若不传则从当前 widget 的 `config.xml` 中读取。

orderId：

- 类型：字符串
- 描述：getOrderId 获取的订单号

mchId：

- 类型：字符串
- 描述：商家和微信合作的 id 号，审核通过后微信服务器会发送到商家邮箱

nonceStr：

- 类型：字符串
- 描述：随机字符串，防重发

timeStamp：

- 类型：字符串
- 描述：时间戳，防重发

package：

- 类型：字符串
- 描述：（可选项）扩展字段，暂填写固定值Sign=WXPay
- 默认：Sign=WXPay

sign：

- 类型：字符串
- 描述：商家根据微信开放平台文档对数据做的签名，详见：[安全规范-签名算法](http://mch.weixin.qq.com/wiki/doc/api/app.php?chapter=4_3)

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true    //布尔型；true||false
}
```

err：

- 类型：JSON对象
- 内部字段：（错误码详见[全局返回码说明](http://mp.weixin.qq.com/wiki/17/fa4e1434e57290788bde25603fa2fcbd.html)）

```js
{
    code: 1     //数字类型；
                //错误码：
                //-2（用户取消，发生场景：用户不支付了，点击取消，返回APP）
                //-1（未知错误，可能的原因：签名错误、未注册APPID、项目设置APPID不正确、注册的APPID与设置的不匹配、其他异常等）
                //1 (apiKey值非法)
}
```

##示例代码

```js
var wxPay = api.require('wxPay');
wxPay.payOrder({
    apiKey: '',
    apiSecret: '',
    orderId: '',
    mchId: '',
    nonceStr: '',
    timeStamp: '',
    package: '',
    sign: ''
}, function(ret, err){
     if(ret.status){
        //支付成功
     }else{
		alert(err.code);
     }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="b3"></div>

#**config**

配置模块内部处理签名时需要的参数（适用于支付方案二）

config({params}, callback(ret, err))

##params

apiKey：

- 类型：字符串
- 描述：（可选项）从微信开放平台获取的 appid，若不传则从当前 widget 的 `config.xml` 中读取。

mchId：

- 类型：字符串
- 描述：（可选项）商家和微信合作的 id 号，审核通过后微信服务器会发送到商家邮箱，若不传或者传空则从 `key.xml` 中读取

partnerKey：

- 类型：字符串
- 描述：（可选项）商户 API 密钥，务必同在商户平台->账户设置->API安全里填写的密钥保持一致，此密钥是根据微信对商户密钥的规范自己生成的，若不传或者传空则从 `key.xml` 中读取

notifyUrl：

- 类型：字符串
- 描述：（可选项）支付结果回调页面，若不传或者传空则从 `key.xml` 中读取

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true   //布尔型；true||false
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
    code: 1     //数字类型；错误码
                //-1（未知错误）
                //1（apiKey 值非法）
                //2（mchId 值非法）
                //3（partnerKey 值非法）
                //4（notifyUrl 值非法）
}
```

##示例代码

```js
var wxPay = api.require('wxPay');
wxPay.config({
     apiKey: '',
     mchId: '',
     partnerKey: '',
     notifyUrl: ''
}, function(ret, err){
     if(ret.status){
        alert('配置商户支付参数成功');
     }else{
         alert(err.code);
     }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

<div id="b4"></div>

#**pay**

支付订单（适用于支付方案二）

pay({params}, callback(ret, err))

##params

description：

- 类型：字符串
- 描述：商品或支付订单简要描述

totalFee：

- 类型：字符串
- 描述：订单总金额，只能为整数，单位：分（￥）

tradeNo：

- 类型：字符串
- 描述：商户系统内部的订单号，32个字符以内，可包含字母，其他说明见[商户订单号](https://pay.weixin.qq.com/wiki/doc/api/app.php?chapter=4_2)

spbillCreateIP：

- 类型：字符串
- 描述：（可选项）APP 和网页支付提交用户端 IP，Native 支付填调用微信支付 API 的机器 IP
- 默认值：196.168.1.1

deviceInfo：

- 类型：字符串
- 描述：（可选项）终端设备号（门店号或收银设备 ID），注意：PC 网页或公众号内支付请传 "WEB"

detail：

- 类型：字符串
- 描述：（可选项）商品名称明细列表

attach：

- 类型：字符串
- 描述：（可选项）附加数据，在查询 API 和支付通知中原样返回，该字段主要用于商户携带订单的自定义数据

feeType：

- 类型：字符串
- 描述：（可选项）符合 ISO 4217标准的三位字母代码，其他值列表详见[货币类型](https://pay.weixin.qq.com/wiki/doc/api/app.php?chapter=4_2)
- 默认：CNY（人民币）

timeStart：

- 类型：字符串
- 描述：（可选项）订单生成时间，格式为 yyyyMMddHHmmss，如2009年12月25日9点10分10秒表示为20091225091010。其他详见[时间规则](https://pay.weixin.qq.com/wiki/doc/api/app.php?chapter=4_2)

timeExpire：

- 类型：字符串
- 描述：（可选项）订单失效时间，格式为 yyyyMMddHHmmss，如2009年12月27日9点10分10秒表示为20091227091010。其他详见[时间规则](https://pay.weixin.qq.com/wiki/doc/api/app.php?chapter=4_2)。**注意：最短失效时间间隔必须大于5分钟**

goodsTag：

- 类型：字符串
- 描述：（可选项）商品标记，代金券或立减优惠功能的参数，说明详见[代金券或立减优惠](https://pay.weixin.qq.com/wiki/doc/api/sp_coupon.php?chapter=12_1)

productId：

- 类型：字符串
- 描述：（可选项）trade_type=NATIVE ，此 id 为二维码中包含的商品 ID，商户自行定义，详见[商户平台开发者文档](https://pay.weixin.qq.com/wiki/doc/api/app.php?chapter=9_1)

openId：

- 类型：字符串
- 描述：（可选项）trade_type=JSAPI ，用户在商户 appid 下的唯一标识。下单前需要调用[【网页授权获取用户信息】](http://mp.weixin.qq.com/wiki/17/c0f37d5704f0b64713d5d2c37b468d75.html)接口获取到用户的 Openid


##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    status: true,   //布尔型；true||false
}
```

err：

- 类型：JSON对象
- 内部字段：（错误码详见[统一下单错误码](https://pay.weixin.qq.com/wiki/doc/api/app.php?chapter=9_1)）

```js
{
    code: 1       //数字类型；
                  //错误码：
                  //-2（用户取消）
                  //-1（可能的原因：签名错误、未注册APPID、项目设置APPID不正确、注册的APPID与设置的不匹配、其他异常等）
                  //1（必传参数缺失）
    msg: 'NOAUTH' //字符串类型；
                  //取值范围：
                  //NOAUTH （商户无此接口权限）
                  //NOTENOUGH（余额不足）
                  //ORDERPAID（商户订单已支付）
                  //ORDERCLOSED（订单已关闭）
                  //SYSTEMERROR（系统错误）
                  //APPID_NOT_EXIST （APPID不存在）
                  //MCHID_NOT_EXIST（MCHID不存在）
                  //APPID_MCHID_NOT_MATCH（appid和mch_id不匹配）
                  //LACK_PARAMS（缺少参数）
                  //OUT_TRADE_NO_USED（商户订单号重复）
                  //SIGNERROR （签名错误）
                  //XML_FORMAT_ERROR（XML格式错误）
                  //REQUIRE_POST_METHOD（请使用post方法）
                  //POST_DATA_EMPTY（post数据为空）
                  //NOT_UTF8（编码格式错误）
}
```

##示例代码

```js
var wxPay = api.require('wxPay');
wxPay.pay({
     description: 'iPad mini 16G 白色',
     totalFee: '888',
     tradeNo: '1217752501201407033233368018',
     spbillCreateIP: '196.168.1.1',
     deviceInfo: '013467007045764',
     detail: 'iPad mini 16G 白色',
     attach: '说明',
     feeType: 'CNY',
     timeStart: '20091225091010',
     timeExpire: '20091227091010',
     goodsTag: 'WXG',
     productId: '12235413214070356458058',
     openId: 'oUpF8uMuAJO_M2pxb1Q9zNjWeS6o'
},function(ret, err){
     if(ret.status){
         alert(ret.result);
     }else{
         alert(err.code);
     }
});
```

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
