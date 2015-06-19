/*
Title: wifi
Description: wifi
*/

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">
[currentWifi](#a1)

[getWifiState](#a2)

[scanWifiList](#a3)

[getConfiguredNetworks](#a4)

[openWifi](#a5)

[closeWifi](#a6)

[getWifiPassword](#a7)

[disconnect](#a8)

[disableNetwork](#a9)

[removeNetwork](#a10)

[manageWifiBySystem](#a11)

[connect](#a12)
</div>

#**概述**

wifi封装了获取当前设备当前连接的wifi的ssid接口，在android平台上（2015.4.24号版本开始）支持获取当前环境下的wifi列表，和连接到指定wifi。由于苹果安全机制，ios暂时不开放获取wifi列表和链接wifi的功能接口。本模块由第三方模块开发者提供，使用本模块需在线云编译安装包

#**currentWifi**<div id="a1"></div>

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

#**getWifiState**<div id="a2"></div>

获取当前wifi状态

getWifiState(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	 status:		    //操作成功状态值
    wifiState：      //wifi的状态 ，取值范围如下：
                      WIFI_STATE_ENABLED	已开启
                      WIFI_STATE_ENABLING	正在开启
                      WIFI_STATE_DISABLED	已关闭
                      WIFI_STATE_DISABLING	正在关闭
                      WIFI_STATE_UNKNOWN	未知状态
}
```

##示例代码

```js
var obj = api.require('wifi');
obj.getWifiState(function(ret,err){ 
	if(ret.status){
      api.alert({msg:ret.wifiState });
    }
});
```

##补充说明

此接口仅支持android平台

##可用性

Android系统

可提供的1.0.1及更高版本


#**scanWifiList**<div id="a3"></div>

扫描获取附近的wifi列表

scanWifiList(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	 status:		    //操作成功状态值
    scanWifiList：   //wifi列表 ，
         内部字段：[{
              frequency：      //
              level:          //
              bssid:          //
              capabilities:   //
              ssid:           //
          }]
}
```

##示例代码

```js
var obj = api.require('wifi');
obj.scanWifiList(function(ret,err){ 
   if(ret.status){
   api.alert({msg:ret.scanWifiList[0].ssid});
   }
});
```

##补充说明

此接口仅支持android平台

##可用性

Android系统

可提供的1.0.1及更高版本

#**getConfiguredNetworks**<div id="a4"></div>

获取已经配置过的wifi列表

getConfiguredNetworks(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	 status:		          //操作成功状态值
    configuredNetworks：   //数组类型 ，
         内部字段：[{
              hiddenSSID：     //
              networkId:      //
              priority:      //
              bssid:          //
              status:         //
              ssid:           //
          }]
}
```

##示例代码

```js
var obj = api.require('wifi');
obj.getConfiguredNetworks (function(ret,err){ 
    if(ret.status){
      api.alert({msg:ret.configuredNetworks[0].ssid});
    }
});

```

##补充说明

此接口仅支持android平台

##可用性

Android系统

可提供的1.0.1及更高版本

#**openWifi**<div id="a5"></div>

打开wifi

openWifi(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	 status:		       //操作成功状态值
    result：               //打开结果，取值范围如下：
	                       WIFI_STATE_ENABLED		已开启
		                   WIFI_STATE_ENABLING	    正在开启
                           WIFI_STATE_DISABLING	    正在关闭
                           WIFI_STATE_UNKNOWN		未知状态
                          OPEN_WIFI_SUCCESS		    打开wifi成功
                          OPEN_WIFI_FAIL			打开wifi失败
}
```

##示例代码

```js
var obj = api.require('wifi');
obj.openWifi(function(ret,err){ 
   if(ret.status){
      api.alert({msg:ret.result });
   }
});
```

##补充说明

此接口仅支持android平台

##可用性

Android系统

可提供的1.0.1及更高版本

#**closeWifi**<div id="a6"></div>

关闭wifi

closeWifi(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	 status:		       //操作成功状态值
    result：               //打开结果，取值范围如下：
	                       WIFI_STATE_ENABLED		已开启
		                   WIFI_STATE_ENABLING	    正在开启
                           WIFI_STATE_DISABLING	    正在关闭
                           WIFI_STATE_UNKNOWN		未知状态
                          OPEN_WIFI_SUCCESS		    打开wifi成功
                          OPEN_WIFI_FAIL			打开wifi失败
}
```

##示例代码

```js
var obj = api.require('wifi');
obj.closeWifi(function(ret,err){ 
   if(ret.status){
      api.alert({msg:ret.result });
   }
});
```

##补充说明

此接口仅支持android平台

##可用性

Android系统

可提供的1.0.1及更高版本


#**getWifiPassword**<div id="a7"></div>

获取指定wifi（已配置）密码

getWifiPassword({params},callback(ret, err))

##params

ssid:
- 类型：字符串
- 默认值：无
- 描述：要获取密码的wifi的名字，不可为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	 status:		         //操作成功状态值
    password：               //获取的密码，字符串类型
}
```

ret：

- 类型：JSON对象

内部字段：

```js
{
	 msg:		         //错误描述
}
```

##示例代码

```js
var obj = api.require('wifi');
obj.getWifiPassword({
   ssid:"abc",
},function(ret,err){ 
    if(ret.status){
       api.alert({msg:"连接成功"});
    }else{
       api.alert({msg:err.msg});
     }
});

```

##补充说明

此接口仅支持android平台

##可用性

Android系统

可提供的1.0.1及更高版本

#**disconnect**<div id="a8"></div>

断开当前wifi连接

disconnect(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	 status:		       //操作成功状态值
}
```

##示例代码

```js
var obj = api.require('wifi');
obj.disconnect (function(ret,err){ 
   if(ret.status){
      api.alert({msg:'断开连接成功'});
   }else{
     api.alert({msg:'断开连接失败'});
   }
});
```

##补充说明

此接口仅支持android平台

##可用性

Android系统

可提供的1.0.1及更高版本

#**disableNetwork**<div id="a9"></div>

禁用某网络

disableNetwork({params},callback(ret, err))

##params

ssid:

- 类型：字符串
- 默认值：无
- 描述：要禁用的wifi的名字，不可为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	 status:		         //操作成功状态值
}
```

ret：

- 类型：JSON对象

内部字段：

```js
{
	 msg:		         //错误描述
}
```

##示例代码

```js
var obj = api.require('wifi');
obj.disableNetwork({
   ssid:"abc",
},function(ret,err){ 
   if(ret.status){
         api.alert({msg:"禁用成功"});
    }else{
         api.alert({msg:err.msg});
    }
});
```

##补充说明

此接口仅支持android平台

##可用性

Android系统

可提供的1.0.1及更高版本

#**removeNetwork**<div id="a10"></div>

删除某网络

removeNetwork({params},callback(ret, err))

##params

ssid:

- 类型：字符串
- 默认值：无
- 描述：要删除的wifi的名字，不可为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	 status:		         //操作成功状态值
}
```

ret：

- 类型：JSON对象

内部字段：

```js
{
	 msg:		         //错误描述
}
```

##示例代码

```js
var obj = api.require('wifi');
obj.removeNetwork({
   ssid:"abc",
},function(ret,err){ 
   if(ret.status){
         api.alert({msg:"删除成功"});
    }else{
         api.alert({msg:err.msg});
    }
});
```

##补充说明

此接口仅支持android平台

##可用性

Android系统

可提供的1.0.1及更高版本

#**manageWifiBySystem**<div id="a11"></div>

跳转到系统设置界面

manageWifiBySystem(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	 status:		       //操作成功状态值
}
```

##示例代码

```js
var obj = api.require('wifi');
obj.manageWifiBySystem (function(ret,err){ 
   if(ret.status){
     api.alert({msg:'跳转成功'});
   }
});
```

##补充说明

此接口仅支持android平台

##可用性

Android系统

可提供的1.0.1及更高版本

#**connect**<div id="a12"></div>

链接某网络

connect({params},callback(ret, err))

##params

ssid:

- 类型：字符串
- 默认值：无
- 描述：要链接的wifi的名字，不可为空

password:

- 类型：字符串
- 默认值：无
- 描述：要连接的wifi的密码，需要与要连接的wifi密码一致，不可为空

type:

- 类型：字符串
- 默认值：无
- 描述：密码保护类型，需要与要连接的wifi保护类型一致，不可为空

##callback(ret, err)

ret：

- 类型：JSON对象

内部字段：

```js
{
	 status:		         //操作成功状态值
}
```

ret：

- 类型：JSON对象

内部字段：

```js
{
	 msg:		         //错误描述
}
```

##示例代码

```js
var obj = api.require('wifi');
obj.connect({
   	ssid:'abc',
	password:'12345678',
	type:'wpa'
},function(ret,err){ 
   if(ret.status){
      api.alert({msg:'连接成功'});
   }else{
     api.alert({msg:err.msg});
   }
});
```

##补充说明

此接口仅支持android平台

##可用性

Android系统

可提供的1.0.1及更高版本