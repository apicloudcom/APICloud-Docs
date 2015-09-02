/*
Title: simInfo
Description: simInfo
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	
</ul>
<div id="method-content">

<div class="outline">
[getPhoneNumber](#a1)

[getOperatorName](#a2)

[isNetworkRoaming](#a3)

</div>

#**概述**

simInfo封装了获取sim卡信息的方法，包括获取本机号码、运营商、sim卡序列号以及判断是否处于漫游状态。**暂仅支持 android 平台。**


#**getPhoneNumber**<div id="a1"></div>

获取本机号码

getPhoneNumber(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	status:                //布尔类型；操作成功状态值，true/false
	phoneNumber:           //数字类型；获取的本机号码
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
    msg:""    //字符串类型；错误描述信息
}
```

##示例代码

```js
var simInfo = api.require('simInfo');
simInfo.getPhoneNumber(function(ret, err){
	if(ret.status){
		api.alert({msg:ret.phoneNumber});
	}else{
		api.alert({msg:err.msg});
	}
});
```

##可用性

Android系统

可提供的1.0.0及更高版本

#**getOperatorName**<div id="a1"></div>

获取网络运营商

getOperatorName(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	status:                //布尔类型；操作成功状态值
	networtOperator:       //字符串类型；网络运营商
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
    msg:""                //字符串类型；错误描述信息
}
```

##示例代码

```js
var simInfo = api.require('simInfo');
simInfo.getOperatorName(function(ret, err){
	if(ret.status){
		api.alert({msg:ret.networtOperator});
	}else{
		api.alert({msg:err.msg});
	}
});
```

##可用性

Android系统

可提供的1.0.0及更高版本

#**getSimSerialNumber**<div id="a2"></div>

获取sim卡序列号

getSimSerialNumber(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	status:                //布尔类型；操作成功状态值
	serialNumber:          //数字类型；sim卡序列号
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
    msg:""                //字符串类型；错误描述信息
}
```

##示例代码

```js
var simInfo = api.require('simInfo');
simInfo.getSimSerialNumber(function(ret, err){
	if(ret.status){
		api.alert({msg:ret.serialNumber});
	}else{
		api.alert({msg:err.msg});
	}
});
```

##可用性

Android系统

可提供的1.0.0及更高版本


#**isNetworkRoaming**<div id="a3"></div>

判断当前网络是否漫游

isNetworkRoaming(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象
- 内部字段：

```js
{
	isRoaming:          //布尔类型；当前网络是否漫游 true/false
}
```

err：

- 类型：JSON对象
- 内部字段：

```js
{
    msg:""             //字符串类型；错误描述信息
}
```

##示例代码

```js
var simInfo = api.require('simInfo');
simInfo.isNetworkRoaming(function(ret, err){
	api.alert({msg:ret.isRoaming});
});
```

##可用性

Android系统

可提供的1.0.0及更高版本