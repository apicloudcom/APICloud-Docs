/*
Title: appManage
Description: appManage
*/

<p style="color: #ccc; margin-bottom: 30px;">来自于：开发者</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>

<div id="method-content">

<div class="outline">
[isInstalled](#a1)

[isSystemApp](#a2)

[install](#a3)

[uninstall](#a4)

</div>


#**概述**

appManage 封装了在 android 系统上安装、卸载 Apk，判断指定应用是否为系统应用、是否安装的功能。


#**isInstalled**<div id="a1"></div>

判断指定应用是否安装

isInstalled({params}, callback(ret, err))

##params

pkgName:
- 类型：字符串
- 描述 : 要查看的应用的包名

```js
{
    pkgName：'com.apicloud.freeman.xxx'
}
```

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status:           //布尔类型：操作成功状态值
    value:            //布尔类型：是否安装，`true` 已安装，`false` 未安装
}
```

##示例代码

```js
var appManage = api.require('appManage');
appManage.isInstalled({
    pkgName: 'com.wan.xdemo'
}, function(ret, err){		
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

Android 系统

可提供的1.0.0及更高版本


#**isSystemApp**<div id="a2"></div>

判断指定应用是否为系统应用

isSystemApp({params}, callback)

##params

pkgName:
- 类型：字符串
- 描述: 要查看的应用的包名

```js
{
	'pkgName': 'com.apicloud.freeman.xxx'
}
```

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status:		//布尔类型: 操作成功状态值
	value:      //布尔类型: 是否为系统应用, `true` 系统应用, `false` 非系统应用（第三方应用）
```


##示例代码

```js
var appManage = api.require('appManage');
appManage.isSystemApp({
    pkgName: 'com.wan.xdemo'
},function( ret, err){		
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

Android 系统

可提供的1.0.0及更高版本

#**install**<div id="a3"></div>

安装存储在指定 sdcard 目录下的 apk 文件

install({params}, callback(ret, err))

##params

filePath:
- 类型：字符串
- 描述 : apk 文件所在的 sdcard 目录，需要指定完整的文件目录名称


```js
{
	'filePath'：'sdcard/folderX/appX.apk'
}
```

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status:		//布尔类型：操作成功状态值
	code:       //数字类型：错误码, `-1` 要安装的文件不存在
}
```

##示例代码

```js
var appManage = api.require('appManage');
appManage.install({
    filePath: 'sdcard/folderX/appX.apk'
},function( ret, err){		
    if( ret.status ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});	
```

##补充说明

仅支持安装 sdcard 目录下的 apk 文件，默认需要安装的 apk 文件下载存储到 sdcard 的指定目录中

##可用性

Android 系统

可提供的1.0.0及更高版本

#**uninstall**<div id="a4"></div>

根据包名卸载指定应用

uninstall({params})

##params

pkgName:
- 类型：字符串
- 描述：要卸载的应用的包名


```js
{
	'pkgName': 'com.apicloud.freeman.xxx'
}
```

##示例代码

```js
var appManage = api.require('appManage');
appManage.uninstsall({
    pkgName: 'com.wan.xdemo'
});
```

##可用性

Android系统

可提供的1.0.0及更高版本