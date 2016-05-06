/*
Title: coinport
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：币丰支付</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">
<div class="outline">
[config](#a1)

[pay](#a2)
</div>

#**概述**

coinport封装了[币丰支付](https://pay.coinport.com)的移动端SDK，使用此模块可实现比特币支付功能。

币丰支付是专业比特币支付平台，支持商家通过人民币或美元定价商品，由平台按实时汇率计算成比特币向买家收款，账款以人民币或美元结算，不受比特币价格波动影响，商家不承担任何风险。详情请访问[币丰支付网站](https://pay.coinport.com)。

iOS平台比特币钱包应用可从以下地址下载：[币丰钱包](http://www.coinport.com/wallet)。


#**config**<div id="a1"></div>

配置商户信息

config({params})

##params

token：

- 类型：字符串
- 默认值：无
- 描述：API token,不能为空。可到[币丰支付网站](https://pay.coinport.com)注册账户后，从“我的账户｜我的设置”页面查询。

secret：

- 类型：字符串
- 默认值：无
- 描述：secret key，不能为空。可到[币丰支付网站](https://pay.coinport.com)注册账户后，从“我的账户｜我的设置”页面查询。

notifyURL：

- 类型：字符串
- 默认值：无
- 描述：接收支付结果的回调地址，不能为空。


##示例代码

```js
var coinport = api.require('coinport');

coinport.config(
    {
        token: "coinport1",
        secret: "ABCDEF",
        notifyURL: "https://pay.coinport.com/debug"
    }
);
```

##补充说明

需配置的信息包括：API token, secret key, notify URL。前两个参数可到[币丰支付网站](https://pay.coinport.com)注册账户后，从“我的账户｜我的设置”页面查询。

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本


#**pay**<div id="a2"></div>

提交支付请求

pay({params}, callback(ret, err))

##params

currency：

- 类型：字符串
- 默认值：CNY
- 描述：结算货币，不能为空。支持以下取值：CNY(人民币),USD(美元),BTC(比特币)。大小写不敏感。

price：

- 类型：数字
- 默认值：无
- 描述：支付金额，单位是currency参数所指定的货币。不能为空。例如：订单金额为1.23人民币，price取值为1.23，无需关心比特币汇率，向买家收取的比特币数量由系统根据实时汇率自动计算。

orderId：

- 类型：字符串
- 默认值：无
- 描述：商家订单号，不能为空。

itemDesc：

- 类型：字符串
- 默认值：无
- 描述：订单描述，可以为空。


##callback(ret, err)

ret：

- 类型：JSON 对象

内部字段：

```js
{
    code:0    //返回码
    msg:""    //错误描述
}
```


##示例代码

```js
var coinport = api.require('coinport.pay');

// call coinport.config() first

var param = {
    currency:"cny",
    price: 0.3,
    orderId: "12345",
    itemDesc: "测试订单"
};
coinport.pay(param, callBack);

function callBack(ret, err){
    api.alert({
        title: '接口返回',
        msg: ret.msg,
        buttons: ['确定']
    });
}
```

##补充说明

详细参数请参阅：[币丰支付API文档](https://pay.coinport.com/api)

更多SDK及技术资料请访问：[币丰支付开发者支持](https://pay.coinport.com/develop)

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本

