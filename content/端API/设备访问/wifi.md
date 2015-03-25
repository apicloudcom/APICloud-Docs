/*
Title: wifi
Description: wifi
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

#**概述**

wifi封装了获取当前设备连接wifi的ssid的接口

#**currentWifi**

获取设备当前连接的wifi

currentWifi(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	status:		//操作成功状态值
	bssid：		//无线ap的mac地址
	ssid:       //无线ap名称
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
	msg:””		//错误描述
}
```

##示例代码

```js
var obj = api.require('wifi');
obj.currentWifi(function(ret,err){
	if(ret.status){
		api.alert({msg:ret.ssid+"*"+ret.bssid});
	}else{
		api.alert({msg:ret.msg});
	}
});
```

##补充说明

无

##可用性

iOS系统，Android系统

可提供的1.0.0及更高版本
