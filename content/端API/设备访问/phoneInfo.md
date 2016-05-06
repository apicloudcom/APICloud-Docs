/*
Title: phoneInfo
Description: phoneInfo
*/

<p style="color: #ccc;margin-bottom: 30px;">来自于：开发者</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
  
</ul>
<div id="method-content">

<div class="outline">
[getBaseInfo](#a1)

[getCpuInfo](#a2)

[getMemoryInfo](#a3)

[getStorageInfo](#a4)

[getDisplayInfo](#a5)
</div>

#**概述**

phoneInfo 封装了获取手机基本信息、CPU 信息、内存信息、存储信息、显示信息等功能，使用 phoneInfo 模块基本上可以获取所有常用的手机设备信息。


#**getBaseInfo**<div id="a1"></div>

获取手机基本信息

getBaseInfo(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status:           			//操作成功状态值
	brand:			  			//品牌
	model:			  			//型号
	manufacturer:    			//制造商
	version:         			//系统版本
	sdkVersion:      			//系统SDK版本
	id:				 			//设备串号
	macAddress:      			//mac地址
	bootTime:         			//开机时间
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
    msg:""    			//错误描述
}
```

##示例代码

```js
var phoneInfo = api.require('phoneInfo');
phoneInfo.getBaseInfo(function(ret,err){
	if(ret.status){
		api.alert({msg:'品牌：'+ret.brand+'\r\n'+
		'型号：'+ret.model+'\r\n'+
		'制造商：'+ret.manufacturer+'\r\n'+
		'Android版本：'+ret.version+'\r\n'+
		'AndroidSDK版本：'+ret.sdkVersion+'\r\n'+
		'设备串号：'+ret.id+'\r\n'+
		'Mac地址：'+ret.macAddress+'\r\n'+
		'开机时间：'+ret.bootTime+'分钟'});
	}else{
		api.alert({msg:err.msg});
	}
});
```

##可用性

Android系统

可提供的1.0.0及更高版本

#<br/>
#**getCpuInfo**<div id="a2"></div>

获取CPU信息

getCpuInfo(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status:           			//操作成功状态值
	architecture:	  			//CPU架构
	coreNumber:		  			//CPU核心数
	minFrequency:     			//CPU最低频率
	maxFrequency:     			//CPU最高频率
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
    msg:""    //错误描述
}
```

##示例代码

```js
var phoneInfo = api.require('phoneInfo');
phoneInfo.getCpuInfo(function(ret,err){
	if(ret.status){
		api.alert({msg:'CPU架构：'+ret.architecture+'\r\n'+
		'CPU核心数：'+ret.coreNumber+'\r\n'+
		'CPU最高频率：'+ret.minFrequency+'\r\n'+
		'CPU最低频率：'+ret.maxFrequency});
	}else{
		api.alert({msg:err.msg});
	}
});
```

##可用性

Android系统

可提供的1.0.0及更高版本

#<br/>
#**getMemoryInfo**<div id="a3"></div>

获取内存信息

getMemoryInfo(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status:           			//操作成功状态值
	totalMemory:	  			//内存总大小
	availableMemory:  			//可用内存大小
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
    msg:""    //错误描述
}
```

##示例代码

```js
var phoneInfo = api.require('phoneInfo');
phoneInfo.getMemoryInfo(function(ret,err){
	if(ret.status){
		api.alert({msg:'内存大小：'+ret.totalMemory+'\r\n'+
		'可用内存大小：'+ret.availableMemory});
	}else{
		api.alert({msg:err.msg});
	}
});
```

##可用性

Android系统

可提供的1.0.0及更高版本

#<br/>
#**getStorageInfo**<div id="a4"></div>

获取手机存储信息

getStorageInfo(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status:           		//操作成功状态值
	sdCardStatus:	  		//SD卡的状态，返回如下值：
								//1001	未设置SD卡为御载，直接拔出SD卡后的状态
								//1002	手机正在检测SD卡过程中的状态
								//1003	SD卡正常使用的状态，并具有读写的权限
								//1004	SD卡正常使用的状态，但只有读的权限
								//1005	手动设置SD卡为御载之后，再拔出SD卡之后 的状态
								//1006	手机连接电脑，SD卡做为U盘使用之后的状态
								//1007	SD卡不可被安装
								//1008	手工设置SD卡为御载之后的状态
								//0	    没有获取到SD卡的状态
	sdCardPath:		  		//SD卡的路径
	sdCardTotalSize:  		//SD卡总大小
	sdCardAvailableSize:    //SD卡可用大小
	romTotalSize:       	//手机自身存储大小
	romAvailableSize:		//手机自身可用存储大小
	romPath:       			//手机自身存储路径
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
    msg:""    //错误描述
}
```

##示例代码

```js
var phoneInfo = api.require('phoneInfo');
phoneInfo.getStorageInfo(function(ret,err){
	if(ret.status){
		api.alert({msg:'SD卡状态：'+ret.sdCardStatus+'\r\n'+
		'SD卡路径：'+ret.sdCardPath+'\r\n'+
		'SD总容量：'+ret.sdCardTotalSize+'\r\n'+
		'SD可用容量：'+ret.sdCardAvailableSize+'\r\n'+
		'Rom路径：'+ret.romPath+'\r\n'+
		'Rom总容量：'+ret.romTotalSize+'\r\n'+
		'Rom可用容量：'+ret.romAvailableSize});
	}else{
		api.alert({msg:err.msg});
	}
});
```

##可用性

Android系统

可提供的1.0.0及更高版本


#<br/>
#**getDisplayInfo**<div id="a5"></div>

获取手机显示信息

getDisplayInfo(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status:           		//操作成功状态值
	width:		  			//屏幕宽度（单位为像素）
	height:  				//屏幕高度（单位为像素）
	densityDpi:    			//屏幕密度（单位为dpi）
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
    msg:""    //错误描述
}
```

##示例代码

```js
var phoneInfo = api.require('phoneInfo');
phoneInfo.getDisplayInfo(function(ret,err){
	if(ret.status){
		api.alert({msg:'分辨率：'+ret.width+'x'+ret.height+'\r\n'+
		'屏幕密度：'+ret.densityDpi+'dpi'});
	}else{
		api.alert({msg:err.msg});
	}
});
```

##可用性

Android系统

可提供的1.0.0及更高版本