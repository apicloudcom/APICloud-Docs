/*
Title: wallPaper
Description: wallPaper
*/

<p style="color: #ccc;margin-bottom: 30px;">来自于：开发者</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
</ul>
<div id="method-content">

<div class="outline">

[setWallPaper](#a1)

</div>

#**概述**

wallPaper封装了原生设置壁纸功能，使用此模块可设置指定图片为桌面背景，支持 http、widget 以及fs路径的图片。

注：此处指的 http 网络路径图片，应为图片的真实 URL，以文件名加文件后缀结尾，例如 http://images.99pet.com/InfoImages/wm600_450/1d770941f8d44c6e85ba4c0eb736ef69.jpg

#**setWallPaper**<div id="a1"></div>

设置指定图片为手机壁纸。

setWallPaper({params}, callback(ret, err))

##params

path:

- 类型：字符串
- 描述：图片路径，支持 http://、widget://、fs://路径的图片。

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	status:     //布尔类型；操作状态，true|false
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
	code：		//数字类型；状态码，取值范围如下：
	            //301：表示路径为空
				//302：表示图片路径有误，若为网络图片可能服务器超时
}
```

##示例代码

```js
var wallPaper = api.require('wallPaper');
wallPaper.setWallPaper({
	path: ''
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
