/*
Title: imageCrop
Description: imageCrop
*/

<p style="color: #ccc;margin-bottom: 30px;">来自于：开发者</p>

<ul id="tab" class="clearfix">
	<li class="active"><a href="#method-content">Method</a></li>
	<li><a href="#const-content">Constant</a></li>
</ul>
<div id="method-content">

<div class="outline">
[takePhoto](#a1)

[getPhoto](#a2)

[clipPhoto](#a3)

[deletePic](#a4)

</div>

#**概述**

imageCrop 模块封装了 Android 原生图片剪切的功能，通过拍照或者从相册选取图片之后，可以调用图片剪切方法。用户可以拖动、缩放、改变剪切框大小，也可以通过剪切框对图片进行缩放。在选取剪切位置和大小之后，可以选择确认或者取消。 **本模块暂仅支持安卓。**

#**takePhoto**<div id="a1"></div>

拍照获取图片路径

takePhoto(callback(ret, err))

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	imgPath: ''		//拍照获取的图片路径
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
	msg:    //错误描述
}
```

##示例代码

```js
var imageCrop = api.require('imageCrop');
imageCrop.takePhoto(function( ret, err ){		
    if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

Android 系统

可提供的1.0.0及更高版本

#**getPhoto**<div id="a2"></div>

通过相册获取图片路径

getPhoto(callback(ret, err))


##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	imgPath: ''			//相册获取的图片路径
}
```
err：

- 类型：JSON 对象
- 内部字段：

```js
{
	msg:       //错误描述
}
```

##示例代码

```js
var imageCrop = api.require('imageCrop');
imageCrop.getPhoto(function( ret, err ){		
    if( ret ){
        alert( JSON.stringify( ret ) );
    }else{
        alert( JSON.stringify( err ) );
    }
});
```

##可用性

Android 系统

可提供的1.0.0及更高版本

#**clipPhoto**<div id="a3"></div>

开始截图

clipPhoto({params}, callback(ret, err))

##params

imgPath：

- 类型：字符串
- 描述：要剪切图片的路径(1.1版本之后可以不传通过以上方法获取的图片路径)

height：

- 类型：数值类型
- 描述：（可选项）裁剪后的图片高度
- 默认值：150

width：

- 类型：数值类型
- 描述：（可选项）裁剪后的图片宽度
- 默认值：150

##callback(ret, err)

ret：

- 类型：JSON 对象
- 内部字段：

```js
{
	imgPath:       //裁剪后的图片路径，可以用于直接上传
}
```

err：

- 类型：JSON 对象
- 内部字段：

```js
{
	msg:       //错误描述
}
```

##示例代码

```js
var imageCrop = api.require('imageCrop');
imageCrop.clipPhoto({
    imgPath: 'widget://.png',
    height: 300,
    width: 300
}, function(ret, err){		
	if( ret ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```
##可用性

Android 系统

可提供的1.0.0及更高版本

#**deletePic**<div id="a4"></div>

图片上传后可以调用此方法删除剪裁后的图片

deletePic(callback(ret, err))

##示例代码

```js
var imageCrop = api.require('imageCrop');
imageCrop.deletePic(function( ret, err ){		
	if( ret ){
		alert( JSON.stringify( ret ) );
	}else{
		alert( JSON.stringify( err ) );
	}
});
```

##可用性

Android 系统

可提供的1.1.0及更高版本

</div>