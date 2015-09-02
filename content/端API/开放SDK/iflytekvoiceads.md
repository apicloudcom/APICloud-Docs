/*
Title: iflytekvoiceads
Description: iflytekvoiceads
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">



**IFLYBannerAd类**
<div class="outline">
[createBannerAd](#1)

[setParameter](#2)

[loadAd](#3)

[showAd](#4)

[destroy](#5)
</div>

**IFLYInterstitialAd类**
<div class="outline">
[createInterstitialAd](#6)

[setParameter](#7)

[loadAd](#8)

[showAd](#9)
</div>

**IFLYFullScreenAd类**
<div class="outline">
[createFullScreenAd](#10)

[setParameter](#11)

[loadAd](#12)

[showAd](#13)
</div>

#**概述**

iflytekvoiceads模块封装了科大讯飞移动广告平台的sdk。开发者只需调用此模块即可实现在自己的应用中嵌入广告，可以获取相应的广告收入。**暂仅支持 Android 平台**

## IFLYBannerAd类 ##

#**createBannerAd**<div id="1"></div>

创建旗帜广告对象

createBannerAd(params,callback(ret, err))

##params
adid：

- 类型：字符串
- 描述：开发者在[广告平台](http://www.voiceads.cn)申请的广告位ID

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	key:success		//字符串类型；标识操作是否成功的状态值
}
```

##示例代码

	var uzBannerAd = null;
	apiready = function(){
		uzBannerAd = api.require('IFLYBannerAd');
	}
	//开发者务必要把这里的adid替换成自己申请的广告位号，否则将不会产生广告收益
	var param = {adid:"309A8A46D22633D6DA57E318EFBDF392"};
	uzBannerAd.createBannerAd(param, function(ret, err){
		if(ret.key=="error"){
	    	alert("广告初始化失败！");
		}
	});

##可用性

Android系统

可提供的1.0.0及更高版本

#**setParameter**<div id="2"></div>

设置广告对象的参数

setParameter(params,callback(ret, err))

##params

name：

- 类型：字符串
- 描述：所要设置的参数的名称

value：

- 类型：字符串
- 描述：所要设置的参数的值

##示例代码

	var uzBannerAd = null;
	apiready = function(){
		uzBannerAd = api.require('IFLYBannerAd');
	}
	//开发者在这里需要使用自己应用在讯飞开放平台获得的真实ID
	var param1 = {name:"appid",value:"544e2c99"};
	var param2 = {name:"debug_mode",value:"true"};
	var param3 = {name:"download_alert",value:"true"};
    uzBannerAd.setParameter(param1, function(ret, err){
    	if(ret.key=="error"){
    		alert("设置appid失败！");
    	}
    });
    uzBannerAd.setParameter(param2, function(ret, err){//成功时无回调
    	if(ret.key=="error"){
    		alert("设置debug_mode失败！");
    	}
    });
    uzBannerAd.setParameter(param3, function(ret, err){//成功时无回调
    	if(ret.key=="error"){
    		alert("设置download_alert失败！");
    	}
    });

##可用性

Android系统

可提供的1.0.0及更高版本


#**loadAd**<div id="3"></div>

加载旗帜广告

loadAd(params,callBack(ret,err))

##params

x：

- 类型：字符串
- 描述：旗帜广告将要显示的位置的X坐标

y：

- 类型：字符串
- 描述：旗帜广告将要显示的位置的Y坐标

w：

- 类型：字符串
- 描述：旗帜广告显示时的宽度

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    key:		     //字符串类型；广告控件在下载和显示过程中返回的状态值
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
    err:           //数字类型；错误码ErrorCode
}
```
##示例代码

	var uzBannerAd = null;
	apiready = function(){
    	uzBannerAd = api.require('IFLYBannerAd');
    }
    var receiveCallback = function(ret, err){
		if(ret.key=="onAdFailed"){
    		alert("广告加载失败！\n错误码："+err.err);//您也可以自定义onAdFailed的处理
    	}
    	else if(ret.key=="onAdReceive"){
    		//添加您自己对于获取广告成功的回调处理，一般包括展示广告（showAd）
    		uzBannerAd.showAd("",function(ret, err){//成功时无回调
    			if(ret.key=="error"){
    				alert("显示广告失败！");
    			}
    		});
    	}
    	else if(ret.key=="onAdClose"){
    		//添加您自己对于广告关闭操作的回调处理
    	}
    	else if(ret.key=="onAdClick"){
    		//添加您自己对于点击广告操作的回调处理
    	}
	}；
	uzBannerAd.loadAd(param4, receiveCallback);

##补充说明

加载旗帜广告，在这个函数中会绑定广告监听器，由监听器控制回调的调用

##可用性

Android系统

可提供的1.0.0及更高版本


#**showAd**<div id="4"></div>

显示加载好的广告

showAd(callBack(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    key:		   //字符串类型；标识广告显示是否成功的状态值
}
```

##示例代码

	见loadAd(params,callBack(ret,err))示例代码

##补充说明

广告加载完成后需要通过该函数的调用才能真正显示在屏幕上

##可用性

Android系统

可提供的1.0.0及更高版本

#**destroy**<div id="5"></div>

销毁广告

destroy()

##示例代码

	var uzBannerAd = null;
	apiready = function(){
    	uzBannerAd = api.require('IFLYBannerAd');
    }
    uzBannerAd.destroy();

##补充说明

讯飞移动广告平台禁止开发者用同一广告位号同时创建多个旗帜广告对象的作弊行为，云端一旦检测到这种行为可能会对开发者的广告收益产生不利影响。因此在开发者创建广告对象时，要保证之前创建的对象已经调用destroy方法进行了销毁。

##可用性

Android系统

可提供的1.0.0及更高版本

## IFLYInterstitialAd类 ##

#**createInterstitialAd**<div id="6"></div>

创建插屏广告对象

createInterstitialAd(params,callback(ret, err))

##params

adid：

- 类型：字符串
- 描述：开发者在[广告平台](http://www.voiceads.cn/)申请的广告位 ID

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	key:success		//字符串类型；标识操作是否成功的状态值
}
```

##示例代码

	var uzInterstitialAd = null;
	apiready = function(){
		uzInterstitialAd = api.require('IFLYInterstitialAd');
	}
	//开发时务必将此处的adid替换成开发者自己申请的广告位号，否则将不会产生广告收益
	var param = {adid:"15DE606C523B40C58C4BFFEDA966827D"};
	uzInterstitialAd.createInterstitialAd(param, function(ret, err){
		if(ret.key=="error"){
	    	alert("广告初始化失败！");
		}
	});

##可用性

Android系统

可提供的1.0.0及更高版本

#**setParameter**<div id="7"></div>

设置广告对象的参数

setParameter(params,callback(ret, err))

##params

name：

- 类型：字符串
- 描述：所要设置的参数的名称

value：

- 类型：字符串
- 描述：所要设置的参数的值

##示例代码

	var uzInterstitialAd = null;
	apiready = function(){
		uzInterstitialAd = api.require('IFLYInterstitialAd');
	}
	//开发者在这里需要使用自己应用在讯飞开放平台获得的真实ID
	var param1 = {name:"appid",value:"544e2c99"};
	var param2 = {name:"debug_mode",value:"true"};
	var param3 = {name:"download_alert",value:"true"};
	var param4 = {name:"back_key_enable",value:"false"};
    uzInterstitialAd.setParameter(param1, function(ret, err){
    	if(ret.key=="error"){
    		alert("设置appid失败！");
    	}
    });
    uzInterstitialAd.setParameter(param2, function(ret, err){
    	if(ret.key=="error"){
    		alert("设置debug_mode失败！");
    	}
    });
    uzInterstitialAd.setParameter(param3, function(ret, err){
    	if(ret.key=="error"){
    		alert("设置download_alert失败！");
    	}
    });
    uzInterstitialAd.setParameter(param4, function(ret, err){
        var json=JSON.stringify(ret); 
		var object=JSON.parse(json); 
    	if(object.key=="error"){
    		alert("设置back_key_enable失败！");
    	}
    });

##可用性

Android系统

可提供的1.0.0及更高版本

#**loadAd**<div id="8"></div>

加载插屏广告

loadAd(callBack(ret,err))

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    key:		   //字符串类型；广告控件在下载和显示过程中返回的状态值
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
    err:           //数字类型；错误码ErrorCode 
}
```
##示例代码

	var uzInterstitialAd = null;
	apiready = function(){
    	uzInterstitialAd = api.require('IFLYInterstitialAd');
    }
    var receiveCallback = function(ret, err){
		if(ret.key=="onAdFailed"){
    		alert("广告加载失败！\n错误码："+err.err);//您也可以自定义onAdFailed的处理
    	}
    	else if(ret.key=="onAdReceive"){
    		//添加您自己对于获取广告成功的回调处理，一般包括展示广告（showAd）
    		uzInterstitialAd.showAd("",function(ret, err){
    			if(ret.key=="error"){
    				alert("显示广告失败！");
    			}
    		});
    	}
    	else if(ret.key=="onAdClose"){
    		//添加您自己对于广告关闭操作的回调处理
    	}
    	else if(ret.key=="onAdClick"){
    		//添加您自己对于点击广告操作的回调处理
    	}
	}；
	uzInterstitialAd.loadAd("", receiveCallback);

##补充说明

加载插屏广告，在这个函数中会绑定广告监听器，由监听器控制回调的调用

##可用性

Android系统

可提供的1.0.0及更高版本

#**showAd**<div id="9"></div>

显示加载好的广告

showAd(callBack(ret,err))

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    key:		//字符串类型；标识广告显示是否成功的状态值
}
```

##示例代码

	见loadAd(params,callBack(ret,err))示例代码

##补充说明

广告加载完成后需要通过该函数的调用才能真正显示在屏幕上

##可用性

Android系统

可提供的1.0.0及更高版本

## IFLYFullScreenAd类 ##
#**createFullScreenAd**<div id="10"></div>

创建全屏广告对象

createFullScreenAd(params,callback(ret, err))

##params
adid：

- 类型：字符串
- 描述：开发者在[广告平台](http://www.voiceads.cn/)申请的广告位 ID

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	key:success		//字符串类型；标识操作是否成功的状态值
}
```

##示例代码

	var uzFullScreenAd = null;
	apiready = function(){
		uzFullScreenAd = api.require('IFLYFullScreenAd');
	}
	//开发时务必将此处的adid替换成开发者自己申请的广告位号，否则将不会产生广告收益
	var param = {adid:"13128689D99B9A479A86E1E91539FB73"};
	uzFullScreenAd.createFullScreenAd(param, function(ret, err){
		if(ret.key=="error"){
	    	alert("广告初始化失败！");
		}
	});

##可用性

Android系统

可提供的1.0.0及更高版本


#**setParameter**<div id="11"></div>

设置广告对象的参数

setParameter(params,callback(ret, err))

##params

name：

- 类型：字符串
- 描述：所要设置的参数的名称

value：

- 类型：字符串
- 描述：所要设置的参数的值

##示例代码

	var uzFullScreenAd = null;
	apiready = function(){
		uzFullScreenAd = api.require('IFLYFullScreenAd');
	}
	//开发者在这里需要使用自己应用在讯飞开放平台获得的真实ID
	var param1 = {name:"appid",value:"544e2c99"};//用于设置应用ID
	var param2 = {name:"debug_mode",value:"true"};//用于设置调试模式
	var param3 = {name:"download_alert",value:"true"};//用于设置是否在下载前弹出提示
	// 全屏广告展示时间，范围5000~10000，默认5000；如果设为-1，则使用叉号方式退出全屏广告
	var param4 = {name:"show_time_fullscreen",value:"-1"};//用户设置全屏广告的展示时间
    uzFullScreenAd.setParameter(param1, function(ret, err){
        var json=JSON.stringify(ret); 
		var object=JSON.parse(json); 
    	if(object.key=="error"){
    		alert("设置appid失败！");
    	}
    });
    uzFullScreenAd.setParameter(param2, function(ret, err){
        var json=JSON.stringify(ret); 
		var object=JSON.parse(json); 
    	if(object.key=="error"){
    		alert("设置debug_mode失败！");
    	}
    });
    uzFullScreenAd.setParameter(param3, function(ret, err){
        var json=JSON.stringify(ret); 
		var object=JSON.parse(json); 
    	if(object.key=="error"){
    		alert("设置download_alert失败！");
    	}
    });
    uzFullScreenAd.setParameter(param4, function(ret, err){
        var json=JSON.stringify(ret); 
		var object=JSON.parse(json); 
    	if(object.key=="error"){
    		alert("设置show_time_fullscreen失败！");
    	}
    });

##可用性

Android系统

可提供的1.0.0及更高版本

#**loadAd**<div id="12"></div>

加载插屏广告

loadAd(callBack(ret,err))

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    key:		    //字符串类型；广告控件在下载和显示过程中返回的状态值
}
```
err：

- 类型：JSON对象
- 内部字段：

```js
{
    err:           //数字类型；错误码ErrorCode
}
```
##示例代码

	var uzFullScreenAd = null;
	apiready = function(){
    	uzFullScreenAd = api.require('IFLYFullScreenAd');
    }
    var receiveCallback = function(ret, err){
		if(ret.key=="onAdFailed"){
    		alert("广告加载失败！\n错误码："+err.err);//您也可以自定义onAdFailed的处理
    	}
    	else if(ret.key=="onAdReceive"){
    		//添加您自己对于获取广告成功的回调处理，一般包括展示广告（showAd）
    		uzFullScreenAd.showAd("",function(ret, err){
    			if(ret.key=="error"){
    				alert("显示广告失败！");
    			}
    		});
    	}
    	else if(ret.key=="onAdClose"){
    		//添加您自己对于广告关闭操作的回调处理
    	}
    	else if(ret.key=="onAdClick"){
    		//添加您自己对于点击广告操作的回调处理
    	}
	}；
	uzFullScreenAd.loadAd("", receiveCallback);

##补充说明

加载全屏广告，在这个函数中会绑定广告监听器，由监听器控制回调的调用

##可用性

Android系统

可提供的1.0.0及更高版本

#**showAd**<div id="13"></div>

显示加载完成的广告

showAd(callBack(ret,err))

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
    key:		//字符串类型；标识广告显示是否成功的状态值
}
```

##示例代码

	见loadAd(params,callBack(ret,err))示例代码

##补充说明

广告加载完成后需要通过该函数的调用才能真正显示在屏幕上

##可用性

Android系统

可提供的1.0.0及更高版本