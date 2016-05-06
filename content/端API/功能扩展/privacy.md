/*
Title: privacy
Description: privacy
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：官方</p>

##基础类

<div class="outline">
[location](#a1)

[contacts](#a2)

[calendars](#a3)

[reminders](#a4)

[photos](#a5)

[bluetooth](#a6)

[microphone](#a7)

[camera](#a8)

</div>

#**概述**

privacy 模块封装了 IOS 平台上设备访问权限判断的接口，包括定位服务、通讯录、日历、提醒事项、照片、蓝牙共享、麦克风、相机、健康。由于 Android 平台上机制不同，所以本模块仅支持 IOS 平台。（Android 上是在应用打包时候注册某一项权限，用户安装时系统弹出提示，若用户同意则安装该 app，若不同意则取消安装。所以若应用被安装成功，则必定有 app 开发者注册给该应用的权限，应用内无需判断。）

<div id="a1"></div>

#**location**

判断是否有定位权限

location(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true	 //布尔型；是否有访问该功能权限；true（有权限）||false （无权限）
}
```

##示例代码

```js
var privacy = api.require('privacy');
privacy.location(function( ret, err ){		
	if( ret.status ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```

##可用性

IOS 系统

可提供的1.0.0及更高版本

<div id="a2"></div>

#**contacts**

判断是否有访问联系人权限

contacts(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true	 //布尔型；是否有访问该功能权限；true（有权限）||false （无权限）
}
```

##示例代码

```js
var privacy = api.require('privacy');
privacy.contacts(function( ret, err ){		
	if( ret.status ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```

##可用性

IOS 系统

可提供的1.0.0及更高版本

<div id="a3"></div>

#**calendars**

判断是否有访问日历权限

calendars(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true	 //布尔型；是否有访问该功能权限；true（有权限）||false （无权限）
}
```

##示例代码

```js
var privacy = api.require('privacy');
privacy.calendars(function( ret, err ){		
	if( ret.status ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```

##可用性

IOS 系统

可提供的1.0.0及更高版本

<div id="a4"></div>

#**reminders**

判断是否有访问提醒事项的权限

reminders(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true	 //布尔型；是否有访问该功能权限；true（有权限）||false （无权限）
}
```

##示例代码

```js
var privacy = api.require('privacy');
privacy.reminders(function( ret, err ){		
	if( ret.status ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```

##可用性

IOS 系统

可提供的1.0.0及更高版本

<div id="a5"></div>

#**photos**

判断是否有访问相册的权限

photos(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true	 //布尔型；是否有访问该功能权限；true（有权限）||false （无权限）
}
```

##示例代码

```js
var privacy = api.require('privacy');
privacy.photos(function( ret, err ){		
	if( ret.status ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```

##可用性

IOS 系统

可提供的1.0.0及更高版本

<div id="a6"></div>

#**bluetooth**

判断是否有访问蓝牙的权限

bluetooth(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true	 //布尔型；是否有访问该功能权限；true（有权限）||false （无权限）
}
```

##示例代码

```js
var privacy = api.require('privacy');
privacy.bluetooth(function( ret, err ){		
	if( ret.status ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```

##可用性

IOS 系统

可提供的1.0.0及更高版本

<div id="a7"></div>

#**microphone**

判断是否有访问录音器的权限

microphone(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true	 //布尔型；是否有访问该功能权限；true（有权限）||false （无权限）
}
```

##示例代码

```js
var privacy = api.require('privacy');
privacy.microphone(function( ret, err ){		
	if( ret.status ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```

##可用性

IOS 系统

可提供的1.0.0及更高版本

<div id="a8"></div>

#**camera**

判断是否有访问摄像头的权限

camera(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
    status: true	 //布尔型；是否有访问该功能权限；true（有权限）||false （无权限）
}
```

##示例代码

```js
var privacy = api.require('privacy');
privacy.camera(function( ret, err ){		
	if( ret.status ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```

##可用性

IOS 系统

可提供的1.0.0及更高版本
