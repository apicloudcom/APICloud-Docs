/*
Title: wifiSSID
Description: wifiSSID
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">方法</a></li>
</ul>
<div id="method-content">

<div class="outline">

[getSsid](#getSsid)

</div>

#**概述**

wifiSSID封装了获取当前WIFI的SSID的接口，使用此模块可轻松获取当前连接的WIFI的名称

##getSsid
获取当前设备连接的WIFI的SSID

getSsid(callback(ret, err))<div id="getSsid"></div>

###callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	ssid:''      //SSID名称
}
```

err：

- 类型：JSON对象

内部字段：

```js
{
    msg:""    //错误描述
}
```

##示例代码

```js
		var wifissid = api.require('wifiSSID');
		wifissid.getSsid(null, function(ret, err) {
			if (ret.ssid) {
			   api.alert({
				msg : 'WIFI:' + ret.ssid
						});
				} else {
					api.alert({
						msg : err.msg
						});
					}
		});
```

##补充说明

无

##可用性

Android系统

可提供的1.0.1及更高版本