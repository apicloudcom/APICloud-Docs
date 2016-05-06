/*
Title: adsYoumi
Description: adsYoumi
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：有米</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>

<div id="method-content">

<div class="outline">
[init](#a0)

[initWall](#a1)

[release](#a2)

[showWall](#a3)

[queryPoints](#a4)

[awardPoints](#a5)

[spendPoints](#a6)

[setListener](#a7)

[removeListener](#a8)

[setWallBrowserConfig](#a9)

[setGlobalConfig](#a10)

</div>

#**概述**

有米广告是中国首家移动广告平台，致力于为广告主提供精准的产品推广和品牌营销服务，为应用开发者创造公正和优质的广告收益。本模块只需简单调用几个接口即可实现对广告平台的集成。

#**init**<div id="a0"></div>

初始化模块

init({params}, callback(ret, err))

##params

appId：

- 类型：字符串
- 描述：APP的ID，在[有米平台](http://www.youmi.net)上申请

appSecret：

- 类型：字符串
- 描述：APP的密钥，在有米平台上生成

isTestModel：

- 类型：bool
- 描述：（可选项）是否为测试模式
- 默认值：false
	+ 对于 **积分广告** ：测试模式下，广告只能结算积分，不结算收入
	+ 以下情况下属于测试模式：
		1. 没有imei唯一设备号的设备（如：部分Android平板）
		2. 应用未上传、待审核的情况
		3. 已上传并通过审核，但是后续版本应用 ID 和密钥与应用的包名不对应
	+ 嵌入好的app需要上传到有米审核才算通过，才可以不用测试模式

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status:				//操作成功状态值				int  1 - 成功     0 - 失败
}
```

err：

- 类型：JSON 对象
- 内部字段：
```js
{
	code:				//错误编码						int
	msg:				//返回操作信息/错误信息			string
}
```

##示例代码

```js
var adsYoumi = api.require('adsYoumi');
adsYoumi.init({ appId:"7f9cda62c051e0a2" , appSecret:"8b82c13f3330417c" , isTestModel: true } , function( ret , err ){
	//成功返回
	if(ret.status==1){
		//
	}
	else{
		//输出错误信息
		api.alert({ msg : err.msg });
	}
});
```

##补充说明

可以在[config.xml](/APICloud/技术专题/app-config-manual)里面写feature,基本的三个参数将参数写在里面，然后直接调用init()也可以。

[config.xml](/APICloud/技术专题/app-config-manual)中配置如下
```xml
	<feature name="adsYoumi">
    		<param name="appId" value="7f9cda62c051e0a2"/>
    		<param name="appSecret" value="8b82c13f3330417c"/>
    		<param name="isTestModel" value="true"/>
  	</feature>
```

##可用性

Android系统

可提供的1.0.0及更高版本


#**initWall**<div id="a1"></div>

初始化积分墙

initWall({params}, callback(ret, err))

##params

isUsingServerCallBack：

- 类型：bool
- 默认值：false
- 描述：设置是否采用[服务器托管积分](http://wiki.youmi.net/Youmi_android_offers_order_callback_protocol)，默认使用客户端托管积分
	+ *客户端托管积分* :
		+ ``用户完成任务 -> 有米服务器生成积分订单 -> 有米sdk通过轮询请求服务器获取订单 -> 本地存储并管理积分``
	+ *服务器托管积分* ：
		+ ``用户完成任务 -> 有米服务器生成积分订单 -> 有米推送积分订单到开发者服务器 -> 开发者服务器告知开发者App -> 开发者App告知用户已获取积分``
	+ **强烈建议开发者采用自己的服务器进行托管积分，提高积分安全性。**

userId：

- 类型：字符串
- 描述：如果使用了服务器回调，建议传入APP系统中的用户id，为空或长度超过50则无效

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status:				//操作成功状态值				int  1 - 成功     0 - 失败
}
```

err：

- 类型：JSON 对象
- 内部字段：
```js
{
	code:				//错误编码						int
	msg:				//返回操作信息/错误信息 		string
}
```

##示例代码

```js
	var adsYoumi = api.require('adsYoumi');
	adsYoumi.init();
	adsYoumi.initWall({ isUsingServerCallBack : true , userId : '123456789' } , function( ret , err ){
		//成功返回
		if(ret.status==1){
			//
		}
		else{
			//输出错误信息
			api.alert({ msg : err.msg });
		}
	});
```

##补充说明

在模块初始化之后使用，初始化积分墙之后才可以使用积分墙

##可用性

Android系统

可提供的1.0.0及更高版本


#**release**<div id="a2"></div>

释放模块

release()

##示例代码

```js
	var adsYoumi = api.require('adsYoumi');

	adsYoumi.init();
	adsYoumi.initWall();

	api.addEventListener({
		name : 'keyback'
	},function(){
		adsYoumi.release();
		api.closeWidget( { silent : true } );
	});
```

##补充说明

释放模块，请在应用退出的时候调用

##可用性

Android系统

可提供的1.0.0及更高版本


#**showWall**<div id="a3"></div>

显示积分墙

showWall({params}, callBack(ret, err))


##params

type：

- 类型：数字
- 描述：使用广告类型中的[积分墙类型常量](!Constant)设置即可，例如``adsYoumi.OfferWallDialog``

w：

- 类型：数字
- 描述：当类型为对话框积分墙的时候生效，为对话框积分墙的宽度

h：

- 类型：数字
- 默认值：无
- 描述：当类型为对话框积分墙的时候生效，为对话框积分墙的高度

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status:				//操作成功状态值				int  1 - 成功		0 - 失败
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
	code:				//错误编码						int
	msg:				//返回操作信息/错误信息 		string
}
```

##示例代码

```js
	var adsYoumi = api.require('adsYoumi');

	adsYoumi.init();
	adsYoumi.initWall();

	adsYoumi.showWall( { type : adsYoumi.OfferWallDialog , w : 300 , h : 600 } , function(ret,err){
		//成功返回
		if(ret.status==1){
			//
		}
		else{
			//输出错误信息
			api.alert({ msg : err.msg });
		}
	});
```

##可用性

Android系统

可提供的1.0.0及更高版本


#**queryPoints**<div id="a4"></div>

查询积分

queryPoints(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status:				//操作成功状态值				int  1 - 成功     0 - 失败
	points:				//返回查询的积分值				int
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
	code:				//错误编码						int
	msg:                //返回操作信息/错误信息			string
}
```

##示例代码
```js
	var adsYoumi = api.require('adsYoumi');
	adsYoumi.init();
	adsYoumi.initWall();
	adsYoumi.queryPoints(function(ret,err){
		//成功返回
		if(ret.status==1){
			//输出查询的积分值
			api.alert({ msg : ret.points });
		}
		else{
			//输出错误信息
			api.alert({ msg : err.msg });
		}
	});
```

##可用性

Android系统

可提供的1.0.0及更高版本

#**awardPoints**<div id="a5"></div>

获取积分

awardPoints({params}, callBack(ret, err))

##params
	
points：

- 类型：数字
- 描述：增加的积分值

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status:				//操作成功状态值				int 1 - 成功     0 - 失败
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
	code:				//错误编码						int
	msg:				//返回操作信息/错误信息 		string
}
```

##示例代码
```js
	var adsYoumi = api.require('adsYoumi');
	adsYoumi.init();
	adsYoumi.initWall();
	adsYoumi.awardPoints( { points : 10.5 } , function(ret,err){
		//成功返回
		if(ret.status==1){
			//
		}
		else{
			//输出错误信息
			api.alert({ msg : err.msg });
		}
	});
```

##可用性

Android系统

可提供的1.0.0及更高版本

#**spendPoints**<div id="a6"></div>

消费积分

spendPoints({params}, callBack(ret, err))

##params
	
points：

- 类型：数字
- 描述：消费的积分值

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status:				//操作成功状态值				int 1 - 成功     0 - 失败
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
	code:				//错误编码						int
	msg:                //返回操作信息/错误信息			string
}
```

##示例代码
```js
	var adsYoumi = api.require('adsYoumi');
	adsYoumi.init();
	adsYoumi.initWall();
	adsYoumi.spendPoints( { points : 10.5 } , function(ret,err){
		//成功返回
		if(ret.status==1){
			//
		}
		else{
			//输出错误信息
			api.alert({ msg : err.msg });
		}
	});
```

##可用性

Android系统

可提供的1.0.0及更高版本

#**setListener**<div id="a7"></div>

添加监听器

setListener({params}, callBack(ret, err))

##params
	
listenerId：

- 类型：字符串
- 描述：为监听器设置一个唯一的id作为识别标识

listenerType：

- 类型：数字
- 描述：监听器的类型，具体可以看文档中的[监听器类型常量](!Constant)

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

当监听器类型为全屏积分墙关闭监听器/对话框积分墙关闭监听器时：

```js
{
	status:				//操作成功状态值		   			int	1 - 成功     0 - 失败
	listenerId:			//监听器的唯一标识id		   		int
	listenerType:			//监听器的类型			   		int
	type:				//添加监听器/触发监听器 执行的回调 	int	0 - 添加监听器	1 - 触发监听器
}
```

当监听器为积分监听器时：

```js
{
	status:				//操作成功状态值						int	1 - 成功     0 - 失败
	listenerId:			//监听器的唯一标识id					int
	listenerType:			//监听器的类型						int
	type:				//添加监听器/触发监听器 执行的回调		int	0 - 添加监听器	1 - 触发监听器
	points:				//触发监听器返回时传回的，当前的积分值	int
}
```

当监听器为订单监听器时：

```js
{
	status:					//操作成功状态值								int	1 - 成功     0 - 失败
	listenerId:				//监听器的唯一标识id							int
	listenerType:			//监听器的类型									int
	type:					//添加监听器/触发监听器 执行的回调				int	0 - 添加监听器	1 - 触发监听器
	orderList:[				//触发监听器返回时传回的,获取的积分订单json数组	Array
		{
			orderId:		//积分订单唯一标识id							int
			appName:		//广告名字										string
			userId:			//用户id										int
			status:			//订单状态										int
							//1.表示开发者获得了收入并且用户获得了积分
							//2.表示没有获得收入但用户获得了积分
							//（未通过审核以及测试模式下结算无效等情况）
			msg:			//完成任务获取100积分							string
			points:			//本次赚取的积分								int
			settlingTime:	//订单结算时间戳								timestamp
		},
		……
	]
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
	code:					//错误编码						int
	msg:                	//返回操作信息/错误信息			string
}
```

##示例代码
```js
	var adsYoumi = api.require('adsYoumi');
	adsYoumi.init();
	adsYoumi.initWall();
	adsYoumi.removeListener( { listenerId : "4_1234" , listenerType : adsYoumi.PointsChangeListener }, function(ret, err) {
		//成功返回
		if(ret.status==1){
			//添加监听器成功
			if(ret.type==0){
				//
			}
			//触发监听器回调
			else if(ret.type==1){
				//
			}
		}
		else{
			//输出错误信息
			api.alert({ msg : err.msg });
		}
	});
```

##补充说明

每一次触发监听器都会执行回调中的函数

##可用性

Android系统

可提供的1.0.0及更高版本


#**removeListener**<div id="a8"></div>

移除监听器

removeListener({params}, callBack(ret, err))

##params
	
listenerId：

- 类型：字符串
- 描述：为监听器设置一个唯一的id作为识别标识

listenerType：

- 类型：数字
- 描述：监听器的类型，具体可以看文档中的[监听器类型常量](!Constant)

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status:				//操作成功状态值			int  1 - 成功     0 - 失败
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
	code:				//错误编码					int
	msg:                //返回操作信息/错误信息		string
}
```

##示例代码
```js
	var adsYoumi = api.require('adsYoumi');
	adsYoumi.init();
	adsYoumi.initWall();
	adsYoumi.removePointsChangeListener( { listenerId : "4_12345" , listenerType : adsYoumi.PointsEarnListener } , function( ret , err ){
		//成功返回
		if(ret.status==1){
			//
		}
		else{
			//输出错误信息
			api.alert({ msg : err.msg });
		}
	});
```

##可用性

Android系统

可提供的1.0.0及更高版本


#**setWallBrowserConfig**<div id="a9"></div>

设置积分墙的配置

setWallBrowserConfig({params}, callBack(ret, err))

##params

title：

- 类型：字符串
- 默认值：免费获取积分
- 描述：积分墙标题,非测试模式有效

bg：

- 类型：字符串
- 默认值：#FFBB34
- 描述：标题栏背景颜色，只支持六位数的颜色编码

isShowPointsBalance：

- 类型：bool
- 默认值：true
- 描述：是否显示标题栏右上角的积分余额

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status:				//操作成功状态值			int  1 - 成功     0 - 失败
}
```

err：

- 类型：JSON 对象
- 内部字段：
```js
{
	code:				//错误编码					int
	msg:				//返回操作信息/错误信息		string
}
```

##示例代码

```js
	var adsYoumi = api.require('adsYoumi');
	adsYoumi.init();
	adsYoumi.initWall();
	adsYoumi.setWallBrowserConfig({ title : '有米积分墙' , bg : '#000000' , isShowPointsBalance : true } ,function(ret,err){
		//成功返回
		if(ret.status==1){
			//
		}
		else{
			//输出错误信息
			api.alert({ msg : err.msg });
		}
	})
```

##可用性

Android系统

可提供的1.0.0及更高版本


#**setGlobalConfig**<div id="a10"></div>

有米广告全局设置

setGlobalConfig({params}, callBack(ret, err))

##params
	
enableDebugLog：

- 类型：布尔
- 默认值：true
- 描述：设置是否允许输出有米的debuglog

enableDownloadTips：

- 类型：布尔
- 默认值：true
- 描述：设置是否允许有米显示广告下载过程中的提示语

enableInstalledTips：

- 类型：布尔
- 默认值：true
- 描述：设置是否允许有米显示广告安装过程中的提示语

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status:             //操作成功状态				int 1 - 成功     0 - 失败
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
	code:               //错误编码					int
	msg:                //返回操作信息/错误信息		string
}
```

##示例代码

```js
	var adsYoumi = api.require('adsYoumi');
	adsYoumi.init();
	adsYoumi.initWall();
	adsYoumi.setGlobalConfig({ enableDebugLog : true , enableDownloadTips : true , enableInstalledTips : true } ,function(ret,err){
		//成功返回
		if(ret.status==1){
			//
		}
		else{
			//输出错误信息
			api.alert({ msg : err.msg });
		}
	})
```

##可用性

Android系统

可提供的1.0.0及更高版本
</div>

<div id="const-content">
<div class="outline">
	[积分墙类型](#a100)
	[监听器类型](#a101)
	[错误异常类型](#a102)
</div>

#**积分墙类型**<div id="a100"></div>

广告类型 - int

##取值范围：

常量 | 值 | 描述 | 类型
-----|--------|--------|--------|
 OfferWall | 1 | 全屏积分墙 | 积分墙类型 | 
 OfferWallDialog | 2 | 对话框积分墙 | 积分墙类型 | 

#**监听器类型**<div id="a101"></div>

监听器类型 - int

##取值范围：

常量 | 值 | 描述   
-----|--------|--------|
 PointsChangeListener | 1 | 积分监听器 |
 PointsEarnListener | 2 | 订单监听器 |
 FullScreenOfferWallCloseListener | 3 | 全屏积分墙关闭监听器 |
 DialogOfferWallCloseListener | 4 | 对话框积分墙关闭监听器 |
 
 
#**错误异常类型**<div id="a102"></div>

错误异常介绍 - int

##取值范围：

值 | 描述   
-----|--------|
-1 | 传入参数无效 |
-2 | 发生未知异常 |

</div>
