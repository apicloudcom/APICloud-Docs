/*
Title: iap
Description: iap
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>
<div id="method-content">

<div class="outline">
[getProducts](#1)

[purchase](#2)

[restoreTransactions](#3)

[setDownloadListener](#4)

[startDownloads](#5)

[pauseDownloads](#6)

[resumeDownloads](#7)

[cancelDownloads](#8)
</div>

#**概述**

iap模块封装了iOS系统应用内购买相关功能，部分功能如商品内容下载，在iOS系统6.0之前不可用

#**getProducts**<div id="1"></div>

获取有效商品列表

getProducts(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	invalidProductIds:			//无效的商品id列表，字符串数组
	products:				//有效商品列表，JSON数组
	[{
		productId:			//商品id，字符串类型
		title:				//商品标题，字符串类型
		description:			//商品描述，字符串类型
		price:				//商品价格，数字类型
		formattedPrice:			//商品格式化后的价格，如￥6.00，字符串类型
		downloadable:			//是否有下载内容，只iOS6.0及以后系统有效，布尔类型
		downloadContentLengths:		//下载内容长度，数字组成的数组
		downloadContentVersion:		//下载内容的版本，字符串类型
	}]
}
```
err：

- 类型：JSON对象

内部字段：

```js
{
	msg:''    //错误描述
}
```

##示例代码

```js
var iap = api.require('iap');
iap.getProducts(
	function(ret, err){
		if (ret) {
			if(ret.products){
			
			}
			if (ret.invalidProductIds) {
				
			}
		} else {
			
		}
	}
);
```

##补充说明

使用此接口来获取有效的商品

##可用性

iOS系统

可提供的1.0.0及更高版本


#**purchase**<div id="2"></div>

购买商品

purchase({params}, callback(ret, err))

##params

productId：

- 类型：字符串
- 默认值：无
- 描述：有效的商品id，不能为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	state:					//交易状态，详见交易状态常量，数字类型
	productId:				//商品id，字符串类型
	transactionId:				//交易id，字符串类型
	originalTransactionId:			//原始交易id，只在state为恢复购买时有效，字符串类型
	receipt:				//交易凭证，经过base64编码，用于验证交易是否合法和有效，避免因越狱破解内购后造成损失，只在state为购买成功时有效，字符串类型
	errorCode:				//交易失败时的错误码，详见错误码常量，数字类型
	downloads:				//有下载内容时的下载信息列表，iOS6.0之前无效
	[{
		transactionId：			//下载内容所属交易id，字符串类型
		contentId:			//下载内容id，字符串类型
		downloadState:			//下载状态，详见下载状态常量，数字类型
		progress：			//下载进度，取值范围0~1，数字类型
		contentLength:			//文件内容大小，数字类型
		timeRemaining:			//下载剩余时间，-1时表示未知，数字类型
		contentVersion:			//下载内容的版本，字符串类型
		contentURL:			//下载成功后文件路径，字符串类型
		errorCode:			//下载失败时的错误码，数字类型
		errorMsg:			//下载失败时的错误描述，字符串类型
	}]
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:'' 		//其它错误，如参数错误、如当前用户不能使用应用内购买等
}
```

##示例代码

```js
var iap = api.require('iap');
iap.purchase({
productId:'com.company.app.productid'		//有效商品id
}, function(ret, err){
    if(ret){
		var state = ret.state;
		switch (state)
		{
			case 0:
			{
				//交易已加入队列
			}
				break;
			case 1:
			{
				//交易成功，应该对交易凭证进行验证；若有下载内容，需把下载内容提供给用户
			}
				break;
			case 2:
			{
				//交易失败
			}
				break;
			case 3:
			{
				//交易恢复，调用恢复购买时会触发，同样若有下载内容，需把下载内容提供给用户
			}
				break;
			case 4:
			{
				//交易等待被确认，待确认后交易状态会变更为其它状态
			}
				break;
			default:
				break;
		}
    }else{
	api.alert({msg:err.msg});
    }
});
```

##补充说明

无

##可用性

iOS系统

可提供的1.0.0及更高版本


#**restoreTransactions**<div id="3"></div>

恢复用户以前购买过的所有商品交易

restoreTransactions(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	finished:					//是否所有交易恢复完成，若未完成，则会有以下当前具体交易信息，布尔类型
	transaction:
	{
		state:					//交易状态，详见交易状态常量，数字类型
		productId:				//商品id，字符串类型
		transactionId:				//交易id，字符串类型
		originalTransactionId:			//原始交易id，只在state为恢复购买时有效，字符串类型
		receipt:				//交易凭证，经过base64编码，用于验证交易是否合法和有效，避免因越狱破解内购后造成损失，只在state为购买成功时有效，字符串类型
		downloads:				//有下载内容时的下载信息列表，iOS6.0之前无效
		[{
			transactionId：			//下载内容所属交易id，字符串类型
			contentId:			//下载内容id，字符串类型
			downloadState:			//下载状态，详见下载状态常量，数字类型
			progress：			//下载进度，取值范围0~1，数字类型
			contentLength:			//文件内容大小，数字类型
			timeRemaining:			//下载剩余时间，-1时表示未知，数字类型
			contentVersion:			//下载内容的版本，字符串类型
			contentURL:			//下载成功后文件路径，字符串类型
			errorCode:			//下载失败时的错误码，数字类型
			errorMsg:			//下载失败时的错误描述，字符串类型
		}]
	}
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	errorCode:    	//错误码，详见错误码常量
}
```

##示例代码

```js
var iap = api.require('iap');
iap.restoreTransactions(
	function(ret, err){
		if(ret){
		if (ret.finished){
				//恢复购买全部完成
			} else {
				//获取当前恢复成功的交易
				var transaction = ret.transaction;
			}
		}else{
			api.alert({errorCode:err.errorCode});
		}
	}
);
```

##补充说明

无

##可用性

iOS系统

可提供的1.0.0及更高版本


#**setDownloadListener**<div id="4"></div>

设置下载监听，所有的下载进度通过此回调返回

setDownloadListener(callback(ret))

##callback(ret)

ret：

- 类型：JSON对象

内部字段：

```js
{
	downloads:			//下载状态和进度变化的下载列表，JSON数组
	[{
		transactionId：		//下载内容所属交易id，字符串类型
		contentId:		//下载内容id，字符串类型
		downloadState:		//下载状态，详见下载状态常量，数字类型
		progress：		//下载进度，取值范围0~1，数字类型
		contentLength:		//文件内容大小，数字类型
		timeRemaining:		//下载剩余时间，-1时表示未知，数字类型
		contentVersion:		//下载内容的版本，字符串类型
		contentURL:		//下载成功后文件路径，字符串类型
		errorCode:		//下载失败时的错误码，数字类型
		errorMsg:		//下载失败时的错误描述，字符串类型
	}]
}
```

##示例代码

```js
var iap = api.require('iap');
iap.setDownloadListener(function(ret){
	var downloads = ret.downloads;
});
```

##补充说明

无

##可用性

iOS系统

可提供的1.0.0及更高版本


#**startDownloads**<div id="5"></div>

开始下载

startDownloads({params})

##params

contentIds：

- 类型：字符串数组
- 默认值：无
- 描述：下载内容id组成的数组，不能为空

##示例代码

var iap = api.require('iap');
iap.startDownloads({
	contentIds: ['xxx']
});

##补充说明

无

##可用性

iOS系统

可提供的1.0.0及更高版本


#**pauseDownloads**<div id="6"></div>

暂停下载

pauseDownloads({params})

##params

contentIds：

- 类型：字符串数组
- 默认值：无
- 描述：下载内容id组成的数组，不能为空

##示例代码

```js
var iap = api.require('iap');
iap.pauseDownloads({
	contentIds: ['xxx']
});
```

##补充说明

无

##可用性

iOS系统

可提供的1.0.0及更高版本


#**resumeDownloads**<div id="7"></div>

恢复下载

resumeDownloads({params})

##params

contentIds：

- 类型：字符串数组
- 默认值：无
- 描述：下载内容id组成的数组，不能为空

##示例代码

```js
var iap = api.require('iap');
iap.resumeDownloads({
	contentIds: ['xxx']
});
```

##补充说明

无

##可用性

iOS系统

可提供的1.0.0及更高版本


#**cancelDownloads**<div id="8"></div>

取消下载

cancelDownloads({params})

##params

contentIds：

- 类型：字符串数组
- 默认值：无
- 描述：下载内容id组成的数组，不能为空

##示例代码

```js
var iap = api.require('iap');
iap.cancelDownloads({
	contentIds: ['xxx']
});
```

##补充说明

无

##可用性

iOS系统

可提供的1.0.0及更高版本
</div>


<div id="const-content">

<div class="outline">
[错误码](#a1)

[下载状态](#a2)

[交易状态](#a3)
</div>

#**错误码**<div id="a1"></div>

应用内购买过程中的错误码。数字类型

##取值范围：

- 0		//未知错误
- 1		//无效请求
- 2		//用户取消购买
- 3		//交易无效
- 4		//设备不允许进行交易
- 5		//不是有效商品

#**下载状态**<div id="a2"></div>

下载状态。数字类型

##取值范围：

- 0		//等待下载
- 1		//正在下载
- 2		//暂停下载
- 3		//下载完成
- 4		//下载失败
- 5		//取消下载


#**交易状态**<div id="a3"></div>

交易状态。数字类型

##取值范围：

- 0		//已加入交易队列
- 1		//交易完成
- 2		//交易失败
- 3		//恢复购买
- 4		//交易等待被确认，iOS8.0及以后有效
