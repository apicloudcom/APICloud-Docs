/*
Title: unionPay
Description: unionPay
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

<div class="outline">
[pay](#a1)
</div>

#**概述**

unionPay封装了银联支付的SDK，使用此模块可在应用内接入银联支付。接入流程参考[银联支付接入文档](https://open.unionpay.com/ajweb/help/query?id=66)

**银联支付流程如下：**

（1）用户在客户端中点击购买商品，客户端发起订单生成请求到商户后台；<br>
（2）商户后台收到订单生成请求后，按照《手机控件支付产品接口规范》（[文档见银联帮助中心->下载->开发包->手机控件支付参评技术开发包](https://open.unionpay.com/ajweb/help/file)）组织并推送订单信息至银联后台；<br>
（3）银联后台接收订单信息并检查通过后，生成对应交易流水号（即TN），并回复交易流水号至商户后台（应答要素：交易流水号等）；<br>
（4）商户后台接收到交易流水号，将交易流水号返回给客户端；<br>
（5）客户端通过交易流水号（TN）调用支付控件；<br>
（6）用户在支付控件中输入相关支付信息后，由支付控件向银联后台发起支付请求；<br>
（7）支付成功后，银联后台将支付结果通知给商户后台；<br>
（8）银联将支付结果通知支付控件；<br>
（9）支付控件显示支付结果并将支付结果返回给客户端；<br>

**注: 本模块实现了上述流程的（5）---（9）步骤**

<div id="a1"></div>
#**pay**

按交易流水号支付订单

pay({params}, callback(ret, err))

##params

tn：

- 类型：字符串
- 描述：交易流水号信息，银联后台生成，通过商户后台返回到客户端

devMode：

- 类型：布尔
- 描述：接入模式设定，值为 false 代表接入生成环境
- 默认值：true

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	result: "success"     //字符串类型；支付结果信息
	                      //取值范围：
	                      //success（支付成功）
	                      //fail（支付失败）
	                      //cancel（用户取消支付）
}
```

##示例代码

```js
	var unPay = api.require('unionPay');
	api.ajax({
	    url: 'http://202.101.25.178:8080/sim/gettn',//从银联测试服务器上获取tn号
	    method: 'post',
	    dataType: 'text',
	    returnAll:false,
	    data:{
	        values: {OrderID: '20150811000001'}//提交商户后台生成的订单ID 
	    }
	},function(ret,err){
	    if (ret) {
			unPay.pay({
				tn: ret,
				devMode: true
		    }, function(ret, err){
			   api.alert({msg:JSON.stringify(ret)});
		    });
	    }
	});
```

##可用性

iOS系统  Android系统

可提供的1.0.0及更高版本